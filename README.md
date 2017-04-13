# Founaint JS Yeoman Generator Docker Image

Docker images for running [Yeoman Foundain Generator](http://fountainjs.io/). Based on Waldek Mastykarz (SPFX Docker Image)

[![Docker Pulls](https://img.shields.io/docker/pulls/rgarita/fountainjs.svg)](https://hub.docker.com/r/rgarita/fountainjs/)
[![Docker Stars](https://img.shields.io/docker/stars/rgarita/fountainjs.svg)](https://hub.docker.com/r/rgarita/fountainjs/)

## Usage

- in **Docker Settings > Shared Drives** verify that the drive where you create your projects is shared
- in the HOSTS file on your host add:
```
127.0.0.1    fountain
```
- Create a folder for your Fountain project
- In the command line (on macOS):
```
cd [your project]
docker run -h fountain -it --rm --name ${PWD##*/} -v $PWD:/usr/app/fountain -p 3000:3000 rgarita/fountainjs
```
- In the command line (on Windows, assuming your project is located at `c:\projects\fountain-helloworld`:
```
cd c:\projects\spfx-helloworld
docker run -h fountain -it --rm --name fountain-helloworld -v /c/projects/fountain-helloworld:/usr/app/fountain -p 3000:3000  rgarita/fountainjs
```

After the container started you can work with it the same way you would work with Fountain installed on your host. To create a new Fountain project in the container command line execute:

```
yo
```

To open the local server after gulp serve navigate in the browser to **https://fountain:3000**.

All files scaffolded by the generator will be stored in your project directory on your host from where you can commit them to source control.

To close the container in the container command line run:
```
exit
```

## Available tags

## Limitations
Windows 10 Anniversary Update and Windows Server 2016 have native support for containers. At this moment Windows supports only containers built on Windows Server Core or Nano Server and you won't be able to run this container natively on Windows. Instead you should use Docker for Windows or Docker Toolbox.