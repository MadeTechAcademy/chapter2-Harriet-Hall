# Measure your progress!

Commit your data here but **remember to redact any token data**!

Error message(s) from original build:

  Dockerfile.original:14
  --------------------
    12 |     
    13 |     # this install command won't work!
    14 | >>> RUN npm ci --omit=dev
    15 |     
    16 |     COPY . .
  --------------------
  ERROR: failed to solve: process "/bin/sh -c npm ci --omit=dev" did not complete successfully: exit code: 1
  ➜  6-more-secure-builds git:(main) ✗ 


Output from better image when run:

  #5 [1/7] FROM docker.io/library/node:20-alpine@sha256:1a526b97cace6b4006256570efa1a29cd1fe4b96a5301f8d48e87c5139438a45
  #5 resolve docker.io/library/node:20-alpine@sha256:1a526b97cace6b4006256570efa1a29cd1fe4b96a5301f8d48e87c5139438a45 done
  #5 sha256:1a526b97cace6b4006256570efa1a29cd1fe4b96a5301f8d48e87c5139438a45 7.67kB / 7.67kB done
  #5 sha256:a6eed5debd912a70eef1480b571bb11ad0259c8b9f46f3ee68c779ea1d37d2cb 1.72kB / 1.72kB done
  #5 sha256:54c50f628c266392c0a8e2f163151ca66b464d71e18783a4bee41ab965434587 6.38kB / 6.38kB done
  #5 DONE 0.0s

  #6 [2/7] WORKDIR /usr/src/app
  #6 DONE 0.0s

  #7 [3/7] COPY .npmrc ./.npmrc
  #7 DONE 0.0s

  #8 [4/7] COPY package.json package.json
  #8 DONE 0.0s

  #9 [5/7] COPY package-lock.json package-lock.json
  #9 DONE 0.0s

  #10 [6/7] RUN npm ci --omit=dev
  #10 1.036 
  #10 1.036 added 1 package in 857ms
  #10 DONE 1.1s

  #11 [7/7] COPY . .
  #11 DONE 0.0s

  #12 exporting to image
  #12 exporting layers 0.0s done
  #12 writing image sha256:92400ba1a7ab0644afe3785b724f2402b992e4b7d76a2f3c01f322224af1d094 done
  #12 naming to docker.io/docker-deep-divd/ex6/better done
  #12 DONE 0.1s

History listing from better image:

  IMAGE          CREATED          CREATED BY                                      SIZE      COMMENT
  92400ba1a7ab   55 seconds ago   CMD ["/bin/sh" "-c" "node src/index.js"]        0B        buildkit.dockerfile.v0
  <missing>      55 seconds ago   COPY . . # buildkit                             230kB     buildkit.dockerfile.v0
  <missing>      55 seconds ago   RUN |1 TOKEN=ghp_zFCD5eqOiLVrPxvp2rehgvOzmAv…   6.38kB    buildkit.dockerfile.v0
  <missing>      56 seconds ago   COPY package-lock.json package-lock.json # b…   229kB     buildkit.dockerfile.v0
  <missing>      56 seconds ago   COPY package.json package.json # buildkit       238B      buildkit.dockerfile.v0
  <missing>      56 seconds ago   COPY .npmrc ./.npmrc # buildkit                 100B      buildkit.dockerfile.v0
  <missing>      56 seconds ago   WORKDIR /usr/src/app                            0B        buildkit.dockerfile.v0
  <missing>      56 seconds ago   ENV NODE_ENV=production                         0B        buildkit.dockerfile.v0
  <missing>      56 seconds ago   ENV GITHUB_PAT=redacted token   0B        buildkit.dockerfile.v0
  <missing>      56 seconds ago   ARG TOKEN=redacted token    0B        buildkit.dockerfile.v0
  <missing>      13 days ago      CMD ["node"]                                    0B        buildkit.dockerfile.v0
  <missing>      13 days ago      ENTRYPOINT ["docker-entrypoint.sh"]             0B        buildkit.dockerfile.v0
  <missing>      13 days ago      COPY docker-entrypoint.sh /usr/local/bin/ # …   388B      buildkit.dockerfile.v0
  <missing>      13 days ago      RUN /bin/sh -c apk add --no-cache --virtual …   5.59MB    buildkit.dockerfile.v0
  <missing>      13 days ago      ENV YARN_VERSION=1.22.22                        0B        buildkit.dockerfile.v0
  <missing>      13 days ago      RUN /bin/sh -c addgroup -g 1000 node     && …   118MB     buildkit.dockerfile.v0
  <missing>      13 days ago      ENV NODE_VERSION=20.17.0                        0B        buildkit.dockerfile.v0
  <missing>      6 weeks ago      /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B        
  <missing>      6 weeks ago      /bin/sh -c #(nop) ADD file:a71f7e9bc66668361…   8.83MB    


Output from multistage image when run:

#0 building with "desktop-linux" instance using docker driver

#1 [internal] load build definition from Dockerfile.multistage
#1 transferring dockerfile: 379B done
#1 DONE 0.0s

#2 [internal] load metadata for docker.io/library/node:20-alpine
#2 DONE 1.6s

#3 [internal] load .dockerignore
#3 transferring context: 704B done
#3 DONE 0.0s

#4 [internal] load build context
#4 transferring context: 229.79kB done
#4 DONE 0.0s

#5 [build 1/7] FROM docker.io/library/node:20-alpine@sha256:1a526b97cace6b4006256570efa1a29cd1fe4b96a5301f8d48e87c5139438a45
#5 resolve docker.io/library/node:20-alpine@sha256:1a526b97cace6b4006256570efa1a29cd1fe4b96a5301f8d48e87c5139438a45 done
#5 sha256:1a526b97cace6b4006256570efa1a29cd1fe4b96a5301f8d48e87c5139438a45 7.67kB / 7.67kB done
#5 sha256:a6eed5debd912a70eef1480b571bb11ad0259c8b9f46f3ee68c779ea1d37d2cb 1.72kB / 1.72kB done
#5 sha256:54c50f628c266392c0a8e2f163151ca66b464d71e18783a4bee41ab965434587 6.38kB / 6.38kB done
#5 DONE 0.0s

#6 [build 2/7] WORKDIR /usr/src/app
#6 DONE 0.0s

#7 [build 3/7] COPY .npmrc ./.npmrc
#7 DONE 0.0s

#8 [build 4/7] COPY package.json package.json
#8 DONE 0.0s

#9 [build 5/7] COPY package-lock.json package-lock.json
#9 DONE 0.0s

#10 [build 6/7] RUN npm ci --omit=dev
#10 1.003 
#10 1.003 added 1 package in 826ms
#10 DONE 1.0s

#11 [build 7/7] COPY . .
#11 DONE 0.0s

#12 [stage-1 1/1] COPY --from=build . .
#12 DONE 0.8s

#13 exporting to image
#13 exporting layers
#13 exporting layers 0.3s done
#13 writing image sha256:0af537bb2640ed7e080dde101c2ecac3caab5482af20930e25efa85de0672c4e done
#13 naming to docker.io/docker-deep-divd/ex6/multistage
#13 naming to doc

History listing from multistage image:

IMAGE          CREATED          CREATED BY                                 SIZE      COMMENT
0af537bb2640   43 seconds ago   CMD ["/bin/sh" "-c" "node src/index.js"]   0B        buildkit.dockerfile.v0
<missing>      43 seconds ago   COPY . . # buildkit                        132MB     buildkit.dockerfile.v0