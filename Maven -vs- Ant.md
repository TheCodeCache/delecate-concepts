
Maven : project and dependency management tool,  it's like a framework.  
Ant: it's just a build tool,  it's like a toolbox.  

Maven: we just need to tell what to do, as it relies on convention  
  like, where to read the source from or where to write the target to.  
  for ex: we can say in a maven script that a project should be packaged as a WAR file, and maven knows how to handle that.  
Ant: we need to tell how to do it, here we need to tell Ant where to read the source from and where to write the output to.   

Maven: configuration file is pom.xml.   
Ant: configuration file is build.xml.   

This is how a `build.xml` looks like:  
```xml
<project name="my-project" default="dist" basedir=".">
    <description>
        simple example build file
    </description>   
    <!-- set global properties for this build -->   
    <property name="src" location="src/main/java"/>
    <property name="build" location="target/classes"/>
    <property name="dist"  location="target"/>

    <target name="init">
      <!-- Create the time stamp -->
      <tstamp/>
      <!-- Create the build directory structure used by compile -->
      <mkdir dir="${build}"/>   
    </target>

    <target name="compile" depends="init"
        description="compile the source " >
      <!-- Compile the java code from ${src} into ${build} -->
      <javac srcdir="${src}" destdir="${build}"/>  
    </target>

    <target name="dist" depends="compile"
        description="generate the distribution" >
      <!-- Create the distribution directory -->
      <mkdir dir="${dist}/lib"/>

      <!-- Put everything in ${build} into the MyProject-${DSTAMP}.jar file -->
      <jar jarfile="${dist}/lib/MyProject-${DSTAMP}.jar" basedir="${build}"/>
   </target>

   <target name="clean"
        description="clean up" >
     <!-- Delete the ${build} and ${dist} directory trees -->
     <delete dir="${build}"/>
     <delete dir="${dist}"/>
   </target>
 </project>
```

This is how a `pom.xml` looks like:  
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.thecodecache</groupId>
	<artifactId>labs</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<name>thecodecache-labs</name>
	<description>the code cache labs</description>

	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<maven.compiler.source>1.8</maven.compiler.source>
		<maven.compiler.target>1.8</maven.compiler.target>
		<antlr.version>4.9.2</antlr.version>
		<exec.varsion>1.6.0</exec.varsion>
	</properties>

	<dependencies>
		<!-- https://mvnrepository.com/artifact/org.antlr/antlr4-runtime -->
		<dependency>
			<groupId>org.antlr</groupId>
			<artifactId>antlr4-runtime</artifactId>
			<version>4.9.2</version>
		</dependency>
		<!-- https://mvnrepository.com/artifact/org.antlr/ST4 -->
		<dependency>
			<groupId>org.antlr</groupId>
			<artifactId>ST4</artifactId>
			<version>4.3.1</version>
		</dependency>

		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<version>4.11</version>
			<scope>test</scope>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.antlr</groupId>
				<artifactId>antlr4-maven-plugin</artifactId>
				<version>${antlr.version}</version>
				<executions>
					<execution>
						<id>run antlr</id>
						<phase>generate-sources</phase>
						<goals>
							<goal>antlr4</goal>
						</goals>
						<configuration>
							<listener>false</listener>
							<visitor>true</visitor>
						</configuration>
					</execution>
				</executions>
			</plugin>
			<plugin>
				<groupId>org.codehaus.mojo</groupId>
				<artifactId>exec-maven-plugin</artifactId>
				<version>${exec.varsion}</version>
			</plugin>
		</plugins>
		<pluginManagement><!-- lock down plugins versions to avoid using Maven 
				defaults (may be moved to parent pom) -->
			<plugins>
				<!-- clean lifecycle, see https://maven.apache.org/ref/current/maven-core/lifecycles.html#clean_Lifecycle -->
				<plugin>
					<artifactId>maven-clean-plugin</artifactId>
					<version>3.1.0</version>
				</plugin>
				<!-- default lifecycle, jar packaging: see https://maven.apache.org/ref/current/maven-core/default-bindings.html#Plugin_bindings_for_jar_packaging -->
				<plugin>
					<artifactId>maven-resources-plugin</artifactId>
					<version>3.0.2</version>
				</plugin>
				<plugin>
					<artifactId>maven-compiler-plugin</artifactId>
					<version>3.8.0</version>
				</plugin>
				<plugin>
					<artifactId>maven-surefire-plugin</artifactId>
					<version>2.22.1</version>
				</plugin>
				<plugin>
					<artifactId>maven-jar-plugin</artifactId>
					<version>3.0.2</version>
				</plugin>
				<plugin>
					<artifactId>maven-install-plugin</artifactId>
					<version>2.5.2</version>
				</plugin>
				<plugin>
					<artifactId>maven-deploy-plugin</artifactId>
					<version>2.8.2</version>
				</plugin>
				<!-- site lifecycle, see https://maven.apache.org/ref/current/maven-core/lifecycles.html#site_Lifecycle -->
				<plugin>
					<artifactId>maven-site-plugin</artifactId>
					<version>3.7.1</version>
				</plugin>
				<plugin>
					<artifactId>maven-project-info-reports-plugin</artifactId>
					<version>3.0.0</version>
				</plugin>
			</plugins>
		</pluginManagement>
	</build>
</project>
```
