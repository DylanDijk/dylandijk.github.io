---
layout: post
title: Linux Binaries
date: 2024-04-24 09:33 +0000
---

Add bash script to `usr/bin` folder then run `chmod +x your_binary`, and add `export PATH=$PATH:~/usr/bin` to bottom of `.bashrc` file.



Below I give my Linux binaries


# CTVsuggestTrain_train_model.sh 
```bash
#!/bin/bash

cd /home/zl22291@bristol.ac.uk/Documents/Projects/CTVsuggestTrain/


# Ask the user for confirmation
read -p "Do you want to pull changes from remote repository before running CTVsuggestTrain::Train_model() (y/n): " choice

# Check the user's response
if [ "$choice" == "y" ]; then
  # Fetch the latest changes from the remote repository
  git pull
  echo "Pull completed."
elif [ "$choice" == "n" ]; then
  echo "Pull  skipped."
else
  echo "Invalid choice. Please enter 'y' for yes or 'n' for no."
fi

Rscript bash_r_scripts/train_model.r
```

# remotebp.sh
```bash
#!/bin/bash

# URL to open
url="https://uobnet2.bristol.ac.uk"

# Open the URL using the default application
xdg-open "$url"

# wait 15 seconds
sleep 15

# connect to blue pebble
ssh bp
```


# runjob_bp.sh
```bash
#!/bin/bash

echo "If remote, make sure vpn is already set up with: remotebp"

# ask for script name
read -p "Enter script name: " scriptname 

# Define the project directory in the work space
work_dir="/user/work/zl22291/simulations"

# Define the project directory in the home space
home_dir="/user/home/zl22291/simulations"

echo "By defualt this binary will store this job in the simulations folder in the home and work directories on the cluster. If you want to change this, the binary will need to be edited, in particular the work_dir and home_dir variables."


# ask for project name and job name
read -p "Enter project name: " projname

echo "Recommended to have job name same as script name"
read -p "Enter job name: " jobname

# setting destination path variable
destination_work_path="${work_dir}/${projname}/${jobname}"
destination_home_path="${home_dir}/${projname}/${jobname}"

# asking for slurm job arguments
read -p "Enter amount of memory: " sl_mem
read -p "Enter amount of time: "  sl_time
read -p "Enter number of cores: " sl_cores

# send script to work folder
echo "sending script to cluster"
scp "$scriptname" "zl22291@bp1-login.acrc.bris.ac.uk:$destination_work_path"

ssh bp "cd $destination_home_path && cat > job_script.slurm << EOF
#!/bin/bash
#SBATCH --account=MATH021322
#SBATCH --mem=$sl_mem
#SBATCH --time=$sl_time
#SBATCH --cpus-per-task=$sl_cores

# Change into working directory
cd \"$destination_work_path\"

# Loading R 4.0.1
# module load lang/r/4.0.1

# Now loading r/4.3.0-gcc as sparsevar package was not working on 4.0.1 module
module load lang/r/4.3.0-gcc

echo \"Running R script\"
Rscript \"$scriptname\"

mail -s \"Job on Blue Pebble is Completed\" zl22291@bristol.ac.uk <<< \"Completed\"
EOF

sbatch job_script.slurm
sleep 5
sacct"

# getting output back to local machine
# scp zl22291@bp1-login.acrc.bris.ac.uk:$destination_work_path:$destination_work_path/
```

# get_files_bp.sh
```bash
#!/bin/bash

# Ask the user for the object names, project name, and job name
read -p "Enter the object names (separated by spaces): " objects
read -p "Enter the project name: " project
read -p "Enter the job name: " job

# Split the object names into an array
IFS=" " read -a object_array <<< "$objects"

# Loop through each object name and transfer the files to the current directory
for object in "${object_array[@]}"; do
    source_path="zl22291@bp1-login.acrc.bris.ac.uk:/user/work/zl22291/simulations/$project/$job/$object"
    
    # Use scp to transfer the files to the current directory
    scp "$source_path" .
    
    # Check the exit status of scp and display a message
    if [ $? -eq 0 ]; then
        echo "Successfully transferred $object to the current directory"
    else
        echo "Failed to transfer $object to the current directory"
    fi
done
```
