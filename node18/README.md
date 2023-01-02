As of Jan 1, 2023:

This is actually harder than I thought.
Basically, node18 requires glibc 2.28+, Amazon Linux 2 only has glibc 2.16, so the node 18 install script cannot work. Good news is that there is a newer Amazon Linux 2022, which has the newer glibc versions. BUT, node18 (or any version) setup scripts do not recognize the release version of Amazon Linux 2022, so I have to patch the install script.

Reference:
- [distribution package Amazon Linux 2022 not supported](https://github.com/nodesource/distributions/issues/1367)
