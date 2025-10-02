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

