---
title: GitHub Actions
date: 2023-01-02 18:25:00 +0000
categories: [Note to self, GitHub]
tags: [GitHub, GitHub actions]     # TAG names should always be lowercase
---

# Scheduling an R script with GitHub Actions

I am working on a project where I want to run a script every week. Using GitHub actions we can have this job to be scheduled to run remotely.

In order to set up a GitHub action you need to create an Action which is a `.yaml` file.

[Documents](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#example-requiring-successful-dependent-jobs) how you can make sure a job is completed before another job is run.
