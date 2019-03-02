# CaboLabs EHRServer

[![Build Status](https://travis-ci.org/ppazos/cabolabs-ehrserver.svg?branch=master)](https://travis-ci.org/ppazos/cabolabs-ehrserver)
[![Gitter chat](https://badges.gitter.im/gitterHQ/gitter.png)](https://gitter.im/CaboLabs/EHRServer)


## Clinical Data Management and Sharing Platform compliant with the [openEHR standard](http://openehr.org).

The EHRServer is a general purpose clinical data repository with a REST API and an Management Web Console, [compliant with the openEHR standard](https://cloudehrserver.com/learn), that helps cutting
development time, increase data quality and enable interoperability for clinical
and health/wellness related information systems.


### EHRServer Components

<div align="center">
<img src="https://yuml.me/diagram/scruffy/class/[QUERY%20BUILDER]--%3E[EHR%20BASE],[WEB%20CONSOLE]--%3E[QUERY%20BUILDER],[REST%20API]--%3E[EHR%20BASE],[REST%20API]--%3E[QUERY%20BUILDER],[QUERY%20BUILDER]--%3E[SNOMED%20QUERY],[WEB%20CONSOLE]--%3E[EHR%20BASE]" />
</div>


### Uses Cases

The EHRServer be used as the main [clinical data repository](https://cloudehrserver.com/learn/use_case_health_and_wellness_apps) of your system or app, as a
[shared repository/integrated patient EHR](https://cloudehrserver.com/learn/use_case_shared_health_recods) between many systems, as a
[secondary/backup](https://cloudehrserver.com/learn/use_case_backup_and_query_database) repository, as a
[wearable/monitoring device backend](https://cloudehrserver.com/learn/use_case_monitoring_and_wearables), as a
standardized data source for [datawarehousing](https://cloudehrserver.com/learn/use_case_analytics_and_datawarehousing), as a
[fast prototyping platform](https://cloudehrserver.com/learn/use_case_fast_prototyping_poc),
and as a micro-service platform with many applications like
[clinical decision support](https://cloudehrserver.com/learn/use_case_clinical_decision_support), clinical dashboards, data visualization, reporting, research, etc.


## Community

[Let me know if you are using the EHRServer!](https://twitter.com/ppazos)

[Asks questions and get support](https://gitter.im/CaboLabs/EHRServer)


## Support the project!

One way of supporting this project and our vision for building a completely open
platform for health information systems, it through community donations.
This will be used to pay for servers and development tools we use, also to maintain the website updated and be able to create new guides, and keep all open.

* [5 USD](https://www.paypal.me/cabolabs/5)
* [10 USD](https://www.paypal.me/cabolabs/10)
* [20 USD](https://www.paypal.me/cabolabs/20)
* [50 USD](https://www.paypal.me/cabolabs/50)


Another way of supporting the project is by [subscribing to the CloudEHRServer](https://cloudehrserver.com/pricing)

Thanks for your support!


## Resources

* [Latest documentation](https://www.cabolabs.com/en/projects)
* [REST API documentation](https://docs.google.com/viewerng/viewer?url=http://cabolabs.com/software_resources/EHRServer_v1.2.pdf)
* [CloudEHRServer: EHRServer SaaS](https://cloudehrserver.com/)
* [More guides](https://cloudehrserver.com/learn)


## Main features

* openEHR compliant clinical data repository
* Administrative Web Console
* Simple but powerful REST API
* Supports XML and JSON
* Full audit access for traceability
* Versioned clinical documents
* Query Builder from the Web Console to create data queries (no programming needed!)
* Support of SNOMED CT Expressions on openEHR queries (simplifies complex queries)
* Supports any structure of clinical document (following the openEHR standard information model)
* Vendor Neutral Archive
* Multitenancy


## Based on Open Source Technologies

* [Grails Framework](http://grails.org)
* [Groovy](http://groovy.codehaus.org)
* [Java](http://docs.oracle.com/javase/specs)
* [MySQL](http://dev.mysql.com/downloads/mysql/)


## Test it

Want to try EHRServer?

* [Installing EHRServer](https://cloudehrserver.com/learn/try_it)
* [Subscribe to CloudEHRServer](https://cloudehrserver.com/pricing)



## Install, Configure, Run locally (steop by step)

### Dependencies

1. curl -s get.sdkman.io | bash
2. source "$HOME/.sdkman/bin/sdkman-init.sh"
3. sdk install grails 2.5.6
4. set version by default: Y
5. grails -version

### Database

1. install [MySQL](https://dev.mysql.com/downloads/mysql/)
2. copy the default root password
3. cd /usr/local/mysql/bin
4. ./mysql -u root -p
5. enter default root password
6. ALTER USER 'root'@'localhost' IDENTIFIED BY 'NEW-ROOT-PASSWORD';
8. CREATE DATABASE ehrserver;
9. exit

### EHRServer configuration

1. cd ehrserver/grails-app/conf
2. nano DataSource.groovy
3. change development password to NEW-ROOT-PASSWORD
4. save

### EHRServer environment variables

Mandatory:

    export EHRSERVER_REST_SECRET="6067dba9-1417-41c5-b1af-92208c77ce77"
    export EHRSERVER_SNQUERY_KEY="22222222-2222-2222-2222-222222222222"

Optional:

    export EHRSERVER_EMAIL_FROM="user@yourdomain.com"
    export EHRSERVER_EMAIL_HOST="mail.yourdomain.com"
    export EHRSERVER_EMAIL_PORT=1234
    export EHRSERVER_EMAIL_USER="user@yourdomain.com"
    export EHRSERVER_EMAIL_PASS="youruserpassword"
    export EHRSERVER_ALLOW_WEB_USER_REGISTER=true


### EHRServer run (dev environment)

1. cd ehrserver
2. grails run-app
3. open http://localhost:8090/ehr
4. login with admin/admin/123456
