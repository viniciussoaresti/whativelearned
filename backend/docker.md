# Docker

"Docker is a software platform that allows you to build, test, and deploy applications quickly. Docker packages software into standardized units called containers that have everything the software needs to run including libraries, system tools, code, and runtime. Using Docker, you can quickly deploy and scale applications into any environment and know your code will run", [AWS](https://aws.amazon.com/docker/).

# Contents:
- [Docker](#docker)
- [Contents:](#contents)
- [Useful CLI commands:](#useful-cli-commands)
  - [Building and starting docker image:](#building-and-starting-docker-image)
  - [Observing container logs:](#observing-container-logs)
  - [Refreshing container:](#refreshing-container)
  - [For running commands inside the container:](#for-running-commands-inside-the-container)
  - [Rebuilding and starting docker image:](#rebuilding-and-starting-docker-image)

# Useful CLI commands:

## Building and starting docker image:

`docker compose -f "docker-compose.yml" up -d --build`

## Observing container logs:

`docker logs --follow <Container ID>`

## Refreshing container:

`docker restart <Container ID>`

## For running commands inside the container:

`docker exec -it <Container ID> bash`

## Rebuilding and starting docker image:

`docker compose -f "docker-compose.yml" down`
`docker builder prune --all`
`docker compose -f "docker-compose.yml" up -d --build`