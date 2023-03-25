## A Docker alpine image toy example

Create a Docker image with python 3 and samtools installed.

1. Case: Alpine base image
Issue the below commands to create the image from the Dockerfile

$ cd /path/to/alpine_workshop/alpine_image/
$ docker build -t alpine_test .

After a coupple of minutes the image should be created with no issues.
Let's launch the container and check the samtools version:

$ docker run alpine_test:latest samtools --version

Looks like it's the correct version.

2. Case: Ubuntu 18.04 base image

Issue the below commands to create the image from the Dockerfile

$ cd /path/to/alpine_workshop/ubuntu_image/
$ docker build -t ubuntu_test .

After a coupple of minutes (maybe more than a couple in this case...) the image should be created with no issues.
Let's launch the container and check the samtools version:

$ docker run ubuntu_test:latest samtools --version

Looks good, but what's the difference?
Let's check the size of each image:

$ docker images

Alpine images tend to be 1/2 in size but there's always a trade off... More on alpine images in person.
