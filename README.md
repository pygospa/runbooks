# Runbooks

Community driven guides for installing software on different operating systems.

Runbooks is a solution to the "How do I install X on Y problem" that currently involves trawling through inconsistent blog
articles and disparate sources to find the information.

Runbooks may go beyond just "how do I install" and also offer recommendations for installing things "properly". For example:

> How do I install Docker on Ubuntu 16.04

This might contain not only how to install the package but more detailed information about docker user groups etc.

## Notes

Example

```yaml
name: docker-ce
description: Install Docker CE un Ubuntu 16.04
os: ubuntu
version: 16.04
sudo: true
steps:
  - apt-get install apt-transport-https ca-certificates curl software-properties-common
  - curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
  - add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable"
  - apt-get update
  - apt-get install -y docker-ce
```

## Runbooks CLI

runbooks install docker-ce

