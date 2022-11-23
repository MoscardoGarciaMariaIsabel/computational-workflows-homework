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
**2. Add the Dockerfile to the repository.** After clonning your Github repository locally, please go the the corresponding local directory. Stage the file for commit to your local repository `git add .`, commit the staged file in the local repository `git commit -m Dockerfile` and push the changes in your local repository `git push origin`.  
**3. Push the Docker image to Docker hub.** The next step would be to build the image of the Dockerfile we created `docker build .`. Then, check for the image ID `docker images | head`, to be able to tag the new image. In this case, the image ID was e3d14a91c7f0 and it was tagged to mariamosgar/homework:latest `docker tag e3d14a91c7f0 mariamosgar/homework:latest`. Once the new image is tagged it is ready to be pushed to the docker hub, by first, login in Docker `docker login` and then, pushing the Dockerfile to your repository `docker push mariamosgar/homework:latest`.  
**4. Run a container and share in files from host.** Since we already cloned our github repository locally we can share the git repository inside the container `docker run -ti -v $(pwd):/shared mariamosgar/homework:latest`.  
**5. Set up a simple python test suite.** The .py file used for this step were obtained from the [original repository](https://github.com/jhale/computational-workflows-homework), by cloning it locally, we could then push this files to our own github repository by adding each file `git add wallet.py` and `git add test_wallet.py`, commit the staged files in the local repository `git commit -m "wallet.py"` and `git commit -m "test_wallet.py"`and push the changes `git ush origin main`.  A pull was required before being able to push the mentioned files to synchronise the local and remote repositories: `git fetch origin main` and `git merge origin main`.  
**6. We can then start a docker container using our image and share our repository into a directory /root/shared into the container by using `docker run -ti -v $(pwd):/root/shared mariamosgar/homework:latest`
