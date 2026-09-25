# CodeAlpha - Jenkins CI with Gradle

A Java application built and managed with **Gradle**, integrated with **Jenkins** for continuous integration as part of the **CodeAlpha DevOps Internship**.

The project demonstrates automated GitHub-triggered Jenkins builds, Gradle compilation, automated testing, and webhook exposure using **ngrok**.

---

## Objectives

* Automate Java builds using Gradle.
* Run automated tests through Jenkins.
* Trigger Jenkins automatically after a GitHub push.
* Demonstrate GitHub Webhook integration.
* Expose the local Jenkins server to GitHub using ngrok.
* Verify successful CI builds and tests.

---

## Technologies Used

* Java 19
* Gradle
* Jenkins
* Docker
* Git & GitHub
* ngrok
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
├── gradlew
├── gradlew.bat
├── settings.gradle
├── Jenkinsfile
└── README.md
```

---

## Jenkins Pipeline

The Jenkins pipeline is defined in the `Jenkinsfile` and performs the following stages:

```text
GitHub Push
     ↓
GitHub Webhook
     ↓
ngrok
     ↓
Jenkins
     ↓
Gradle Assemble
     ↓
Gradle Test
     ↓
Build Success
```

### Gradle commands executed by Jenkins

```bash
./gradlew assemble
./gradlew test
```

Both stages completed successfully during the final CI test.

---

## GitHub Webhook and ngrok

Jenkins runs locally inside Docker and is accessible on:

```text
http://localhost:8080
```

GitHub cannot directly access this local address. **ngrok** creates a secure public HTTPS tunnel to the local Jenkins server.

```text
GitHub
   │
   │ HTTPS
   ▼
https://cancel-filler-whoopee.ngrok-free.dev
   │
   │ ngrok tunnel
   ▼
http://localhost:8080
   │
   ▼
Jenkins
```

The GitHub Webhook payload URL is:

```text
https://cancel-filler-whoopee.ngrok-free.dev/github-webhook/
```

ngrok maps the public URL to:

```text
http://localhost:8080
```

When a push is made to the repository, GitHub sends a `POST` request to:

```text
/github-webhook/
```

Jenkins receives the webhook and automatically starts the pipeline.

The ngrok inspection interface can be used locally to verify incoming requests:

```text
http://127.0.0.1:4040
```

A successful webhook request appears as:

```text
POST /github-webhook/    200 OK
```

---

## Jenkins Verification

The final automated pipeline successfully demonstrated:

```text
Started by GitHub push
        ↓
Checkout from GitHub
        ↓
./gradlew assemble
        ↓
BUILD SUCCESSFUL
        ↓
./gradlew test
        ↓
BUILD SUCCESSFUL
        ↓
Finished: SUCCESS
```

The Jenkins workspace uses:

```text
/var/jenkins_home/workspace/CodeAlpha-Jenkins-Project
```

and the Gradle project is executed from:

```text
CodeAlpha_JavaApplication_UsingGradle
```

---

## Useful Commands

| Command                       | Purpose                             |
| ----------------------------- | ----------------------------------- |
| `./gradlew assemble`          | Builds the application              |
| `./gradlew test`              | Runs automated tests                |
| `./gradlew build`             | Builds and tests the project        |
| `./gradlew run`               | Runs the Java application           |
| `./gradlew :app:dependencies` | Displays Gradle dependencies        |
| `java -version`               | Verifies Java version               |
| `ngrok http 8080`             | Exposes local Jenkins through ngrok |

---

## Outcome

The project successfully demonstrates a basic **Continuous Integration workflow** using GitHub, Jenkins, Docker, Gradle, and ngrok.

A GitHub push automatically triggers Jenkins, which checks out the latest code, runs the Gradle build, executes the tests, and reports the final build status.
