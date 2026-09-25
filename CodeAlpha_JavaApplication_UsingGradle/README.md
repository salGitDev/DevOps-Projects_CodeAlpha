# CodeAlpha - Java Application Using Gradle

A simple Java application built and managed with **Gradle** as part of the **CodeAlpha DevOps Internship**. This project demonstrates build automation, dependency management, testing, report generation, and executable JAR creation using Java 19.

---

## Objectives

* Automate Java project builds using Gradle.
* Manage external libraries using Gradle dependencies.
* Generate an executable JAR file.
* Execute automated unit tests.
* Produce an HTML test report.
* Demonstrate Java 19 project configuration.

---

## Technologies Used

* Java 19
* Gradle
* SQLite JDBC
* JUnit Jupiter
* Visual Studio Code

---

## Project Structure

```text
CodeAlpha_JavaApplication_UsingGradle
│
├── app
│   ├── src
│   │   ├── main
│   │   └── test
│   ├── build.gradle
│   └── build
│
├── assets
│   ├── java-version.png
│   ├── sqlite-jdbc-dependency.png
│   ├── dependency-report.png
│   ├── test-report.png
│   ├── build-success.png
│   └── run-output.png
│
├── gradlew
├── gradlew.bat
├── settings.gradle
└── README.md
```

---

## Project Verification

The following tasks were completed successfully during development.

### 1. Java 19 Configuration

Verified that Java 19 was correctly installed and configured.

**Commands**

```bash
java -version
javac -version
```

**Result**

* Java Runtime verified
* Java Compiler verified
* Project configured to use Java 19

---

### 2. Dependency Management

Added the SQLite JDBC driver to the Gradle project by editing the `app/build.gradle` file.

```gradle
implementation 'org.xerial:sqlite-jdbc:3.50.3.0'
```

Verified the dependency using:

```bash
gradlew :app:dependencies
```

**Result**

* SQLite JDBC successfully downloaded
* Dependency resolved by Gradle

---

### 3. Build the Application

Compiled the project and generated an executable JAR.

**Command**

```bash
gradlew build
```

Generated JAR location:

```text
app/build/libs/
```

**Result**

* Project compiled successfully
* Executable JAR generated

---

### 4. Run the Application

Executed the application using Gradle.

```bash
gradlew run
```

The generated JAR can also be executed directly:

```bash
java -jar app/build/libs/<jar-file-name>.jar
```

**Result**

* Application executed successfully

---

### 5. Automated Testing

Executed the unit tests.

```bash
gradlew test
```

Generated HTML report:

```text
app/build/reports/tests/test/index.html
```

**Result**

* All tests passed successfully (100%)
* HTML report generated

---

## Screenshots

The **assets/** directory contains screenshots demonstrating:

* Java 19 verification
* SQLite JDBC dependency
* Dependency report
* Successful build
* Application execution
* HTML test report & (100% success)

---

## Gradle Commands Used

| Command                                        | Description                                         |
| ---------------------------------------------- | --------------------------------------------------- |
| `gradlew build`                                | Builds the project and generates the executable JAR |
| `gradlew run`                                  | Runs the Java application                           |
| `gradlew test`                                 | Executes unit tests and generates the HTML report   |
| `gradlew :app:dependencies`                    | Displays project dependencies                       |
| `java -version`                                | Displays the installed Java Runtime version         |
| `javac -version`                               | Displays the installed Java Compiler version        |
| `java -jar app/build/libs/<jar-file-name>.jar` | Runs the generated executable JAR                   |

---

## Outcome

This project successfully demonstrates the use of Gradle for Java application development, including dependency management, build automation, testing, report generation, and executable JAR creation. All project verification tasks were completed successfully, and supporting screenshots have been included for reference.
