How to copy Maven dependencies to a folder
==========================================

Description:
Sometimes we want to collect all the jars from maven repository into a single folder so that we can package them easily.

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
									<outputDirectory>lib</outputDirectory>
								</configuration>
							</execution>
						</executions>
					</plugin>
				</plugins>
			</build>
		</profile>
	</profiles>
````
