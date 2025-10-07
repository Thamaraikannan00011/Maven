## MAVEN Commands by Life-cycle:

### Default Life-cycle (Build):

1. **mvn validate** - Validates project structure and POM file configuration

2. **mvn compile** - Compiles main source code (src/main/java)
   - **mvn compiler:compile** - Alternative way to compile main source only

3. **mvn test-compile** - Compiles test source code (src/test/java)
   - **mvn compiler:testCompile** - Alternative way to compile tests only

4. **mvn test** - Executes unit tests using Surefire plugin
   - **mvn test -Dtest=ClassName** - Runs specific test class
   - **mvn test -DskipTests** - Skips test execution but compiles them
   - **mvn surefire:test** - Explicitly runs Surefire tests

5. **mvn package** - Creates distributable format (JAR/WAR/EAR)
   - **mvn jar:jar** - Creates JAR file specifically
   - **mvn war:war** - Creates WAR file for web applications
   - **mvn source:jar** - Packages source code into JAR

6. **mvn integration-test** - Runs integration tests in isolated environment
   - **mvn failsafe:integration-test** - Executes integration tests using Failsafe plugin

7. **mvn verify** - Verifies package validity and quality checks
   - **mvn failsafe:verify** - Verifies integration test results

8. **mvn install** - Installs package to local repository (~/.m2/repository)
   - **mvn install:install-file** - Manually installs external JAR to local repo
   - **mvn install -DskipTests** - Installs without running tests

9. **mvn deploy** - Uploads artifact to remote repository (Nexus/Artifactory)
   - **mvn deploy:deploy-file** - Deploys specific file to remote repository

---

### Clean Life-cycle (Cleanup):

1. **mvn pre-clean** - Executes processes before project cleaning (rarely used directly)

2. **mvn clean** - Deletes target directory and generated files
   - **mvn clean:clean** - Explicit clean execution
   - **mvn clean compile** - Cleans then compiles
   - **mvn clean install** - Cleans then installs
   - **mvn clean package** - Cleans then packages

3. **mvn post-clean** - Executes processes after project cleaning (rarely used directly)

---

### Site Life-cycle (Documentation):

1. **mvn pre-site** - Executes processes before site generation (rarely used directly)

2. **mvn site** - Generates project documentation website
   - **mvn site:site** - Explicit site generation
   - **mvn site:run** - Runs site locally for preview
   - **mvn javadoc:javadoc** - Generates API documentation only
   - **mvn surefire-report:report** - Generates test results report

3. **mvn post-site** - Executes processes after site generation (rarely used directly)

4. **mvn site-deploy** - Deploys generated site to remote web server
   - **mvn site:deploy** - Alternative command for site deployment

---

### Independent/Plugin-Specific Commands (Not tied to life-cycle):

#### Dependency Management:
- **mvn dependency:tree** - Shows project dependency hierarchy
- **mvn dependency:resolve** - Downloads all project dependencies
- **mvn dependency:analyze** - Detects unused/undeclared dependencies
- **mvn dependency:purge-local-repository** - Clears and re-downloads dependencies
- **mvn dependency:copy-dependencies** - Copies dependencies to target folder

#### Version Management:
- **mvn versions:display-dependency-updates** - Shows available dependency updates
- **mvn versions:display-plugin-updates** - Shows available plugin updates
- **mvn versions:set -DnewVersion=X.Y.Z** - Updates project version
- **mvn versions:use-latest-releases** - Updates dependencies to latest releases

#### Release Management:
- **mvn release:prepare** - Prepares release (version tagging, updates)
- **mvn release:perform** - Executes the actual release process
- **mvn release:clean** - Cleans release preparation files

#### Execution Commands:
- **mvn exec:java** - Executes Java main class
- **mvn spring-boot:run** - Runs Spring Boot application
- **mvn tomcat7:run** - Starts embedded Tomcat server
- **mvn jetty:run** - Starts embedded Jetty server

#### Help & Information:
- **mvn help:describe** - Describes plugin goals and parameters
- **mvn help:effective-pom** - Shows complete POM with inheritance
- **mvn help:active-profiles** - Lists currently active profiles
- **mvn help:system** - Displays system properties and environment variables

#### IDE Integration:
- **mvn eclipse:eclipse** - Generates Eclipse project files
- **mvn eclipse:clean** - Removes Eclipse project files
- **mvn idea:idea** - Generates IntelliJ IDEA project files

#### Project Creation:
- **mvn archetype:generate** - Creates new project from template
- **mvn archetype:create-from-project** - Creates archetype from existing project

#### Debugging Options (Flags):
- **mvn -X [goal]** - Debug mode with verbose output
- **mvn -e [goal]** - Shows full error stack traces
- **mvn -U [goal]** - Forces dependency updates (snapshots/releases)
- **mvn -o [goal]** - Offline mode (uses only local repository)
- **mvn -DskipTests [goal]** - Skips test execution
- **mvn -Dmaven.test.skip=true [goal]** - Skips test compilation and execution
- **mvn -P profile-name [goal]** - Activates specific Maven profile

---

### Common Combined Commands:

- **mvn clean install** - Full build with cleanup
- **mvn clean package -DskipTests** - Package without tests
- **mvn clean verify -U** - Clean, verify and update dependencies
- **mvn clean install -P production** - Build with production profile
- **mvn dependency:tree clean install** - Show dependencies then build