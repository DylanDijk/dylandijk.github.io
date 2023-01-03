---
title: Scheduling an R Script - GitHub Actions
date: 2023-01-02 18:25:00 +0000
categories: [Note to self, GitHub]
tags: [GitHub, GitHub actions]     # TAG names should always be lowercase
---

**Main references**:
  - I have used the links provided by [this blog post](https://blog--simonpcouch.netlify.app/blog/r-github-actions-commit/) by Simon Couch
  - Used workflow templates from the [rlib/actions repo](https://github.com/r-lib/actions)

# Scheduling an R script with GitHub Actions

I am working on a project where I want to run a script every week. Using GitHub actions we can have this job to be scheduled to run remotely.

In order to set up a GitHub action you need to create an Action which is a `.yaml` file.

The `.yaml` file I used is given below:

```yaml
on:
  schedule:
    - cron: "40 8 * * TUE"

name: schedule-train-model

jobs:
  ctvsuggesttrain-train-model:
    runs-on: ubuntu-latest
    env:
      GITHUB_PAT: ${{ secrets.GITHUB_TOKEN }}
    steps:
      - name: Checkout repo
        uses: actions/checkout@v3

      - uses: r-lib/actions/setup-r@v2

      - uses: r-lib/actions/setup-r-dependencies@v2

      - name: Run Train_model
        run: CTVsuggestTrain::Train_model(save_output = TRUE, save_path = "OUTPUT/")
        shell: Rscript {0}

      - name: Commit and Push model output
        run: |
          git config --local user.email "actions@github.com"
          git config --local user.name "GitHub Actions"
          git add --all
          git commit -am "add data"
          git push
```

The first part:


```yaml
on:
  schedule:
    - cron: "40 8 * * TUE"
```    


Tells GitHub actions to run this every Tuesday at 8:40, this [website](https://crontab.guru/#40_8_*_*_TUE) converts a schedule time into `cron schedule expressions`.

For the rest of the `.yaml` file I made use of the templates provided by the [rlib/actions repo](https://github.com/r-lib/actions). The rlib/actions repository stores actions that make it easy to setup an R environment for GitHub actions.

For example:

```yaml
- uses: r-lib/actions/setup-r-dependencies@v2
```

Installs all of the dependencies listed in the `DESCRIPTION` file of your repository. I noticed that this part of the job took a substantial amount of time in my case (15 minutes), but the `setup-r-dependencies` action has a `cache` input that is `true` by default which caches packages across runs.

For documentation on setting up workflows with GitHub actions view:
[About Workflows Section](https://docs.github.com/en/actions/using-workflows/about-workflows).
