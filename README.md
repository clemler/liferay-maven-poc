liferay-maven-poc
=================

This repository contains a set of Liferay *proof of concept* (POC) projects
that leverage Liferay 6.1, and the Liferay Maven SDK.

Prerequisites
--------------
* Maven 3
* A copy of the Liferay 6.1 community edition
* The top level *pom.xml* file assumes there is a directory called 
*bundle* that contains the Liferay runtime. The directory structure is as follows:
    * bundle (contains liferay runtime)
        * liferay-ce-6.1
    * liferay-maven-poc
        * pom.xml
        * README.md
        * Maven modules for the various examples


        INITIAL SETUP
        -------------
        You must edit the top level pom.xml and set the properties 
        'liferay.auto.deploy.dir', and 'liferay.version'. You
        must be careful to NOT checkin your custom changes back
        into subversion. The default value is used for the 
        Bamboo automated builds.

        CREATING A PROJECT
        ===================
        Open command prompt or  terminal and go to your project directory. Next 
        we'll going to create a portlet project using  a liferay portlet project template.
        Type the following in your terminal window:

        mvn archetype:generate

        That command will create a list of available project templates like below:

        ...
        21: remote -> com.liferay.maven.archetypes:liferay-ext-archetype (Provides an archetype to create Liferay extensions.)
        22: remote -> com.liferay.maven.archetypes:liferay-hook-archetype (Provides an archetype to create Liferay hooks.)
        23: remote -> com.liferay.maven.archetypes:liferay-layouttpl-archetype (Provides an archetype to create Liferay layout templates.)
        24: remote -> com.liferay.maven.archetypes:liferay-portlet-archetype (Provides an archetype to create Liferay portlets.)
        25: remote -> com.liferay.maven.archetypes:liferay-servicebuilder-archetype (Provides an archetype to create Liferay Service Builder portlets.)
        26: remote -> com.liferay.maven.archetypes:liferay-theme-archetype (Provides an archetype to create Liferay themes.)
        27: remote -> com.liferay.maven.archetypes:liferay-web-archetype (Provides an archetype to create Liferay webs.)
        ...
        Choose a number or apply filter (format: [groupId:]artifactId, case sensitive contains): 171:
        view rawtemplates snippetThis Gist brought to you by GitHub.

        Choose number 24 or what ever the number you have for com.liferay.maven.archetypes:liferay-portlet-archetype

        Next you will be asked to choose the template version: 

        Choose version:
        1: 6.0.2
        2: 6.0.3
        3: 6.0.4
        4: 6.0.5
        5: 6.0.6
        6: 6.1.0
        7: 6.2.0-SNAPSHOT
        view rawversion snippetThis Gist brought to you by GitHub.

        Choose number 6 or what ever you have for 6.1.0 version.

        Next you will be asked to provide groupId, artifactId and version:

        Define value for property 'groupId': : com.liferay.sample
        Define value for property 'artifactId': : sample-portlet
        Define value for property 'version': 1.0-SNAPSHOT: :
        Define value for property 'package': com.liferay.sample: :
        Confirm properties configuration:
        groupId: com.liferay.sample
        artifactId: sample-portlet
        version: 1.0-SNAPSHOT
        package: com.liferay.sample
         Y: :
        view rawtemplate properties snippetThis Gist brought to you by GitHub.

        For groupId use the same as in the first pom.xml. In my case it would be com.liferay.sample. For artifactId I chose sample-portlet as this is the directory it will create. Version should be the same as the project parent. Once you have confirmed the values maven will create the portlet project and add it to you parent project as module automatically.

        Now you project structure should be something like this:

        pom.xml
        sample-portlet
        sample-portlet/pom.xml
        sample-portlet/src
        sample-portlet/src/main
        sample-portlet/src/main/java
        sample-portlet/src/main/resources
        sample-portlet/src/main/webapp
        sample-portlet/src/main/webapp/css
        sample-portlet/src/main/webapp/css/main.css
        sample-portlet/src/main/webapp/icon.png
        sample-portlet/src/main/webapp/js
        sample-portlet/src/main/webapp/js/main.js
        sample-portlet/src/main/webapp/view.jsp
        sample-portlet/src/main/webapp/WEB-INF
        sample-portlet/src/main/webapp/WEB-INF/liferay-display.xml
        sample-portlet/src/main/webapp/WEB-INF/liferay-plugin-package.properties
        sample-portlet/src/main/webapp/WEB-INF/liferay-portlet.xml
        sample-portlet/src/main/webapp/WEB-INF/portlet.xml
        sample-portlet/src/main/webapp/WEB-INF/web.xml
        view rawproject file listingThis Gist brought to you by GitHub.

        4) Go to sample-portlet directory and run 

        mvn package

        This will compile any classes and packages the portlet war file in target directory. 

        5) To deploy the portlet into your Liferay bundle you can run

        mvn liferay:deploy

        Now you have created your first Liferay plugin project with maven and deployed it to your Liferay bundle.
  
Foo


