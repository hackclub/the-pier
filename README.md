![](https://github.com/thecodingmachine/workadventure/workflows/Continuous%20Integration/badge.svg) [![Discord](https://img.shields.io/discord/821338762134290432?label=Discord)](https://discord.gg/G6Xh9ZM9aR) ![Awesome](https://awesome.re/badge.svg)

![WorkAdventure office image](README-MAP.png)

Live demo [here](https://play.staging.workadventu.re/@/tcm/workadventure/wa-village).

# WorkAdventure (THE PIER / HACKCLUB EDITION)


We plan to make our fork of WorkAdventure an awesome hangout & work space for Hack Clubbers

This will be used for one of the next Big HQ Projects™!

In WorkAdventure you can move around your office and talk to your colleagues (using a video-chat system, triggered when you approach someone).


## Community resources

1. Want to build your own map, check out our **[map building documentation](https://docs.workadventu.re/map-building/)**
2. Check out resources developed by the WorkAdventure community at **[awesome-workadventure](https://github.com/workadventure/awesome-workadventure)**

## Setting up a production environment

We support 2 ways to set up a production environment:

- using Docker Compose
- or using a Helm chart for Kubernetes

Please check the [Setting up a production environment](docs/others/self-hosting/install.md) guide for more information.

## Setting up a development environment on GitHub Codespaces

First, create a Codespace on this repository. Click the green Code button, select Codespaces, and press "Create codespace on master". That's it! A dev environment will be set up for you automatically.

For reference, this is the command used to run everything in Codespaces.

```bash
docker compose -f docker-compose-base.yaml -f docker-compose-codespaces.yaml up --force-recreate
```

## Setting up a development environment locally

> [!NOTE]
> These installation instructions are for local development only. They will not work on
> remote servers as local environments do not have HTTPS certificates.

Install Docker and clone this repository.

> [!WARNING]
> If you are using Windows, make sure the End-Of-Line character is not modified by the cloning process by setting
> the `core.autocrlf` setting to false: `git config --global core.autocrlf false`

Run:

```bash
cp .env.template .env
docker compose -f docker-compose-base.yaml -f docker-compose-dev.yaml up --force-recreate
```

The environment will start.

You should now be able to browse to http://play.workadventure.localhost/ and see the application.
You can view the Traefik dashboard at http://traefik.workadventure.localhost

Note: on some OSes, you will need to add this line to your `/etc/hosts` file:

**/etc/hosts**
```
127.0.0.1 oidc.workadventure.localhost redis.workadventure.localhost play.workadventure.localhost traefik.workadventure.localhost matrix.workadventure.localhost extra.workadventure.localhost icon.workadventure.localhost map-storage.workadventure.localhost uploader.workadventure.localhost maps.workadventure.localhost api.workadventure.localhost front.workadventure.localhost
```

You can also start WorkAdventure + a test OpenID connect server using:

```console
$ docker-compose -f docker-compose.yaml -f docker-compose-oidc.yaml up
```

(Test user is "User1" and his password is "pwd")

This is potentially a pathway to implement Sign in with Slack


### Troubleshooting

See our [troubleshooting guide](docs/others/troubleshooting.md). 
