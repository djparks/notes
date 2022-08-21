# Maven Cheatsheet

$ cheat maven

REM -- SHARED --
mvn clean package -Dmaven.test.skip=true
mvn clean package -Dmaven.test.skip=true -Pstage-to-IT
mvn clean deploy -Dmaven.test.skip=true -Pstage-to-IT
mvn clean install -Dmaven.test.skip=true -Pstage-to-IT
mvn package -fpomWar.xml -Dmaven.test.skip=true
mvn clean package -Ppkg-dev

-- -----------------------------------------------------------------
--  MVN VERSION Commands  -- http://mojo.codehaus.org/versions-maven-plugin/index.html
-- -----------------------------------------------------------------
mvn versions:set -DnewVersion=1.2.3-your-new-version
mvn -N versions:update-child-modules
mvn versions:display-dependency-updates
---

mvn package --debug

mvn help:effective-pom > effective.xml
mvn help:effective-settings > effective.xml
mvn help:effective-pom

-------------------BRANCH
mvn release:branch -DbranchName=msis-2010.04_BRANCH

---------------- Archetype
mvn archetype:create -DgroupId=com.monsanto.commercial.agsolutions -DartifactId=agservices-sso -DarchetypeArtifactId=maven-archetype-site-simple
mvn archetype:create -DgroupId=com.monsanto.commercial.agsolutions -DartifactId=agservices-sso -DarchetypeArtifactId=maven-archetype-webapp

C:\projects\MSIS_Shared\java-shared\target\msis-shared-java-2008.10.02-SNAPSHOT.jar

mvn install:install-file -Dfile=C:\projects\MSIS_Admin\lib\ditchnet-tabs-taglib-0.8.jar -DgroupId=org.ditchnet -DartifactId=ditchnet-tabs -Dversion=0.8 -Dpackaging=jar
mvn install:install-file -Dfile=C:\projects\MSIS_EAR\ANT\msis-shared-web-2009.07.2-SNAPSHOT.war -DgroupId=com.monsanto.commercial.msis -DartifactId=msis-shared-web -Dversion=2009.07.2-SNAPSHOT -Dpackaging=war
mvn install:install-file -Dfile=C:\projects\MSIS_EAR\ANT\msis-shared-java-2009.07.2-SNAPSHOT.jar -DgroupId=com.monsanto.commercial.msis -DartifactId=msis-shared-java -Dversion=2009.07.2-SNAPSHOT -Dpackaging=jar

mvn install:install-file -DgroupId=com.monsanto.commercial.msis -Dartifact Id=msis-shared-web -Dversion=2008.10.2-SNAPSHOT -Dpackaging=war -Dfile=/path/to/
file
mvn site -- builds reports

set maven_opts='-Dlsi.function=win -DMONCRYPTJV=C:\MONCRYPTJV -Djava.endorsed.dirs=C:\apache\jakarta-tomcat-5.5.20\common\endorsed -Dcatalina.base=C:\www\tomcat-5.5.20'
--------------------------
Release Steps
** Have own directory with pulled code for tag or branch.
1) mvn scm:update
2) mvn release:prepare
3) mvn -Pstage_to_dev release:perform

--------------------------
mvn package -Dmaven.test.skip=true
mvn release:prepare -DdryRun=true
mvn scm:update

mvn idea:idea

mvn install - puts in local repository.
mvn deploy - puts in repository form everyone.
**

mvn install:install-file -Dfile=C:\projects\MSIS_Shared\target\msis-shared-1.0.0-SNAPSHOT.jar -DgroupId=com.monsanto.commercial.msis -DartifactId=msis-shared -Dversion=1.0.0-SNAPSHOT -Dpackaging=jar

mvn install:install-file -Dfile=C:\projects\MSIS_Shared\Source\build\msis_shared-web-1_0_0.war -DgroupId=com.monsanto.commercial.msis -DartifactId=msis-shared-web -Dversion=1.0.0 -Dpackaging=war


mvn install:install-file -Dfile=c:\www\tomcat_5.5.20\common\lib\jsp-api.jar -DgroupId=javax.servlet -DartifactId=jsp-api -Dversion=2.4 -Dpackaging=jar
mvn install:install-file -Dfile=C:\www\tomcat_5.5.20\common\lib\commons-el.jar -DgroupId=commons-el -DartifactId=commons-el -Dversion=1.1 -Dpackaging=jar


C:\Documents and Settings\djpark\.m2\repository\com\monsanto\commercial\msis\msis-shared\1.0.0-SNAPSHOT\msis-shared-1.0.0-SNAPSHOT.jar

IntelliJ integration:
Build tab of maven settings, can turn on tests.

SCOPES:
compile
provided (only needed at compile time, not run time)
runtime
test
system (somehow always available)


project.build.finalname


            <manifestEntries>
              <mode>development</mode>
              <url>${pom.url}</url>
              <time>${date}</time>
              <time1>${now}</time1>
              <time2>${system.timestamp}</time2>
              <time3>${today}</time3>
              <time4>${time}</time4>
              <project-version>{project.version}</project-version>
           <Implementation-Title>${pom.name}</Implementation-Title>
           <Implementation-Version>${pom.version}</Implementation-Version>
           <Implementation-Vendor-Id>${pom.groupId}</Implementation-Vendor-Id>
           <Implementation-Vendor>${pom.organization.name}</Implementation-Vendor>
           <Implementation-Artifact>${pom.artifactId}</Implementation-Artifact>
            </manifestEntries>


          <webResources>
            <!-- TODO [mkp] Maven 2.0 has a bug where context.xml is filtered from packaged WAR.
                 Fixed in 2.1.  When we upgrade we can remove workaround and use the following...
                 <containerConfigXML>META-INF/context.xml</containerConfigXML>
            -->
            <resource>
              <directory>${basedir}/META-INF</directory>
              <includes>
                <include>context.xml</include>
              </includes>
              <targetPath>META-INF</targetPath>
            </resource>
            <resource>
              <directory>${basedir}/src/main/java</directory>
              <includes>
                <include>*.log4j.properties</include>
              </includes>
              <targetPath>WEB-INF/classes</targetPath>
            </resource>
          </webResources>
To build and thus create the project's artifact (war, jar, etc):

mvn package



To clean all previous build files:

mvn clean



To clean all previous build files and then build:

mvn clean package



If you want to do the above but in a "off-line" mode

mvn -o clean package



To clean all previous build files, then build, then install in the local

repository:

mvn clean package install



---------------------------------



Installing Artifact in Local Repository

mvn clean install



To build the package file (jar, war, etc) allowing test failure:

mvn -Dmaven.test.failure.ignore=true package



To generate Eclipse project descriptor after configuring the dependencies in

pom.xml:

mvn eclipse:eclipse



To clean previous generated Eclipse support files and then generate Eclipse

project descriptor after configuring the dependencies in pom.xml:

mvn eclipse:clean eclipse:eclipse



To generate the project's development support site

mvn site



To generate site documentation without running the tests (handy while updating

the APTs):

mvn -Dmaven.test.skip=true clean site



To generate javadoc

mvn javadoc:javadoc



To generate javadoc stuffed into a jar file

mvn javadoc:jar



To create a new non web app Java project (artifact is jar):

mvn archetype:create -DgroupId=com.mycompany.app -DartifactId=my-app



To create a new web app Java project (artifact is war):

mvn archetype:create -DgroupId=com.mycompany.app -DartifactId=my-webapp

-DarchetypeArtifactId=maven-archetype-webapp



To check the version of Maven:

mvn --version



To run unit tests:

mvn test



To distribute the source code:

mvn assembly:assembly -DdescriptorId=src



To install a jar file on local repo:

mvn install:install-file -Dfile=foo.jar -DgroupId=bar -Dversion=x.y

-Dpackaging=jar -DartifactId=blah



To install the oracle ojdbc14_g.jar file on local repo:

Optionally Download the Oracle JDBC driver from

http://www.oracle.com/technology/software/tech/java/sqlj_jdbc/index.html

Q:

cd C:\some\path\to\file\oracle

mvn install:install-file -DgroupId=com.oracle -DartifactId=ojdbc14_g

-Dversion=10.2.0.1.0 -Dpackaging=jar -Dfile=ojdbc14_g.jar

Then add a dependency in the pom.xml file similar to the following

 <project>

 <dependencies>

        <dependency>

                <groupId>com.oracle</groupId>

                <artifactId>ojdbc14_g</artifactId>

                <version>10.2.0.1.0</version>

        </dependency>

 </dependencies>

 </project>



Installing 3rdParty jar in local repository:

mvn install:install-file -Dfile=foo.jar -DgroupId=org.foosoft -DartifactId=foo

-Dversion=1.2.3 -Dpackaging=jar



Setting Compiler Version

 <project>

   <build>

      <plugins>

         <plugin>

         <artifactId>maven-compiler-plugin</artifactId>

            <configuration>

               <source>1.6</source>

               <target>1.6</target>

            </configuration>

         </plugin>

      </plugins>

   </build>

 </project>



Standard Project Structure

/new-app/pom.xml               maven2 project file

/new-app/src/                  Sources

/new-app/src/main/java/               Java source tree

/new-app/src/test/java/               Java unit tests

/new-app/src/main/resources/   Java classpath resources

/new-app/src/test/resources/   Resources for unit-tests

/new-app/target/classes/       compiles classes

/new-app/target/test-classes/  compiles test classes

/new-app/target/dots           other plugins' output

/newwebapp/src/main/webapp     root of webapp





Generic Create Commands using Archetypes

Create a jar artifact project

mvn archetype:create -DgroupId=com.mycompany.app -DartifactId=my-app



Create a web app, war artifact project

mvn archetype:create -DgroupId=com.mycompany.app -DartifactId=my-webapp

-DarchetypeArtifactId=maven-archetype-webapp



Add documentation source

mvn archetype:create -DarchetypeGroupId=org.apache.maven.archetypes

-DarchetypeArtifactId=maven-archetype-site -DgroupId=com.mycompany.app

-DartifactId=my-app-site



Create a Groovy based project, groovy-jar artifact project

mvn archetype:create \

    -DarchetypeGroupId=org.codehaus.mojo.groovy \

    -DarchetypeArtifactId=groovy-maven-archetype \

    -DgroupId=com.mycompany.app \

    -DpackageName=com.mycompany.app.mygroovymodule \

    -DartifactId=my-groovy-module



Fake Specific Create Commands



create a jar artifact project

mvn archetype:create -DgroupId=com.mycompany.app -DartifactId=my-app



Create a web app, war artifact project

mvn archetype:create -DgroupId=com.mycompany.app -DartifactId=my-app

-DarchetypeArtifactId=maven-archetype-webapp


Add documentation source

mvn archetype:create -DarchetypeGroupId=org.apache.maven.archetypes

-DarchetypeArtifactId=maven-archetype-site -DgroupId=com.mycompany.app

-DartifactId=my-app

or cd into project dir

mvn archetype:create -DarchetypeGroupId=org.apache.maven.archetypes

-DarchetypeArtifactId=maven-archetype-site


Creating a war project

http://maven.apache.org/guides/mini/guide-webapp.html

 