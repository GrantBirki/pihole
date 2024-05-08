# pihole 🥧

[![deploy](https://github.com/GrantBirki/pihole/actions/workflows/deploy.yml/badge.svg)](https://github.com/GrantBirki/pihole/actions/workflows/deploy.yml)

Custom pihole configuration for my homelab

## About 💡

This repository contains my custom pihole configuration to deploy a Docker container to a raspberry pi to block ads.

It works by using the official pihole Docker image and utilizing the [github/branch-deploy](https://github.com/github/branch-deploy) + [runway](https://github.com/runwaylab/runway) to facilitate deployments.

## Setup 💻

Clone this repo and run `script/bootstrap` for first time setup. Then, run `script/deploy` to start the stack.

Beyond the initial setup, all deployments are facilitated by my personal `runway` controller. This is a simple CLI tool that I use to deploy my homelab services through branch deployments in GitHub Actions.

## Configuration ⚙️

All configration takes place in the [`docker-compose.yml`](docker-compose.yml) file in the root of this repository.

For additional options, see the official documentation [here](https://github.com/pi-hole/docker-pi-hole)

## Deployment 🚀

It is preferred to deploy this stack through pull requests following the branch deploy patterns.

However, you can also just yeet commits directly to `main` which will start an `in_progress` deployment. My `runway` service will detect deployments from PR branches, or `main` and complete the deployment process.
