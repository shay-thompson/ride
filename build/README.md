# Building the Ride Framework

Ride is based on the core Java/Maven concepts of modularity and extensibility.  Because of this, you may build all of Ride from the parent pom located in the ```/build``` directory, or any of the sub modules from their root location, where their specific pom resides.

## Syntax and Location

The build command follows the standard maven syntax.  However, because of the inclusion of GPG signing in the dependencies, in order to build locally, you need to add an additional flag ```-Dgpg.skip``` to skip the signing process.

Whether you choose to build one of the framework modules or all of the framework, here is what the command will look like (in your command-line tool of choice): ```mvn clean install -Dgpg.skip```.  

## Unit Tests 

While tests do exist within the sub projects of the Ride framework, the best way to test if the framework was built successfully is to run the integration tests which come in the form of sample assets.  

## Build All Sample Assets

In order to work with the sample assets, it's best to make sure that all of them are built and the way to do that is to build from the parent pom.  In the command-line, navigate to ```/sample/build``` in your local copy of the Ride directories, and run ```mvn clean install```.

## Sample Target Server

In order to run the sample tests against the Ride Components, you need to have two things in place:
- Sample assets built and installed (as described above).
- Have the sample service server running on a webserver.  

Currently, we are working to provision a sample target server to test a build of Ride against.  In the meantime, you may run the sample server locally.  To do this, you need to have [Apache Tomcat ](http://tomcat.apache.org/) 7 or higher running on your localhost.
Once you have verified that, place the WAR file that was created from "Build All Sample Assets" step above (```/sample/sample-service-server/target/sample-service-server.war```) into the webapps folder of your Tomcat instance.

## Integration Tests

To run the tests against the core functionality, open a terminal window in the sample-service-tests an run ```mvn clean verify```.  If you are running a localhost instance of the sample server, you do not need to specify a target server.  If you are running against a server based elsewhere, you'll need to specify it like any other test in Ride by adding a target flag: ```-Dtarget=<config file name in extension project resources>```.  You can read more about resources in the Ride Quickstart guide: see [Ride Extension Resources](https://github.com/adobe/ride/blob/develop/QuickStart.md#resource-code)



