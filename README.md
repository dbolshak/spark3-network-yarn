# Descrption
This is silently modified copy of [network-yarn](https://github.com/apache/spark/tree/v3.2.0/common/network-yarn) module based on 3.2.0 spark version.

# Purpose
It allows having two shuffle services in Yarn cluster for different versions of Spark. So it makes possible to run spark2 and spark3 worloads on Yarn simulteniously without any classpath conflicts (aka dependency hell).

# Hadoop
Hadoop version for this project has been changed to 2.6.5.
All hadoop dependenices are used as provided, so it should work on other hadoop versions as well.

# Important
Package `spark.network.yarn` has been renamed to `spark3.network.yarn`, so be carefull setting correct value for property `yarn.nodemanager.aux-services.XXXX.class.`

# Configuration
Default port has been changed from 7337 to 7338.
In order to overwrite default configs of shuffle service use `spark3` suffix instead of just `spark`. For example, to change port of shuffle service please use `spark3.shuffle.service.port` config parameter instead of `spark.shuffle.service.port`.

# Build
To build project you have to run `mvn clean install` command.
So it requires to have maven (at least 3.6.3 version) and java 8.
Or you can download ready to use jar file from releases of this github repository.

# Implementation
- Hadoop version was set to 2.6.5
- Package `spark.network.yarn` was renamed to `spark3.network.yarn`
- All dependenices was shaded to `org/spark3project`
- All constants and text literals (including configuration for shuffle service) was renamed from spark to spark3

# Licence
The project does not contain any extra dependencies comparing to spark project itself.
So it makes sence to use exact the same licence as Apache Spark uses.
LICENCE file is execactly the same as in Apache Spark github repo.
