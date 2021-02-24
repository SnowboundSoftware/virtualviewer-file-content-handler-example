# VirtualViewer Sample File Content Handler
By default, VirtualViewer will use its built-in sample handler. This example contains that code that you can build your handler from. This example is provided as-is and should not be used in production.

## API Documentation
The VirtualViewer API documentation is located [here](https://docs.snowbound.com/virtualviewer/latest/content-handler-api/) and [here](https://docs.snowbound.com/virtualviewer/latest/java/docs/content-handler/)

## Supported Versions
At the time this document was written, when using https://repo.snowbound.com/ as your Maven repository, we support version 5.6.0 and newer. If you require an older version, please visit our main support page at http://www.snowbound.com/support or contact us at +1-617-607-2010.

## Requirements
* Java JDK 1.8 or newer
    * VirtualViewer 5.3 and 5.4 require JDK 11
* [Apache Maven](https://maven.apache.org/)
    * To make development easier, the `mvn` command should be part of your system `PATH` variable.
    * On most Linux distros, this will be added automaticly if you install via the package manager.
    * On Windows, add the Maven `bin` directory to your PATH environmental variable.

## Building
Before making any modifications, we recomend you run this command to make sure your system is in a sane state. Using the command line, run `mvn clean verify`. You will find the JAR(s) will output to `target/deploy`. If you prefer to use an IDE, you will need one that supports Maven based projects. We (Snowbound) do not recomend any particular IDE as this is a personal preference.

## Installing Your Handler
To install your new content handler, maven will output a JAR with the required additional dependencies to the `target/deploy` directory. If you are using VirtualViewer on Docker, copy all these files to the `classes` directory and update the `web.xml` to use your content handler. See the VirtualViewer Docker documentation for more information. If you are using a `virtualviewer.war` file, extract the WAR file, install the contenyd of `deploy` output to `virtualviewer/WEB-INF/lib/` and update the contentHandlerClass in `web.xml` file in `virtualviewer/WEB-INF` (see below).

### Configure web.xml
In web.xml, change the `contentHandlerClass` value to the name of your new content handler. In this example, we will use `com.snowbound.virtualviewer.contenthandler.example.FileContentHandler`
