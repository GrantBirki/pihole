# pihole 🥧

Custom pihole configuration for my homelab

## About 💡

This repository contains my custom pihole configuration to deploy a Docker container to a raspberry pi to block ads.

It works by using the official pihole Docker image and running a cronjob to look for new tags published to this repo. This way, I can maintain my infrastructure through the GitHub flow!

## Usage 💻

Run the following command (`make run`) to start the Docker Compose stack:

```console
$ make run
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
3. Run `make run` to start the stack

The `script/bootstrap` script will do the following for you automatically:

1. Check to ensure all dependencies are installed
2. Generate a random password for the pihole admin panel and store it in the `WEBPASSWORD_FILE.txt` file in the root of this repo
3. Setup a cronjob that will automatically look for new release tags from the source repo and update the stack if a new release is found

## Release 🏷️

Deployed pihole's from this repository have cronjobs configured that look for new tags (not releases but **tags**) and automatically update their code when these tags are published.

Here is how you can publish a new tag + release for consumption by the deployed pihole's:

```console
$ script/release
... follow the prompts!
```

After executing this command, a new release tag will be published and GitHub Actions will automatically publish a new release with the same tag name
