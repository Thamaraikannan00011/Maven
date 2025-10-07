## Traditional approach without ***Maven***
* Time-consuming setup.
* No standardized directory structure.
* Manual dependency updates.
* No built-in lifecycle management.
* Manual compilation with javac.
* No central repository coordination.
* Custom documentation processes.


# MAVEN 

- Maven is a ***Build automation and Project management*** tool primarly used for Java.
- Maven builds a project using its Project object model (POM) and a set of plugins.
- Manages project dependencies automatically.

### Features of Maven:
* Free and Open source.
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
- It is an configuration file which contains project structure, dependencies, build configurations, plugins and build profiles.
- ***pom.xml*** helps the maven to build and manage the project.
- It is written in the file called ***pom.xml*** (xml - Extensible Markup language)

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
    - groupId: Your organization's domain, usually in reverse. (ex ***google.com*** given as ***com.google***)
    - artifactId: name of your project or library. (ex ***android***)
    - version: version of your project. (ex 1.0.0 [major, minor, patch])

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
    - **Plugins:** Tools that perform tasks like compiling code, running tests, generating reports, etc.
    - **Plugin Configuration:** Customizes how the plugin behaves, such as setting specific options.

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

