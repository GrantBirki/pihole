# pihole 🥧

[![release](https://github.com/GrantBirki/pihole/actions/workflows/release.yml/badge.svg)](https://github.com/GrantBirki/pihole/actions/workflows/release.yml)

Custom pihole configuration for my homelab

## About 💡

This repository contains my custom pihole configuration to deploy a Docker container to a raspberry pi to block ads.

It works by using the official pihole Docker image and utilizing the [github/branch-deploy](https://github.com/github/branch-deploy) + [runway](https://github.com/runwaylab/runway) to facilitate deployments.

## Usage 💻

Run the following command (`script/deploy`) to start the Docker Compose stack:

```console
$ script/deploy
[#] Killing old docker processes
docker-compose down -v -t 1
[#] Building docker container
docker-compose up --build -d
Creating network "pihole_default" with the default driver
Creating pihole ... done
[#] Container is now running!
```

## Configuration ⚙️

All configration takes place in the [`docker-compose.yml`](docker-compose.yml) file in the root of this repository.

For additional options, see the official documentation [here](https://github.com/pi-hole/docker-pi-hole)

## Deployment 🚀

> Note: These are mostly docs for myself. If you want to adapt this code, edit the `Makefile` and `docker-compose.yml` files and any script in the `script/` directory to ensure that they work for your environment. There are a few places where I hardcode my repo name (this one) and also my home network address so you will need to change those

To deploy this stack onto a raspberry pi you will need to do the following:

1. Clone this repo onto your raspberry pi
2. Run `script/bootstrap` and follow the prompts
3. Run `script/deploy` to start the stack

The `script/bootstrap` script will do the following for you automatically:

1. Check to ensure all dependencies are installed
2. Generate a random password for the pihole admin panel and store it in the `WEBPASSWORD_FILE.txt` file in the root of this repo
