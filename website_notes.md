# Notes for building website

I am writing important parts of the workflow of the website building process.  

Main things:
- I am using [`rbenv`](https://github.com/rbenv/rbenv#seamlessly-manage-your-apps-ruby-environment-with-rbenv) as a Ruby version manager. It allows you to choose virtual environments that use a specific Ruby version.
  - I have used the [Basic git checkout method to install `rbenv`](https://github.com/rbenv/rbenv#basic-git-checkout)
  - `.rbenv` directory exists in my home directory
  - There is then further [documentaion](https://github.com/rbenv/rbenv#installing-ruby-versions) on installing Ruby and Ruby gems.
    - Main thing is to set the Ruby version you want for your project and then install the gems. [commands](https://github.com/rbenv/rbenv#command-reference) provided show how to view/set a Ruby version locally or globally.


- To build locally run in terminal: ` bundle exec jekyll s`

***

## Changes to webpage setup

Edit the _config.yml file to update links, images and text such as name.
Can add description under name by editing the `tagline:` line.

### Changing main image
Select path of image in the line:  
`# the avatar on sidebar, support local or CORS resources`  
in the `_config.yml` file.

***

## Generating favicons
Follow [Tutorial](https://chirpy.cotes.page/posts/customize-the-favicon/). The favicons are stored in the path `assets/img/favicons`.

***

## Adding posts

To add a post that comes up on the home page 
