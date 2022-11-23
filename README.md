# Computational Research Workflows Homework

**1. Create a Docker file.** In the terminal I used `vim Dockerfile` command to create a file containing the lines provided in [the homework instructions](https://github.com/jhale/computational-workflows-homework):
```
FROM ubuntu:21.04

RUN apt-get -y update && \
    apt-get install -y python3-minimal python3-ipython python3-pytest python3-numpy && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
```
