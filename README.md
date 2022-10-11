# pihole 🥧

Custom pihole configuration for my homelab

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
