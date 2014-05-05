How to copy Maven dependencies to a folder
==========================================

Description:
Sometimes we want to collect all the jars from maven repository into a single folder so that we can package them easily. Collecting jars is what ant old-timers like to do.

You can do this via the [maven-dependency-plugin](http://maven.apache.org/plugins/maven-dependency-plugin/). see [here](http://maven.apache.org/plugins/maven-dependency-plugin/examples/copying-project-dependencies.html) for more details. 


Add the following to your pom.xml
````
	<profiles>
		<profile>
			<id>qa</id>
			<build>
				<plugins>
					<plugin>
						<artifactId>maven-dependency-plugin</artifactId>
						<executions>
							<execution>
								<phase>install</phase>
								<goals>
									<goal>copy-dependencies</goal>
								</goals>
								<configuration>
									<outputDirectory>{folder}</outputDirectory>
								</configuration>
							</execution>
						</executions>
					</plugin>
				</plugins>
			</build>
		</profile>
	</profiles>
````

then from the command line, 
````
> mvn dependency:copy-dependencies
````
