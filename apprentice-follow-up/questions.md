# Question sheet

Commit your answers to these questions in your copy

## Part 1
Answer these after a day or two to see how much you remember

1. What principle(s) can we apply to improve the size of images?

-	Begin with a small base image eg scratch images. Scratch images are empty images that give developers full control over the dependencies and software they require for their application. Therefore, the images that are built can be lightweight. 
However, many developers prefer to use base images with a set of commonly-used libraries and packages as this saves time and reduces the risk of human error. 
-   	The ‘slim’ tag reduces the size of images and ensures only the necessary components are available to run the application with no added extras. Docker images with this tag are usually large base images. Other images including Alpine are already minimal image, often smaller than those with the slim tag.  
- 	Minimising the number of layers 


1. What principle(s) can we apply to speed up rebuilds of images locally?

Immutability: when ordering the commands in the dockerfile, ensure those that are less likely to change are above those that will change - the ones that don't changed can be cached

Resource Optimisation: destroying old images and containers helps free up disk space and reduces the risk of build failures due to insufficient storage.

1. What principles can we apply to speed up builds of an image in a pipeline?

Layer caching: reduce the number of layers in the dockerfile as each layer builds a new container 
If images require the same configurations, place these in a separate dockerfile to create a base image. 
Use smaller base images
.dockerignore: add files to .dockerignore to ensure only necessary files required to build the project are available 
Multi stage builds - While the initial build may be slower as there are more build stages needing to be built, subsequent builds may be faster since the build environment can be separated from the final runtime environment - meaning the build environment does not need to be rebuilt if something changes in production.

1. What are examples of artefacts, files or values we would not want to have baked into a shipped image used in production and why?
Secret keys: authorisation tokens, api keys & the files in which they may be referenced - this can make the application vulnerable to security breaches, or hackers stealing personal information
The Dockerfile: or any file that reveals too much about the configuration of the applications 
Version control directories: this can be a security risk as sensitive information can be committed and made public - and ultimately misused   

1. What principles can we apply to avoid this?
.dockerignore file: prevents files from being available in version control
Multi-stage builds: they ensure that the final image includes only the essential artefacts needed for production. The tools and dependencies used during the build process are excluded from the final image.

1. Which exercise had the biggest impact on the image quality and why?
exercise 4 - strategically ordering the layers made a big difference - it reduced build time and significantly reduced the rebuild time as most of the layers had been cached. 

## Part 2


1. Which is the most important type of problem to fix first and why?
Security related problems: exposure of secure tokens. This may not be as important as we are using Github which prevents users from exposing personal access tokens when committing code, or deletes them then they have been committed. Despite this, this is not good practice, especially when working with sensitive data. 

1. What problem have you spotted on your delivery that either needs improving or has been solved by one of these approaches? (or another approach we haven’t discussed)
Images can take several minutes to build and often need rebuilding
Resource Optimisation: I have been advised to destroy images at the end of the day to ensure I have only the latest image available. This frees up space on my machine, which is particularly useful when disk space is limited, and helps reduce performance degradation.

1. Give an example of a problem you spotted and the proposal you made for it to be fixed 

On my project the Dockerfiles are not referenced in the .dockerignore files. This is something I queried with my team and suggested that maybe they should be as they reveal information about how our images are built. However, since sensitive information is not available in the dockerfiles and is instead stored in environment variables, and our repos are private, this is not required. According to various articles online, it seems that the decision of whether or not to put the Dockerfile in the .dockerignore is a matter of personal preference. Keeping it out may be favourable in certain circumstances when greater transparency is required, especially in open-source or shared projects.
 
2. Give an example of a problem you were involved in fixing and the impact that the fix brought. How was the impact measured?
