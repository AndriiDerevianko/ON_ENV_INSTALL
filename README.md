[![Docker Birthday Tutorial Voting App](../../raw/master/images/postaddon.png)](../../../jelastic-docker-birthday)
## Docker Birthday Tutorial Voting App

The JPS package deploys Voting App that initially contains 1 application server, 2 database containers and 2 extra containers.

### Highlights
This package is designed to deploy Voting App environment which represents an example of dockers using.

### Environment Topology

![Docker Birthday Tutorial Voting App Topology](https://docs.google.com/drawings/d/1b4iqUgngApIIPujniWqT_dr4WCQbHDA3fUC3_odcfKg/pub?w=448&h=284)

### Specifics

Layer                |     Image          | Number of CTs <br/> by default | Cloudlets per CT <br/> (reserved/dynamic) | Options
-------------------- | :----------------: | :----------------------------: | :---------------------------------------: | :-----:
AS                   | manomarks/examplevotingapp_voting-app:latest |       1                        |           1 / 2                          | links with DB redis
DB                   |    postgres:9.4      |       1                        |           1 / 4                           | -
DB                   |    redis:alpine      |       1                        |           1 / 4                           | -
Extra (result)                   |    manomarks/examplevotingapp_result-app:latest      |       1                        |           1 / 2                           | links with DB postgres
Extra (worker)                   |   manomarks/worker:latest     |       1                        |           1 / 2                           | links with DB postgres and  DB redis

* AS - Application server 
* DB - Database
* Extra - Extra Container (Data) 
* CT - Container

**Postrgres Database**: 9.4

### Deployment

In order to get this solution instantly deployed, click the "Get It Hosted Now" button, specify your email address within the widget, choose one of the [Jelastic Public Cloud providers](https://jelastic.cloud) and press Install.

[![GET IT HOSTED](https://raw.githubusercontent.com/jelastic-jps/jpswiki/master/images/getithosted.png)](https://jelastic.com/install-application/?manifest=https%3A%2F%2Fgithub.com%2Fjelastic-jps%2Fjelastic-docker-birthday%2Fraw%2Fmaster%2Fmanifest.jps)

To deploy this package to Jelastic Private Cloud, import [this JPS manifest](../../raw/master/manifest.jps) within your dashboard ([detailed instruction](https://docs.jelastic.com/environment-export-import#import)).

More information about Jelastic JPS package and about installation widget for your website can be found in the [Jelastic JPS Application Package](https://github.com/jelastic-jps/jpswiki/wiki/Jelastic-JPS-Application-Package) reference.