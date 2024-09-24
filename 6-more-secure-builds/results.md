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
[
  '/usr/src/app/src/../.npmrc',
  '/usr/src/app/src/../.nvmrc',
  '/usr/src/app/src/../node_modules/.package-lock.json',
  '/usr/src/app/src/../node_modules/@tess-barnes-mt/basic-node-lib/.github/workflows/publish-package.yml',
  '/usr/src/app/src/../node_modules/@tess-barnes-mt/basic-node-lib/.nvmrc',
  '/usr/src/app/src/../node_modules/@tess-barnes-mt/basic-node-lib/README.md',
  '/usr/src/app/src/../node_modules/@tess-barnes-mt/basic-node-lib/package.json',
  '/usr/src/app/src/../package-lock.json',
  '/usr/src/app/src/../package.json',
  '/usr/src/app/src/../src/index.js'
]

History listing from better image:
IMAGE          CREATED              CREATED BY                                      SIZE      COMMENT
5f4a316c2850   About a minute ago   CMD ["/bin/sh" "-c" "node src/index.js"]        0B        buildkit.dockerfile.v0
<missing>      About a minute ago   COPY . . # buildkit                             230kB     buildkit.dockerfile.v0
<missing>      About a minute ago   RUN |1 TOKEN=redacted_token                     6.39kB    buildkit.dockerfile.v0
<missing>      18 minutes ago       COPY package-lock.json package-lock.json # b…   229kB     buildkit.dockerfile.v0
<missing>      18 minutes ago       COPY package.json package.json # buildkit       238B      buildkit.dockerfile.v0
<missing>      18 minutes ago       COPY .npmrc ./.npmrc # buildkit                 100B      buildkit.dockerfile.v0
<missing>      18 minutes ago       WORKDIR /usr/src/app                            0B        buildkit.dockerfile.v0
<missing>      18 minutes ago       ENV NODE_ENV=production                         0B        buildkit.dockerfile.v0
<missing>      18 minutes ago       ENV GITHUB_PAT=redacted_token                   0B        buildkit.dockerfile.v0
<missing>      18 minutes ago       ARG TOKEN=edacted_token                         0B        buildkit.dockerfile.v0
<missing>      4 weeks ago          CMD ["node"]                                    0B        buildkit.dockerfile.v0
<missing>      4 weeks ago          ENTRYPOINT ["docker-entrypoint.sh"]             0B        buildkit.dockerfile.v0
<missing>      4 weeks ago          COPY docker-entrypoint.sh /usr/local/bin/ # …   388B      buildkit.dockerfile.v0
<missing>      4 weeks ago          RUN /bin/sh -c apk add --no-cache --virtual …   5.59MB    buildkit.dockerfile.v0
<missing>      4 weeks ago          ENV YARN_VERSION=1.22.22                        0B        buildkit.dockerfile.v0
<missing>      4 weeks ago          RUN /bin/sh -c addgroup -g 1000 node     && …   118MB     buildkit.dockerfile.v0
<missing>      4 weeks ago          ENV NODE_VERSION=20.17.0                        0B        buildkit.dockerfile.v0
<missing>      4 weeks ago          /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B        
<missing>      4 weeks ago          /bin/sh -c #(nop) ADD file:ee5bb8409915b1141…   8.83MB   

Output from multistage image when run:

[
  '/usr/src/app/src/../.npmrc',
  '/usr/src/app/src/../.nvmrc',
  '/usr/src/app/src/../node_modules/.package-lock.json',
  '/usr/src/app/src/../node_modules/@tess-barnes-mt/basic-node-lib/.github/workflows/publish-package.yml',
  '/usr/src/app/src/../node_modules/@tess-barnes-mt/basic-node-lib/.nvmrc',
  '/usr/src/app/src/../node_modules/@tess-barnes-mt/basic-node-lib/README.md',
  '/usr/src/app/src/../node_modules/@tess-barnes-mt/basic-node-lib/package.json',
  '/usr/src/app/src/../package-lock.json',
  '/usr/src/app/src/../package.json',
  '/usr/src/app/src/../src/index.js'
]