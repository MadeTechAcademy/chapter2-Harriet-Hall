# Question sheet

Commit your answers to these questions in your copy

## Part 1
Answer these after a day or two to see how much you remember

1. What principle(s) can we apply to improve the size of images?
Begin with a small base image eg scratch
When defining the environment needed to run the code, use a slim version - this provides only what is necessary with no added extras 


1. What principle(s) can we apply to speed up rebuilds of images locally?

When ordering the commands in the dockerfile, ensure those that are less likely to change are above those that will change - the ones that don't changed can be cached

1. What principles can we apply to speed up builds of an image in a pipeline?
Reduce the number of layers in the dockerfile as each layer builds a new container
If images require the same configurations, place these in a seperate dockerfile to create a base image. 
Use smaller base images
add .dockerignore files to ensure only necessary files required to build the project are available 
create multi stage builds - Seperating the build environment from the final runtime environment. The build stage can be copied to a smaller runtimeimage. Also, if you need to change something within the project, only the last stage of the built can be rebuilt - meaning the biild stage can be cached.

1. What are examples of artefacts, files or values we would not want to have baked into a shipped image used in production and why?
secret keys eg Authentification tokens, api keys

1. What principles can we apply to avoid this?
.dockerignore file
 multi stage builds - only the last stage of the built can be rebuilt

1. Which exercise had the biggest impact on the image quality and why?
excersize 4 - strategically ordering the layers made a big difference - it reduced build time and significantly reduced the rebuild time as most of the layers had been cached. 

## Part 2


1. Which is the most important type of problem to fix first and why?
Security related problems - exposure of secure tokens. This may not be as important as we are using Github which prevents users from exposing personal access tokens when committing code, or deletes them then they have been committed. Despite this, this is not good practice, and as the client is the MOJ, we are working with sensative data.

1. What problem have you spotted on your delivery that either needs improving or has been solved by one of these approaches? (or another approach we haven’t discussed)
Images can take several minutes to build and often need rebuilding
I have been advised to distory images at the end of the day as this ensures I have only the latest image available & frees up space in my machine 

1. Give an example of a problem you spotted and the proposal you made for it to be fixed   
2. Give an example of a problem you were involved in fixing and the impact that the fix brought. How was the impact measured?

