# Jelastic Docker Birthday Tutorial Voting App Installation Package 

This repository provides [Docker Birthday Tutorial Voting App](http://jelastic.com/) JPS-based installation package for Jelastic Platform.


**jelastic-docker-birthday** is Example Voting App. Docker Birthday Tutorial.

**Engine**: docker

**Environment topology**:

1. 
   - node type: docker
   - count: 1
   - flexibleCloudlets: 2
   - nodeGroup: cp
   - docker: 
     - image: manomarks/examplevotingapp_voting-app:latest
     - links: nosqldb:redis
2. 
   - node type: docker
   - count: 1
   - flexibleCloudlets: 2
   - nodeGroup: result
   - docker: 
     - image: manomarks/examplevotingapp_result-app:latest
     - links: sqldb:db
3. 
   - node type: docker
   - count: 1
   - flexibleCloudlets: 2
   - nodeGroup: worker
   - docker: 
     - image: manomarks/worker:latest
     - links: 
        - sqldb:db
        - nosqldb:redis
4. 
   - node type: docker
   - count: 1
   - flexibleCloudlets: 4
   - nodeGroup: nosqldb
   - docker: 
     - image: redis:alpine
5. 
   - node type: docker
   - count: 1
   - flexibleCloudlets: 4
   - nodeGroup: sqldb
   - docker: 
     - image: postgres:9.4
 
 
### What it can be used for?
You can use this manifest as example


### Deployment

In order to get this solution instantly deployed, click the "Get It Hosted Now" button, specify your email address within the widget, choose one of the [Jelastic Public Cloud providers](https://jelastic.cloud) and press Install.

[![GET IT HOSTED](https://raw.githubusercontent.com/jelastic-jps/jpswiki/master/images/getithosted.png)](https://jelastic.com/install-application/?manifest=https%3A%2F%2Fgithub.com%2Fjelastic-jps%2Fjelastic-docker-birthday%2Fraw%2Fmaster%2Fmanifest.jps)

To deploy this package to Jelastic Private Cloud, import [this JPS manifest](../../raw/master/manifest.jps) within your dashboard ([detailed instruction](https://docs.jelastic.com/environment-export-import#import)).

More information about Jelastic JPS package and about installation widget for your website can be found in the [Jelastic JPS Application Package](https://github.com/jelastic-jps/jpswiki/wiki/Jelastic-JPS-Application-Package) reference.