# Computational Research Workflows Homework
This is a small summary of the steps to be followed to complete the homework activities of the Computational Research Workflows course, which was taught at the University of Luxembourg on the 10<sup>th</sup> of November 2022.  
**1. Create a Dockerfile.** In the terminal use `vim Dockerfile` command to create a file containing the lines provided in [the homework instructions](https://github.com/jhale/computational-workflows-homework). However, I had to modify the ubuntu version to a lower version (20.04) to avoid errors on the following lines. 
```
FROM ubuntu:20.04

RUN apt-get -y update && \
    apt-get install -y python3-minimal python3-ipython python3-pytest python3-numpy && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
```
**2. Add the Dockerfile to the repository.** After clonning your Github repository locally, please go the the corresponding local directory. Stage the file for commit to your local repository `git add .`, commit the staged file in the local repository `git commit -m Dockerfile` and push the changes to the local repository `git push origin`.  
**3. Push the Docker image to Docker hub.** The next step would be to build the image of the Dockerfile we created `docker build .`. Then, check for the image ID `docker images | head`, to be able to tag the new image. In this case, the image ID was e3d14a91c7f0 and it was tagged to mariamosgar/homework:latest `docker tag e3d14a91c7f0 mariamosgar/homework:latest`. Once the new image is tagged it is ready to be pushed to the docker hub. First, login in Docker `docker login` and then, push the Dockerfile to your repository `docker push mariamosgar/homework:latest`.
