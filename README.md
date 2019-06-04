# arduino-cli
Docker Image for arduino-cli

# Supported tags and respective `Dockerfile` links

-	[`0.3.6-alpha.preview`, `latest` (*Dockerfile*)](https://github.com/ElectroStar/arduino-cli/blob/49e00f9d5e4132ac5b252d8e689a1b646baf902a/Dockerfile)

# Quick reference

-	**Where to get help**:  
  [the Docker Community Forums](https://forums.docker.com/), [the Docker Community Slack](https://blog.docker.com/2016/11/introducing-docker-community-directory-docker-community-slack/), or [Stack Overflow](https://stackoverflow.com/search?tab=newest&q=docker)

-	**Where to file issues**:  
	[GitHub Issues Page](https://github.com/ElectroStar/arduino-cli/issues)

-	**Maintained by**:  
	[ElectroStar](https://github.com/ElectroStar)

### How to use this Image

To use this Image with Gitlab-CI use the following commands in a .gitlab-ci.yml - File:


```
stages:
  - build

build_project:
  stage: build
  image: electrostar/arduino-cli:latest
  script:
    - arduino-cli compile -b arduino:avr:nano:cpu=atmega328old Blink.ino -o Blink.hex
  artifacts:
    paths:
    - Blink.hex
    expire_in: 3 hrs
  only:
    - master
```
Just replace the qualified board name (-b arduino:...) for your specific target and change the names for input project and the output file.

# Installed Packages

-	AVR

To use additional Packages like `megaavr, sam or samd` you have to install these packages first.
To do that just add before_script and use the update-index and install commands like in the following lines:

```
build_project:
  before_script:
    - arduino-cli core update-index
    - arduino-cli core install arduino:megaavr
```

# License

The Dockerfiles and associated scripts are licensed under the [MIT License](https://github.com/ElectroStar/arduino-cli/blob/master/LICENSE).

