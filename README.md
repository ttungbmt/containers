# The LaraGIS Containers Library

Popular applications, provided by [LaraGIS](https://laragis.vn), containerized and ready to launch.

## Get an image

The recommended way to get any of the LaraGIS Images is to pull the prebuilt image from the [Docker Hub Registry](https://hub.docker.com/r/laragis/).

```console
docker pull laragis/APP
```

To use a specific version, you can pull a versioned tag.

```console
docker pull laragis/APP:[TAG]
```

If you wish, you can also build the image yourself by cloning the repository, changing to the directory containing the Dockerfile, and executing the `docker build` command.

```console
git clone https://github.com/laragis/containers.git
cd laragis/APP/VERSION/OPERATING-SYSTEM
docker build -t laragis/APP .
```

> [!TIP]
> Remember to replace the `APP`, `VERSION`, and `OPERATING-SYSTEM` placeholders in the example command above with the correct values.

## Run the application using Docker Compose

The main folder of each application contains a functional `docker-compose.yml` file. Run the application using it as shown below:

```console
curl -sSL https://raw.githubusercontent.com/laragis/containers/main/laragis/APP/docker-compose.yml > docker-compose.yml
docker-compose up -d
```

> [!TIP]
> Remember to replace the `APP` placeholder in the example command above with the correct value.

## Vulnerability scan in LaraGIS container images

As part of the release process, the LaraGIS container images are analyzed for vulnerabilities. At this moment, we are using two different tools:

- [Trivy](https://github.com/aquasecurity/trivy)
- [Grype](https://github.com/anchore/grype)

This scanning process is triggered via a GH action for every PR affecting the source code of the containers, regardless of its nature or origin.
