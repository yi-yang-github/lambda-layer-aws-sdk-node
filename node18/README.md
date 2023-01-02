# Usage
(Assume your working dir is  this `node18` folder, if not
```
cd node18
```

## Build:
```
docker-compose build
```
This will build / rebuild the `layer.zip` inside docker container at `/tmp/layer.zip`.

## Copy
```
docker-compose up
```
This will copy the `layer.zip` from inside docker container to local `opt/layer.zip`.

## Use
The repo is public so you can directly use this zip file from the github public URL.
E.g. use that in TerraForm.

# How it's built
As of Jan 1, 2023:

This is actually harder than I thought.
Basically, node18 requires glibc 2.28+, Amazon Linux 2 only has glibc 2.16, so the node 18 install script cannot work. Good news is that there is a newer Amazon Linux 2022, which has the newer glibc versions. BUT, node18 (or any version) setup scripts do not recognize the release version of Amazon Linux 2022, so I have to patch the install script.

Reference:
- [distribution package Amazon Linux 2022 not supported](https://github.com/nodesource/distributions/issues/1367)
