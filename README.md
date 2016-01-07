build-resources
===============

<a href="https://raw.githubusercontent.com/groupon/api-build-resources/master/LICENSE">
    <img src="https://img.shields.io/hexpm/l/plug.svg"
         alt="License: Apache 2">
</a>
<a href="https://travis-ci.org/groupon/api-build-resources/">
    <img src="https://travis-ci.org/groupon/api-build-resources.png"
         alt="Travis Build">
</a>
<a href="http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22com.groupon.api%22%20a%3A%22build-resources%22">
    <img src="https://img.shields.io/maven-central/v/com.groupon.api/build-resources.svg"
         alt="Maven Artifact">
</a>

Resources for building Groupon API projects.

Usage
-----

### Checkstyle

Determine the latest version of the build resources in [Maven Central](http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22com.groupon.api%22%20a%3A%22build-resources%22).  If you have not, you should consider using the [API Parent Pom](https://github.com/groupon/api-parent-pom) instead of directly integrating with the build-resources package.

To integrate with the [Maven Checkstyle Plugin](https://maven.apache.org/plugins/maven-checkstyle-plugin/) declare a dependency on the build-resources package and set the __configLocation__, __propertyExpansion__ and __suppressionsLocation__ as shown below.

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-checkstyle-plugin</artifactId>
    <version>${maven.checkstyle.plugin.version}</version>
    <executions>
        <execution>
            <id>checkstyle-check</id>
            <phase>verify</phase>
            <goals>
                <goal>checkstyle</goal>
                <goal>checkstyle-aggregate</goal>
                <goal>check</goal>
            </goals>
            <configuration>
                <consoleOutput>true</consoleOutput>
                <logViolationsToConsole>true</logViolationsToConsole>
                <failOnViolation>true</failOnViolation>
                <maxAllowedViolations>0</maxAllowedViolations>
                <includeTestSourceDirectory>true</includeTestSourceDirectory>
                <configLocation>api_coding_conventions.xml</configLocation>
                <propertyExpansion>suppressions.file=${project.build.directory}/checkstyle-suppressions.xml</propertyExpansion>
                <suppressionsLocation>checkstyle-suppressions.xml</suppressionsLocation>
            </configuration>
        </execution>
    </executions>
   <dependencies>
       <dependency>
           <groupId>com.groupon.api</groupId>
           <artifactId>build-resources</artifactId>
           <version>VERSION</version>
       </dependency>
   </dependencies>
</plugin>
```

Building
--------

Prerequisites:
* [JDK8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
* [Maven 3.3.3+](http://maven.apache.org/download.cgi)

Building:

    api-build-resources> mvn verify

To use the local version you must first install it locally:

    api-build-resources> mvn install

You can determine the version of the local build from the pom file.  Using the local version is intended only for testing or development.

License
-------

Published under Apache Software License 2.0, see LICENSE

&copy; Groupon Inc., 2014
