# 🛠️ Java Maven CI/CD Project with Jenkins  
### **Learning Objectives🚀**  
- **Set up a structured Maven project** with dependencies & build tools.  
- **Use Git for version control** to track changes & trigger builds.  
- **Automate builds in Jenkins** with webhooks & CI/CD pipelines.  
- **Run unit tests with JUnit** to validate application functionality.  
![](https://github.com/gaurav3972/maven-project/blob/master/Images/1.0.png)
### **Prerequisites** 🔧  
- **Basic Linux commands** for navigating and managing files.  
- **Understanding of Git** for version control and repository management.  
- **Familiarity with Maven** for dependency management and build automation.  
- **Jenkins setup** with Maven and JDK installed. 
Here are some **Learning Objectives** you can include for your Maven + Jenkins CI/CD project:

---

## 📁 Project Structure

```bash
mavenapp/
├── pom.xml
└── src/
    ├── main/
    │   └── com/fortune/myapp/App.java
    └── test/
        └── com/fortune/myapp/AppTest.java
```

---

## 🚀 How It Works

1. **Write Code**
   Simple Java app with a message and JUnit test.

2. **Configure `pom.xml`**
   Includes plugins for build, compiler, and enforcer.

3. **Set Up Jenkins Freestyle Job**

   * Source: GitHub
   * Trigger: Webhook
   * Build: Maven Goal `clean install`

4. **Push Code to GitHub**
   Automatically triggers Jenkins to:

   * Clone repo
   * Build `.jar`
   * Run unit tests

5. **View `.jar` in Workspace**
   Artifact is generated after successful build.

---

## 🧪 Sample Output

```bash
Hello World!
Tests passed: 2
```

---

## 🧰 Jenkins Configuration Summary

* **Tool Setup**: JDK 17, Maven 3+
* **Project Type**: Freestyle
* **SCM**: Git (GitHub repo)
* **Build Trigger**: GitHub Webhook
* **Build Step**: `clean install`

---

## 🌐 Webhook Setup (GitHub)

1. Go to your GitHub repo → Settings → Webhooks
2. Add your Jenkins URL:
   `http://<jenkins-server>:8080/github-webhook/`
3. Content type: `application/json`

---
Here’s a **detailed step-by-step guide** to building a full **Java Maven application CI/CD pipeline using Jenkins**, starting from scratch:

---

## ✅ STEP 1: Project Structure

Open your **Jenkins server terminal** and create the Maven project:

```bash
mkdir mavenapp
cd mavenapp
mkdir -p src/main/com/fortune/myapp src/test/com/fortune/myapp
```

Check structure using:

```bash
sudo apt install tree  # If not installed
tree
```

---

## ✅ STEP 2: Add Source Code Files

Use sample Maven Java project from GitHub:

**🔗 GitHub Source**:
[https://github.com/jenkins-docs/simple-java-maven-app](https://github.com/gaurav3972/Java-Maven-CI-CD-Project-with-Jenkins.git)

### 1. `pom.xml`

Download and edit `pom.xml` for project name and Java version:

```bash
nano pom.xml
```

Make sure to:

* Use `groupId`: `com.fortune`
* Set Java version: `17`
* Add JUnit 5 dependency

### 2. `App.java`

```bash
nano src/main/com/fortune/myapp/App.java
```

```java
package com.fortune.myapp;

public class App {
    private static final String MESSAGE = "Hello World!";
    public static void main(String[] args) {
        System.out.println(MESSAGE);
    }
    public String getMessage() {
        return MESSAGE;
    }
}
```

### 3. `AppTest.java`

```bash
nano src/test/com/fortune/myapp/AppTest.java
```

```java
package com.fortune.myapp;

import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class AppTest {
    @Test
    public void testAppMessage() {
        App app = new App();
        assertEquals("Hello World!", app.getMessage());
    }
}
```

---

## ✅ STEP 3: Git Setup

Initialize local Git repo and push code:

```bash
git init
git config --global user.name "yourname"
git config --global user.email "you@example.com"
git remote add origin https://github.com/<your-username>/maven-project.git
git add .
git commit -m "initial commit"
git push origin master
```

---

## ✅ STEP 4: Jenkins Setup

### 1. Install JDK and Maven in Jenkins:

Go to:

```
Dashboard → Manage Jenkins → Global Tool Configuration
```

* **Add JDK**
  Name: `jdk17` → Install automatically

* **Add Maven**
  Name: `maven3` → Install automatically

---

## ✅ STEP 5: Create Jenkins Job

1. **Dashboard → New Item → Freestyle project**
   Name: `mavenapp-build`

2. **Source Code Management → Git**

   * Repo URL: `https://github.com/<your-username>/maven-project.git`

3. **Build Trigger**

   * Check: `GitHub hook trigger for GITScm polling`

4. **Build Environment**

   * Leave as default

5. **Build Step**

   * Add → `Invoke top-level Maven targets`
   * Goals: `clean install`

6. **Save Job**

---

## ✅ STEP 6: GitHub Webhook Setup

1. Go to your GitHub repo → Settings → Webhooks
2. Add webhook:

   * Payload URL: `http://<your-jenkins-ip>:8080/github-webhook/`
   * Content type: `application/json`

---

## ✅ STEP 7: Build & Test

Push a code update:

```bash
git add .
git commit -m "trigger build"
git push
```

This will trigger Jenkins automatically:

* Clone project
* Compile using Maven
* Run JUnit test
* Generate `.jar` file

You can find the `.jar` in the workspace under:

```
/var/lib/jenkins/workspace/mavenapp-build/target/
```

---
## ✅ Final Validation:
1. ✅ **Code Structure** is correct (`src/main`, `src/test`, `pom.xml`, `App.java`, `AppTest.java`).
2. ✅ **GitHub Repo** is public and has latest committed code.
3. ✅ **Jenkins Setup** has JDK & Maven installed, and webhook configured.
4. ✅ **Freestyle Job** runs on code push, builds with `clean install`.
5. ✅ **Build Succeeds**, JAR file generated, tests pass.
## 📦 Tech Stack

| Tool         | Purpose                            |
| ------------ | ---------------------------------- |
| Java 17      | Core programming language          |
| Maven        | Project build & dependency manager |
| Jenkins      | CI/CD automation                   |
| Git & GitHub | Source control & remote repo       |
| JUnit        | Testing framework                  |
### 📌 Maven Project – Jenkins CI/CD Pipeline: Project Summary

This project demonstrates a **simple Java-based Maven application** integrated with **Jenkins** for CI/CD automation. The application uses **JUnit** for unit testing, and Jenkins is configured to **automatically trigger builds** via GitHub webhook. The project covers:

* Java source and test structure
* Maven project setup with `pom.xml`
* GitHub version control
* Jenkins Freestyle job setup
* Automatic build, test, and JAR file generation
 ### 🔑 Key Features:

* Maven-based Java project with JUnit tests
* Jenkins CI/CD setup with GitHub integration
* Auto build on code push using Webhook
* Generates executable `.jar` file
* Simple, modular, and ready for deployment
