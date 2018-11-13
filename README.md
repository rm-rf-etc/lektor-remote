## Quickstart

If you have docker installed, you don't need anything else (not even Lektor).
```
docker-compose up
```


## Status

This is a work in progress. Currently it's been tested only as far as running on localhost with docker-compose.

In `lektor-project/` you'll see the output from running `lektor quickstart`. At the prompt for blog models I said no. Simply overwrite the content of `lektor-project/` with your project files.

Ultimately, the goal is to have all manifests necessary to deploy Lektor to a remote server, and login via
some auth process, such as basic auth.


### Helpful commands

In case you're not that familiar with docker, here's some commands to help you out.

To see output path:
```
docker run -it --mount type=bind,source=$(pwd)/lektor-project,target=/opt/lektor softinstigate/lektor project-info --output-path
```

To get an interactive bash session:
```
docker run -it --mount type=bind,source=$(pwd)/lektor-project,target=/opt/lektor --entrypoint bash softinstigate/lektor
```

And if the container is already running:
```
docker container ls
docker exec -it <container id> bash
```

Note, docker-compose is a different animal. And so too is `docker swarm`. If you're confused, you should be.


### Docker hub images

I see two images available on docker hub...
* [softinstigate/lektor](https://hub.docker.com/r/softinstigate/lektor/)
* [mfellner/lektor](https://hub.docker.com/r/mfellner/lektor/)

Both can work but the lektor root is different, so update your volume path if you change the image.


### What's next

* Add manifest to run s3cmd for S3 deployments ([see docs](https://www.getlektor.com/docs/deployment/)).
* Need to recommend an approach to separate project files from Lektor container
* Add traefik and basic auth
* Probably other things that will come up once I try deploying to a docker swarm...
