# SkillsNetworkLabs


## A look at OpenJ9 and AdoptOpenJDK
Cloud-native is an approach to application development and deployment. It's the product of a number of industry movements over the past 10-15 years - agile development practices, DevOps, Microservices and Cloud. Cloud-native applications are developed using agile practices, use continuous integration/continuous delivery to streamline deployment, are architected around team-aligned microservices, and leverage the cloud for rapid deployment at scale.

OpenJ9 is an Eclipse open source JVM. It resulted from the contribution of IBM's JVM implementation to Eclipse and so has many years of high-volume, high-availability production use behind it. It's low footprint, fast startup and high throughput characteristics make it an ideal choice for cloud-native applications - if you pay for your cloud by memory footprint, this is going to be important to you.

Every JVM needs a class library, and most people don't want to build their own Java distribution. The best place to get a build of OpenJ9 is AdoptOpenJDK. This provides pre-built binaries of the OpenJDK class libraries with different JVMs.

`"export JAVA_HOME=/usr" >> ~/.profile;`

`git clone https://github.com/yasmin-aumeeruddy/open-cloud-native-intro.git;`

Run the command: 

`which java`

To find out more about the Java you have installed, run: 

`java -version`

## Build a cloud-native microservice

Navigate in to the project directory that has been provided for you. This contains a pre-build microservice for you to study and extend. 

`cd open-cloud-native-intro`

Build and run the microservice application:

`mvn liberty:dev`

Building the application (`mvn install`) also downloads Open Liberty from Maven Central and installs it to `target/liberty`. The build also packages the application in the `target` directory in a WAR file, called `mpservice.war` and creates a minimal runnable jar containing Open Liberty and the application, called `mpservice.jar`. The `liberty:run` command (Maven goal) starts the `mpserviceServer` server in the `target/liberty` directory.

Note: you will see some warnings from the server relating to SSL configuration. These are expected and will be addressed later.

To see what the app does, open a web browser at the following URL:

http://localhost:9080/mpservice

This displays a simple web page that provides a link to the microservice. On that page, click on the link to the greeting service. This will call the microservice URL: 

http://localhost:9080/mpservice/mpservice/greeting/hello/John%20Doe
