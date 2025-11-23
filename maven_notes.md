## Traditional approach without ***Maven***
* Time-consuming setup.
* Human error.
* Lack of consistency.
* Inefficent.
* No standardized directory structure.
* Manual dependency updates.
* No built-in lifecycle management.
* Manual compilation with javac.
* No central repository coordination.
* Custom documentation processes.

## write (.java) -> compile (.class) -> package -> build (.jar format)

# MAVEN 

- Maven is a ***Build automation and Project management*** tool primarly used for Java.
- Maven builds a project using its Project object model (POM) and a set of plugins.
- Manages project dependencies automatically.

### History of Maven:
* It was developed in the year 2002 by ***Jason van xyl***.
* It was released in the year 2004.
* It is owned by Apache software foundation.

### Features of Maven:
* Free and Open source.
* To automate build process.
    - Dependency management.
    - Plugins.
    - Dependencies.
    - Pom.xml
* Maven repositories.
    - Local repositories. 
    - Central repositories.
    - Remote repositories.
* Easy to use.
* Project management.
* Build Automation. (follows build life-cycle)
* Automatic dependency mangement.
* versioning the application.

### Advantages of Maven:

1. easy project setup.
2. maven provides standard directory structure.
3. Dependency management with automatic download.
4. build lifecycle management.
5. follows Repository system.
6. manages documentation, reporting.

### What is Build?

- The process of converting source code into executable file.
- The process include validate, compile, package.

## Build tools:

- It is a software or tool which is used to automate the build process.
- Some of build tools are include 
    1. Ant.
    2. Gradle.
    3. MS build.
    4. Bazel.
    5. PyBuilders.
    6. Maven.
    7. npm.
    8. Yarn.
    9. make.
    10. ninja.

## Maven Installation & Setup:

- Pre-requisites for installing maven
    java installed environment.

- Windows Installation:
    1. Download Maven from maven.apache.org (binary zip archive)
    2. Extract the downlaoded
    3. click on  button
        - search for "edit environment variables for your account"
        - click on environment variables
        - in system variables
        - click new 
        - variable name : MAVEN_HOME
        - copy the extracted file path 
        - paste it in variable path : for example (C:\apache-maven-3.x.x)
        - edit ***Path*** variable and add new: C:\apache-maven-3.x.x\apache-maven-3.x.x\bin
        - click on ***ok***
    4. in cmd verify command using "mvn -version"

- Linux Installation (Ubuntu):
    1. sudo apt update 
    2. sudo apt install maven
    3. in terminal verify command using "mvn -version"

## Maven POM:

- POM stands for **Project Object Model**.
- It contains information related to project and configuration details used by maven to build projects.
- It is an configuration file which contains project structure, dependencies, build configurations, plugins and build profiles.
- ***pom.xml*** helps the maven to build and manage the project.
- It is written in the file called ***pom.xml*** (xml - Extensible Markup language)

### Basic Terminologies:

- **Dependencies:** are the external library/dependencies that are required for the project to function correctly.
- **groupId:** Your organization's domain group that owns project, usually in reverse of domain name. (ex ***google.com*** given as ***com.google***)
- **artifactId:** name of your project or library. (ex ***android***)
- **version:** version of your project. (ex 1.0.0 [major, minor, patch])
- **Plugins:** Tools that perform tasks like compiling code, running tests, generating reports, etc.
- **Plugin Configuration:** Customizes how the plugin behaves, such as setting specific options.

### Components of ***pom.xml***:

1. Project Information Section (<project>):
    - This is the root tag of pom.xml file.
    - Maven reads this to understand what to build and Contains all project settings in one place.

    ```
        <project>
            <!-- project coordinates (AGV - Artifact id, Group id, version)-->
            <!-- project dependencies (libraries needed) -->
            <!-- build configuration (how to compile/test) -->
            <!-- packaging type (JAR, WAR, etc.) -->
            <!-- developer information -->
            <!-- plugins -->
            <!-- build profile-->
        </project>
    ```

2. Project Coordinates Section:
    - The project coordinates section are used to identify the project uniquely.
    - There are three different coordinate available to identify uniquely. They are Artifact id, Group id, Versions.

    ```
        <groupId>com.geeks</groupId>
        <artifactId>maven-pom-example</artifactId>
        <version>1.0-SNAPSHOT</version>
    ```

3. Dependencies Section:
    - In this section we add the external libraries or dependecies which are required for the project.
    - when building maven read config file and downloads the library or dependencies from the repository to your project.
    ```
        <dependencies>
            <dependency>
                <groupId>org.seleniumhq.selenium</groupId>
                <artifactId>selenium-java</artifactId>
                <version>4.6.0</version>
            </dependency>
        </dependencies>
    ```

4. Build Section:
    - In this section define how your project are compiled, tested, packed.
    - It contains instructions and tools needed to convert source code into a machine code or distributable code.

    ```
        <build>     <!-- Build configuration and plugin management -->
            <plugins>
                <plugin>      <!-- Compiler plugin configuration -->
                    <groupId>org.apache.maven.plugins</groupId>
                    <artifactId>maven-compiler-plugin</artifactId>
                    <version>3.8.1</version>
                    <configuration>    <!-- Compiler configuration settings -->
                        <source>1.8</source>    <!-- java 1.8 version for compile -->
                        <target>1.8</target>    <!-- bytecode target 1.8 version -->
                    </configuration>
                </plugin>
            </plugins>
        </build>
    ```

5. Repositories Section:
    - Repository section are used to define maven to fetch dependecies or libraries from specified repositories.

    ```
        <repositories>     <!-- Define where to download dependencies -->
            <repository>
                <id>central</id>                 <!-- Maven Central Repository identifier -->
                <url>https://repo.maven.apache.org/maven2</url>  <!-- Official Maven repo URL -->
            </repository>
            <repository>
                <id>jitpack.io</id>              <!-- JitPack repository identifier -->
                <url>https://jitpack.io</url>    <!-- GitHub repo as Maven dependency source -->
            </repository>
        </repositories>
    ```

6. Profile Section:
    - profile section in maven allows to define different configuration for various environment. (like Development, Testing or Production)
    - Each profile can have their own dependencies, properties for specific tassks.
   
    ```
    <profiles>             <!-- Environment-specific configurations -->
        <profile>                 <!-- Development environment settings -->
            <id>dev</id>           <!-- Profile identifier for development -->
            <properties>           <!-- Development-specific properties -->
                <environment>development</environment>  <!-- Sets environment type -->
                <debug>true</debug>         <!-- Enables debug mode for development -->
            </properties>
        </profile>

        <profile>                           
            <id>prod</id>                 
            <properties>        
                <environment>production</environment>  <!-- Sets environment type -->
                <debug>false</debug>        <!-- Disables debug mode for production -->
            </properties>
        </profile>
    </profiles>
    ```

## Workflow of maven pom.xml file:

1. Initialization - mvn reads the pom.xml file and initialize the build process.
2. Dependency resolution - download the dependencies mentioned in pom.xml file.
3. Build lifecycle - executes the build lifecycle phase like compile, test, pack, verify.
4. plugin execution - run configured plugins for compiling and analyzing code.
5. Package - pack the compiled code into specified format. (jar, war, etc,.)
6. Deploy - deploy the packed code into remote repository or server.

### Types of Maven POM:
##### 1. Super POM:    
- Super POM in maven ***default POM***.
- All POM inherits from its parent or default. 
##### 2. Simplest POM:
- The simplest POM is ***one you define in your project***.
- The simplest POM must defined with **Model Version, Artifact id, Group id, Version(Snapshot)**.
- All other properties will inherited default configuration.
##### 3. Effective POM:
- Effective POM ***combines all the super POM and Simplest POM***.
- Maven does not uses simplest POM to generate project it requires all the configuration.
- Developers can overrite the default configuration.

## Maven Repository:

- It is the location where dependencies, plugins and other build artifacts are stored and retrived.
- There are three types of maven repositories. they include
    1. Local repository.
    2. Central reository.
    3. Remote repository.

**1. Local Repository:**

* It is an directory/folder on your local machine where maven stores all downloaded dependencies, plugins, project specific artifacts.
* The directory local repository is ***.m2***

**2. Central repository:**

* It is the public repository provided by maven project.
* It contains most open-source libraries and artifacts.
* It is the default location where maven will search for dependency, if dependency is not found in local repository.
* location of maven original repository is ***https://mvnrepository.com/***

**3. Remote repository:**

* It is any repository that is hosted on web-server or a private network and can be used to store or retrive artifacts.
* It can be custom repositories provided by third party organization or private repositories setup by organization to host internal dependencies.
* location - we can configure remote url in pom.xml.

## Maven Life cycle:
- It consists of several phases grouped into lifecycles.
- each hadling different aspect of the project lifecycle.
- There types include.
    1. Default life-cycle.
    2. Clean life-cycle.
    3. Site life-cycle.

**1. Default life-cycle:**
- It handles the project build process.
- Phases of default
    1. ***Validate*** - verify that the project is correct all necceary info is available and identifies pom.xml
    2. ***Compile*** - it compiles the project source code into byte code. converts the source code from human readable to machine language.
    3. ***Test-compile*** - compile the project test source code into byte code. 
    4. ***Test*** - runs the project tests.
    5. ***Package*** - packages the compile code into distributed format.
    6. ***Integeration-test*** - after combining all the code, verifies that different modules are componets of a system interact and function together as expected.
    7. ***Verify*** - verifies that package is valid and meets quality criteria.
    8. ***Install*** - install the package into local maven repository for use by other project.
    9. ***Deploy*** - deploy the package to a remote repository, making it available to other projects done by other developers.
```
    Note : when executing a maven command specifing a phase the previous phase get executed.

    if we run package command. it execute all the previous phase of package.
```


**2. Clean life-cycle:**
- It is used to clean up the project, workspace by removing files generated by the previous build.
- Phases of clean cycle include
    1. Pre-clean
    2. Clean
    3. Post-clean

***Pre-clean*** - It executes before the clean phase. it perform any clean perfoemance needed.

***clean*** - delete the project build direectory/folder. removes all files generated by previous build.

***Post-clean*** - It performs after the clean.

**3. Site life-cycle:**
- It generate the project site documentation.
- It includes report such as code coverage, java doc, plugin etc,.
- phases includes
    1. pre-site
    2. site
    3. post-site
    4. site-deploy

***pre-site*** - performs any pre site generation tasks.
***site*** - it generates the project site documentation.
***post-site*** - performs any post site generation task.
***site-deploy*** - it deploy the generated site into a web server or repository.

### Maven directory structure:

```
    project_name
         |
         |-> src
         |   |
         |   |-> main
         |   |
         |   |-> test
         |
         |-> target
         |   |
         |   |-> main
         |   |
         |   |-> test
         |
         |-> pom.xml
```
