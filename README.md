# dockerized-idp-testbed
Used to validate the dockerized shibboleth-idp image.

More documentation is forthcoming, but it's a full working IDP, SP, and LDAP server that runs under `docker-compose`. 

1. Update the `idp/Dockerfile` with the version of the base image you want to test.
1. Call `docker-compose build` and then `docker-compose up` (or `docker-compose up -d` to run as a daemon).
1. Browse to `https://idptestbed/` (after setting up an `etc/hosts` file entry pointing to your Docker Host IP), and you can login with `staff1` and `password`.  
1. `ctrl+c` then `docker-compose rm` cleans everything up to try again.

## Prepping for the Test
If testing the IdP build process locally, you'll want to make sure to `docker pull centos:centos7` to ensure that you have the latest before building the IdP. This will ensure that your version will match what Docker Hub will use when it builds. 

Build the IdP with `docker build --tag="unicon/shibboleth-idp:<version>" .`. Make sure the `FROM` entry in testbed's `idp/Dockerfile` matches the tag used in the idp build  or Docker Compose will pull the wrong version when running the Testbed (see step #1).
