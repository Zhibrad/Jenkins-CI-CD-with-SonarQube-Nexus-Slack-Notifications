# 🚀 Jenkins CI/CD with SonarQube, Nexus & Slack Notifications

### Automated Build • Code Quality Analysis • Quality Gate • Artifact Management • Team Notifications

![AWS](https://img.shields.io/badge/AWS-EC2-orange?logo=amazonaws)
![Jenkins](https://img.shields.io/badge/Jenkins-CI%2FCD-red?logo=jenkins)
![SonarQube](https://img.shields.io/badge/SonarQube-Code%20Quality-blue?logo=sonarqube)
![Nexus](https://img.shields.io/badge/Nexus-Repository%20Manager-3C3C3C)
![Maven](https://img.shields.io/badge/Maven-3.9.9-C71A36?logo=apachemaven)
![Slack](https://img.shields.io/badge/Slack-Notifications-4A154B?logo=slack)
![GitHub](https://img.shields.io/badge/GitHub-Source%20Control-181717?logo=github)
![DevOps](https://img.shields.io/badge/Domain-DevOps-purple)

> **A production-oriented Jenkins CI/CD project integrating GitHub, Maven, SonarQube, SonarQube Quality Gates, Nexus Repository and Slack to automate software build, code-quality validation, artifact management and delivery notifications.**

---
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/46f528c3-b5c0-431b-bf28-fd62b21c57aa" />

# 📌 Project Overview

This project extends a foundational Jenkins environment into a more complete CI/CD workflow.

The objective is to ensure that code is not simply built successfully, but also:

- retrieved from source control,
- compiled,
- tested,
- inspected for code-quality issues,
- evaluated against a quality gate,
- packaged,
- uploaded to a centralized artifact repository,
- and communicated to the development team through Slack.

The final workflow is:

```text
GitHub
   ↓
Jenkins
   ↓
Maven Build
   ↓
Unit Test
   ↓
SonarQube Analysis
   ↓
Quality Gate
   ↓
Nexus Repository
   ↓
Slack Notification
```

This transforms Jenkins from a simple build server into a **quality-aware CI/CD orchestration platform**.

---

# 🎯 Project Objectives

The project was designed to demonstrate:

- Jenkins CI/CD pipeline construction.
- GitHub source-code integration.
- Maven build automation.
- Automated unit testing.
- SonarQube static code analysis.
- SonarQube quality-gate enforcement.
- Nexus Repository artifact management.
- Jenkins-to-Nexus authentication.
- Slack build notifications.
- AWS EC2 infrastructure.
- Linux administration.
- Security Group configuration.
- Credentials management.
- Pipeline-as-Code.

---

# 💼 Business Scenario

A development team is delivering a Java-based application.

A basic CI workflow may only verify:

```text
Developer
   ↓
GitHub
   ↓
Jenkins
   ↓
Maven Build
   ↓
SUCCESS
```

But a successful compilation does not necessarily mean that the software is ready to progress.

A production-oriented workflow should also answer:

> Is the code maintainable?

> Did the automated tests pass?

> Did the code-quality analysis meet the organization's standards?

> Was the build artifact stored centrally?

> Did the development team receive the result?

This project addresses those questions with:

```text
GitHub
   ↓
Build
   ↓
Test
   ↓
Analyze
   ↓
Quality Gate
   ↓
Publish
   ↓
Notify
```

---

# 🏗️ Solution Architecture

```text
                         DEVELOPER
                             |
                             v
                          GitHub
                             |
                             v
                   +-------------------+
                   | Jenkins Controller|
                   +---------+---------+
                             |
                             v
                        Maven Build
                             |
                             v
                        Unit Tests
                             |
                             v
                    SonarQube Analysis
                             |
                             v
                       Quality Gate
                      /            \
                   PASS             FAIL
                    |                |
                    v                v
               Nexus Upload      Stop Pipeline
                    |
                    v
             Slack Notification
```

---

# 🌐 AWS Architecture

```text
                              AWS
                               |
       +-----------------------+-----------------------+
       |                       |                       |
       v                       v                       v
+-------------+        +---------------+       +-------------+
| Jenkins EC2 |        | SonarQube EC2 |       |  Nexus EC2 |
|             |        |               |       |             |
| Jenkins     |        | SonarQube     |       | Nexus       |
| Maven       |        | Code Analysis |       | Repository  |
+------+------+        +-------+-------+       +------+------+
       |                       ^                       ^
       |                       |                       |
       +---------- HTTP -------+---------- HTTP -------+
       |
       v
     Slack
```

---

# 🔄 End-to-End Pipeline

```text
             FETCH
               |
               v
           GitHub / Git
               |
               v
            BUILD
               |
               v
           Maven
               |
               v
          UNIT TEST
               |
               v
         SonarQube Scan
               |
               v
        QUALITY GATE
          /       \
       PASS       FAIL
        |           |
        v           v
      Nexus       STOP
     Upload      Pipeline
        |
        v
      Slack
   Notification
```

---

# 🧩 Core Components

| Component | Purpose |
|---|---|
| Jenkins | Pipeline orchestration |
| GitHub | Source repository |
| Maven | Build and test automation |
| SonarQube | Code-quality analysis |
| Quality Gate | Controls whether pipeline can proceed |
| Nexus | Central artifact repository |
| Slack | Build and deployment notifications |
| AWS EC2 | Hosts Jenkins, Nexus and SonarQube |
| Security Groups | Network access control |

---

# 🛠️ Technology Stack

### Cloud

- AWS EC2
- AWS Security Groups
- VPC private networking
- EC2 Key Pairs

### CI/CD

- Jenkins
- Jenkins Pipeline
- Jenkins Credentials

### Code Quality

- SonarQube
- SonarQube Scanner
- Quality Gates

### Build

- Java
- Maven
- JUnit
- Checkstyle

### Artifact Management

- Sonatype Nexus Repository
- Maven Hosted Repository

### Collaboration

- Slack

### Source Control

- Git
- GitHub

---

# 📚 Table of Contents

1. [Project Overview](#-project-overview)
2. [Project Objectives](#-project-objectives)
3. [Business Scenario](#-business-scenario)
4. [Solution Architecture](#-solution-architecture)
5. [AWS Architecture](#-aws-architecture)
6. [Core Components](#-core-components)
7. [Technology Stack](#-technology-stack)
8. [Construction Rules](#-construction-rules)
9. [Pipeline Execution Flow](#-pipeline-execution-flow)
10. [Implementation Prerequisites](#-implementation-prerequisites)
11. [Phase 1 — Nexus Server](#phase-1--nexus-server)
12. [Phase 2 — SonarQube Server](#phase-2--sonarqube-server)
13. [Phase 3 — Security Group Configuration](#phase-3--security-group-configuration)
14. [Phase 4 — Jenkins Plugin Installation](#phase-4--jenkins-plugin-installation)
15. [Phase 5 — SonarQube Integration](#phase-5--sonarqube-integration)
16. [Phase 6 — SonarQube Token](#phase-6--sonarqube-token)
17. [Phase 7 — Pipeline Quality Gate](#phase-7--pipeline-quality-gate)
18. [Phase 8 — SonarQube Webhook](#phase-8--sonarqube-webhook)
19. [Phase 9 — Nexus Repository](#phase-9--nexus-repository)
20. [Phase 10 — Jenkins Nexus Credentials](#phase-10--jenkins-nexus-credentials)
21. [Phase 11 — Slack Integration](#phase-11--slack-integration)
22. [Phase 12 — Jenkins Pipeline](#phase-12--jenkins-pipeline)
23. [Complete Pipeline](#-complete-pipeline)
24. [Quality Gate Behavior](#-quality-gate-behavior)
25. [Security Architecture](#-security-architecture)
26. [Verification Checklist](#-verification-checklist)
27. [Troubleshooting](#-troubleshooting)
28. [Cost Considerations](#-cost-considerations)
29. [Production Improvements](#-production-improvements)
30. [Skills Demonstrated](#-skills-demonstrated)
31. [Lessons Learned](#-lessons-learned)
32. [Future CI/CD Evolution](#-future-cicd-evolution)
33. [Project Structure](#-project-structure)
34. [Official Documentation](#-official-documentation)
35. [Project Author](#-project-author)

---

# 📐 Construction Rules

## Rule 1 — Every Build Must Be Traceable

Every pipeline execution should identify:

```text
Git Commit
   ↓
Jenkins Build
   ↓
SonarQube Analysis
   ↓
Artifact Version
   ↓
Nexus Repository
```

---

## Rule 2 — Build Must Precede Analysis

The pipeline follows:

```text
Checkout
   ↓
Build
   ↓
Test
   ↓
Analysis
```

This ensures that the code-quality stage operates against the application being built.

---

## Rule 3 — Quality Gate Controls Promotion

The pipeline should not automatically publish an artifact when the required SonarQube quality gate fails.

```text
SonarQube
     |
     v
Quality Gate
   /      \
 PASS      FAIL
  |          |
  v          v
Nexus      STOP
```

Jenkins' SonarQube integration provides `waitForQualityGate`, which can pause the pipeline and optionally abort it when the quality gate is not green. :contentReference[oaicite:1]{index=1}

---

## Rule 4 — Credentials Must Never Be Hardcoded

Do not place:

```text
Nexus password
SonarQube token
Slack token
AWS credentials
```

inside the Jenkinsfile.

Use:

```text
Jenkins Credentials
```

and reference credential IDs.

---

## Rule 5 — Use Private IPs for Internal Services

Where Jenkins, Nexus and SonarQube share the same AWS VPC, prefer:

```text
Jenkins
  |
  +---- private IP ---> SonarQube
  |
  +---- private IP ---> Nexus
```

rather than exposing administrative services unnecessarily over the public Internet.

---

## Rule 6 — Restrict Security Groups

Only required traffic should be permitted.

Example:

```text
Jenkins → SonarQube : TCP 80
Jenkins → Nexus     : TCP 8081
Jenkins             : TCP 8080
Admin               : TCP 22
```

Sources should preferably be restricted by Security Group or trusted IP rather than opening everything to the world.

---

# 🔄 Pipeline Execution Flow

```text
1. Fetch Source Code
        ↓
2. Maven Build
        ↓
3. Unit Tests
        ↓
4. SonarQube Analysis
        ↓
5. Quality Gate
        ↓
6. Upload WAR to Nexus
        ↓
7. Notify Slack
```

---

# 🚦 Implementation Prerequisites

Before beginning, ensure you have:

- AWS account
- Jenkins server
- GitHub repository
- Java/Maven project
- Maven configured in Jenkins
- Jenkins credentials access
- AWS key pairs
- AWS Security Groups
- Nexus server
- SonarQube server
- Slack workspace

---

# PHASE 1 — Nexus Server

## 1. Create the Nexus EC2 Instance

Create an EC2 instance for Nexus.

Example:

```text
AMI:
Amazon Linux

Instance Type:
t3.small / t3.medium

Storage:
EBS

Public IPv4:
Enabled for initial setup
```

For a production deployment, consider private networking, DNS and HTTPS.

---
<img width="1380" height="825" alt="Screenshot 2026-09-17 155332" src="https://github.com/user-attachments/assets/dbffbadf-ff60-44eb-b93c-ec882603aef0" />

## 2. Create Key Pair

Create:

```text
nexus-key
```

Download the private key and protect it.

---

## 3. Configure Nexus Security Group

Allow:

### SSH

```text
TCP 22
Source: My IP
```

### Nexus Web Interface

```text
TCP 8081
Source: My IP
```

### Jenkins → Nexus

```text
TCP 8081
Source: Jenkins Security Group
```

The architecture becomes:

```text
Administrator
     |
     | TCP 8081
     v
 Nexus

Jenkins
     |
     | TCP 8081
     v
 Nexus
```

---
<img width="1339" height="475" alt="Screenshot 2026-09-17 155634" src="https://github.com/user-attachments/assets/55205ff0-ced6-4173-8cf2-04ef6520debd" />

# 4. Install Nexus Using User Data

If your implementation uses a GitHub repository containing the tested Nexus user-data script:

```text
AWS Console
   ↓
Advanced Details
   ↓
User Data
   ↓
Paste Nexus installation script
```

Then launch the EC2 instance.

> Keep the user-data script in your project documentation or infrastructure repository rather than hiding the deployment process.

---
<img width="1286" height="786" alt="Screenshot 2026-09-17 155755" src="https://github.com/user-attachments/assets/31a0a313-56ba-48f9-afde-6cdab52de7ff" />

# 5. Validate Nexus

SSH into the Nexus server:

```bash
ssh -i "nexus-key.pem" ec2-user@<NEXUS-PUBLIC-IP>
```

Check the service:

```bash
sudo systemctl status nexus
```

Inspect the installation directory:

```bash
ls /opt/nexus/
```

Verify Java:

```bash
java -version
```

---
<img width="1125" height="417" alt="Screenshot 2026-09-17 160139" src="https://github.com/user-attachments/assets/39ce624f-3c97-48ed-8812-15b914578343" />

# 6. Open Nexus

Browse:

```text
http://<NEXUS-PUBLIC-IP>:8081
```

Select:

```text
Sign In
```

For the initial administrator password, use the path reported by your installed Nexus deployment.

A common Nexus installation stores the initial password under the Nexus data directory, for example:

```text
sonatype-work/nexus3/admin.password
```
<img width="1919" height="776" alt="Screenshot 2026-09-17 160219" src="https://github.com/user-attachments/assets/5289e840-221d-4f70-b681-47c2304cd5fe" />

Retrieve it from the server according to the version and installation path:

```bash
sudo cat /opt/sonatype-work/nexus3/admin.password
```

If your user-data installation places the data directory elsewhere, use that exact path.

Login:

```text
Username:
admin

Password:
<INITIAL PASSWORD>
```

Nexus will then prompt you to establish a new administrator password.

---
<img width="1407" height="786" alt="Screenshot 2026-09-17 160551" src="https://github.com/user-attachments/assets/633133d9-48c0-4c0b-a515-14e4dba7ffde" />
<img width="1886" height="903" alt="Screenshot 2026-09-17 160640" src="https://github.com/user-attachments/assets/3cc2cdca-7f65-44ef-9545-c3a003520e21" />

# PHASE 2 — SonarQube Server

# 7. Create the SonarQube EC2 Instance

Create another EC2 instance.

Recommended starting environment:

```text
AMI:
Ubuntu 24.04 LTS

Instance Type:
t3.medium or larger depending on workload

Storage:
Dedicated EBS volume recommended

Key Pair:
sonarqube-key
```

SonarQube resource requirements should be checked against the specific server edition/version being deployed.

---
<img width="1312" height="835" alt="Screenshot 2026-09-17 160938" src="https://github.com/user-attachments/assets/40428254-d8d1-4909-a758-91c5b0048ac5" />

# 8. Create SonarQube Security Group

Allow:

### SSH

```text
TCP 22
Source:
My IP
```

### SonarQube

```text
TCP 80
Source:
My IP
```

### Jenkins → SonarQube

```text
TCP 80
Source:
Jenkins Security Group
```

Architecture:

```text
Jenkins
   |
   | TCP 80
   v
SonarQube
```

---
<img width="1749" height="552" alt="Screenshot 2026-09-17 161057" src="https://github.com/user-attachments/assets/bb8bd62c-261d-4f29-bee9-af95497e9ff1" />

# 9. Install Using User Data

If your repository contains your tested SonarQube user-data deployment script:

```text
EC2
  ↓
Advanced Details
  ↓
User Data
  ↓
Paste SonarQube installation script
```

Launch the instance.

---
<img width="1183" height="852" alt="Screenshot 2026-09-17 161202" src="https://github.com/user-attachments/assets/d3c96abb-1f1b-4716-8e10-dbbcffbfa0fb" />
<img width="1310" height="879" alt="Screenshot 2026-09-17 161306" src="https://github.com/user-attachments/assets/aba9d6dc-d501-459f-982d-dff1cd9ab5a6" />
<img width="866" height="255" alt="Screenshot 2026-09-17 161354" src="https://github.com/user-attachments/assets/5f3caa11-c869-421a-a575-265b4105a8dc" />

# 10. Validate SonarQube

Browse:

```text
http://<SONARQUBE-PUBLIC-IP>
```

or, if your reverse proxy listens on port 80:

```text
http://<SONARQUBE-PUBLIC-IP>:80
```

Initial login:

```text
Username:
admin

Password:
admin
```

You should immediately change the default password.

---
<img width="1919" height="942" alt="Screenshot 2026-09-17 161450" src="https://github.com/user-attachments/assets/cfd8a500-b0bc-4c6f-8445-9b2e732f7560" />

# PHASE 3 — Security Group Configuration

At this stage we have:

```text
               AWS VPC
                  |
      +-----------+-----------+
      |           |           |
      v           v           v
   Jenkins     SonarQube    Nexus
    :8080        :80         :8081
```

Configure traffic carefully.

### Jenkins Security Group

Allow required inbound traffic:

```text
TCP 8080
Source: Administrator IP
```

For the SonarQube webhook:

```text
TCP 8080
Source: SonarQube Security Group
```

### SonarQube Security Group

```text
TCP 80
Source: Jenkins Security Group
```

### Nexus Security Group

```text
TCP 8081
Source: Jenkins Security Group
```

---

# PHASE 4 — Jenkins Plugin Installation

Go to:

```text
Manage Jenkins
    ↓
Plugins
```

Install the plugins required by this implementation.

Recommended categories:

```text
SonarQube Scanner
Pipeline support
Maven Integration
Nexus artifact upload
Slack Notification
Build Timestamp
```

Jenkins provides an official SonarQube Scanner plugin for integrating SonarQube analysis into Jenkins Pipelines. :contentReference[oaicite:2]{index=2}

The Nexus Artifact Uploader plugin also provides the `nexusArtifactUploader` Pipeline step. :contentReference[oaicite:3]{index=3}

> **Production note:** the current Nexus Artifact Uploader plugin is available but is marked "up for adoption"; evaluate the supported Sonatype Nexus Platform Plugin or direct repository/API-based publishing when designing a long-lived production platform. :contentReference[oaicite:4]{index=4}

The Slack Notification plugin provides `slackSend` Pipeline integration. :contentReference[oaicite:5]{index=5}

---
<img width="1906" height="432" alt="Screenshot 2026-09-17 161747" src="https://github.com/user-attachments/assets/bee08b6a-a7f6-4642-afa0-834303f8f660" />
<img width="1496" height="745" alt="Screenshot 2026-09-17 162056" src="https://github.com/user-attachments/assets/3807f585-13d5-409e-8bae-d83f38541008" />

# PHASE 5 — SonarQube Integration

## 11. Configure SonarQube Scanner

Go to:

```text
Manage Jenkins
   ↓
Tools
```

Find:

```text
SonarQube Scanner installations
```

Create:

```text
Name:
Sonar8.0
```

Choose a SonarQube Scanner version compatible with your Jenkins/SonarQube environment.

If your lab specifically uses:

```text
8.0.1.6346
```

you can retain that configuration, but verify compatibility rather than treating the version as a universal production requirement.

---
<img width="1703" height="520" alt="Screenshot 2026-09-17 163251" src="https://github.com/user-attachments/assets/e06a53d8-07fc-4f0b-b272-06a266ecf733" />

# 12. Configure SonarQube Server

Go to:

```text
Manage Jenkins
   ↓
System
```

Find:

```text
SonarQube servers
```

Enable:

```text
Environment variables
```

Create:

```text
Name:
Sonar server
```

Use the internal SonarQube URL:

```text
http://<SONARQUBE-PRIVATE-IP>:80
```

Example:

```text
http://10.0.2.20:80
```

where the actual IP is your SonarQube server's private VPC address.

---
<img width="1615" height="457" alt="Screenshot 2026-09-17 163814" src="https://github.com/user-attachments/assets/63ed8c10-888d-48a5-a074-827a859934e6" />

# PHASE 6 — SonarQube Token

## 13. Generate a SonarQube Token

Open SonarQube.

Navigate to:

```text
My Account
   ↓
Security
```

Create a token:

```text
Name:
Jenkins
```

Set an appropriate expiration period for your security policy.

Generate the token.

Copy it immediately.

> Treat the token like a password. Do not place it directly inside a Jenkinsfile.

---
<img width="1586" height="706" alt="Screenshot 2026-09-17 163905" src="https://github.com/user-attachments/assets/2814f040-85fc-4f3f-bdd1-cd2b5fc10c34" />

# 14. Add the Token to Jenkins

In Jenkins:

```text
Manage Jenkins
   ↓
Credentials
   ↓
System
   ↓
Global credentials
   ↓
Add Credentials
```

Create an appropriate secret credential.

For example:

```text
Kind:
Secret text

ID:
sonar-token

Description:
SonarQube Jenkins token
```

Paste the SonarQube token into the secret field.

Save.

---
<img width="586" height="496" alt="Screenshot 2026-09-17 164149" src="https://github.com/user-attachments/assets/65f39ca9-4cc2-4402-b959-233c6b4d73eb" />

# 15. Verify Network Access

From the Jenkins server, test that SonarQube is reachable.

Example:

```bash
curl -I http://<SONARQUBE-PRIVATE-IP>:80
```

The Security Group must permit:

```text
Jenkins SG
       |
       | TCP 80
       v
SonarQube SG
```

---

# PHASE 7 — Pipeline Quality Gate

The purpose of the quality gate is to prevent bad code from progressing automatically.

Example policy:

```text
SonarQube Analysis
       |
       v
Quality Gate
   /        \
 PASS       FAIL
  |           |
  v           v
 Nexus       STOP
```

Jenkins' SonarQube integration provides the `waitForQualityGate` step for this purpose. :contentReference[oaicite:6]{index=6}

---

# 16. Create SonarQube Quality Gate

Open:

```text
SonarQube
   ↓
Quality Gates
```

Create:

```text
Vprofile Quality Gate
```

For your lab implementation, you can define an issue-based threshold such as:

```text
Issues > 3
```

according to your chosen comparison condition.

A better production policy would normally include multiple quality dimensions, such as:

- Reliability
- Security
- Maintainability
- Coverage
- Duplications
- New-code issues

The important principle is that the gate should reflect an explicit engineering quality policy.

---
<img width="1471" height="849" alt="Screenshot 2026-09-17 164630" src="https://github.com/user-attachments/assets/03a56fbe-6b6a-479f-8876-a8d92e15b946" />

# PHASE 8 — SonarQube Webhook

This is critical.

Go to:

```text
SonarQube
   ↓
Project
   ↓
Project Settings
   ↓
Webhooks
```

Create a webhook.

The Jenkins endpoint should be:

```text
http://<JENKINS-URL>/sonarqube-webhook/
```

The trailing slash is important for the Jenkins integration. :contentReference[oaicite:7]{index=7}

For example:

```text
http://jenkins.example.com/sonarqube-webhook/
```

or for your lab:

```text
http://<JENKINS-IP>:8080/sonarqube-webhook/
```

Then ensure the Jenkins Security Group accepts the webhook traffic:

```text
SonarQube SG
       |
       | TCP 8080
       v
Jenkins
```

This allows:

```text
SonarQube
   |
   | Webhook
   v
Jenkins
   |
   v
waitForQualityGate()
```

---
<img width="549" height="580" alt="Screenshot 2026-09-21 123935" src="https://github.com/user-attachments/assets/7d616513-2f90-4894-9f41-49c7ba3ade71" />

# PHASE 9 — Nexus Repository

## 17. Open Nexus

Browse:

```text
http://<NEXUS-PUBLIC-IP>:8081
```

Login:

```text
admin
```

using the credentials created during Nexus initialization.

---
<img width="1725" height="877" alt="Screenshot 2026-09-17 174547" src="https://github.com/user-attachments/assets/57e1dd5b-9970-40c1-94fb-524cb2d94346" />

# 18. Create Maven Hosted Repository

Navigate to:

```text
Settings
   ↓
Repositories
   ↓
Create Repository
```

Select:

```text
Maven 2 (hosted)
```

Give the repository a meaningful name.

Example:

```text
vprofile-releases
```

Save.

A Nexus Maven hosted repository is designed to store internally produced Maven artifacts. Sonatype documents Maven hosted repositories as the authoritative repository location for internally hosted components. :contentReference[oaicite:8]{index=8}

---

# PHASE 10 — Jenkins Nexus Credentials

## 19. Create Nexus Credential

In Jenkins:

```text
Manage Jenkins
   ↓
Credentials
   ↓
System
   ↓
Global credentials
   ↓
Add Credentials
```

Create:

```text
Kind:
Username with password
```

Example:

```text
ID:
nexus-login

Username:
admin / deployment-user

Password:
<SECURE PASSWORD>
```

### Production Recommendation

Do not use the Nexus `admin` account for application publishing.

Create a dedicated least-privilege deployment account.

For example:

```text
jenkins-nexus-publisher
```

with only the permissions required to upload artifacts.

---
<img width="604" height="691" alt="Screenshot 2026-09-17 175021" src="https://github.com/user-attachments/assets/a395713e-927a-4b13-b00a-4b8d655d6e26" />

# 20. Verify Nexus Configuration

Before building, verify that:

```text
Repository name
        =
Jenkins pipeline repository value
```

Also verify:

```text
Credential ID
        =
Jenkins credential ID
```

And:

```text
Artifact file
        =
Actual file generated by Maven
```

Example:

```text
target/vprofile-v2.war
```

---

# ⏱️ Build Timestamp

To make build records easier to trace, configure the Jenkins timestamp pattern:

```text
yy-MM-dd_HH-mm
```

This creates readable timestamps such as:

```text
26-09-15_14-35
```

---
<img width="1645" height="406" alt="Screenshot 2026-09-17 175334" src="https://github.com/user-attachments/assets/6d23645e-32ec-4cbc-8123-0bee4f27688b" />

# PHASE 11 — Slack Integration

## 21. Install Slack Notification Plugin

Go to:

```text
Manage Jenkins
   ↓
Plugins
```

Search:

```text
Slack Notification
```

Install it.

Jenkins' official Slack plugin documentation provides the current setup flow and recommends using Jenkins Secret Text credentials for the bot token. :contentReference[oaicite:9]{index=9}

---
<img width="1546" height="291" alt="image" src="https://github.com/user-attachments/assets/33b78b34-e52b-4ca5-8348-fee1001fccec" />

# 22. Create Slack App

In Slack:

```text
Slack
   ↓
API / Apps
   ↓
Create New App
```

Create a Jenkins notification app.

The current Jenkins Slack plugin documentation recommends creating a bot-user Slack app, installing it into the workspace, copying its Bot User OAuth Token, and storing that token as a Jenkins Secret Text credential. :contentReference[oaicite:10]{index=10}

---
<img width="1598" height="984" alt="image" src="https://github.com/user-attachments/assets/4103bbb6-44c1-4632-80fe-231f2cd211ac" />
<img width="1868" height="915" alt="image" src="https://github.com/user-attachments/assets/d4ba5d27-34c9-4a63-b2ea-1046cd0e6a57" />


# 23. Install the Slack App

Install the Slack app into your workspace.

Copy the:

```text
Bot User OAuth Token
```

Do not publish it.

Do not put it in your Jenkinsfile.

---
<img width="1790" height="911" alt="image" src="https://github.com/user-attachments/assets/7d032744-26d6-4b97-9f9c-2369415233c2" />
<img width="1052" height="648" alt="image" src="https://github.com/user-attachments/assets/ee604a26-7721-44d1-8d6c-aedc50814d0b" />

# 24. Add Slack Token to Jenkins

Go to:

```text
Manage Jenkins
   ↓
Credentials
   ↓
Global
   ↓
Add Credentials
```

Select:

```text
Kind:
Secret text
```
<img width="581" height="446" alt="image" src="https://github.com/user-attachments/assets/61220b96-d5b6-4ea8-94d2-2e8f2848957a" />

Example:

```text
ID:
slack-token

Description:
Jenkins Slack bot token
```
<img width="727" height="613" alt="image" src="https://github.com/user-attachments/assets/6c318944-af48-4a13-b625-b3afb5b962ce" />

Paste the token.

The Slack plugin supports a `tokenCredentialId` that references this Secret Text credential. :contentReference[oaicite:11]{index=11}

---

# 25. Configure Slack in Jenkins

Go to:

```text
Manage Jenkins
   ↓
System
   ↓
Slack
```

Configure:

```text
Workspace:
<your-workspace-name>

Credential:
slack-token

Channel:
#jenkins
```

Enable the bot-user/custom Slack app option if using the current bot-user setup.

Invite the Jenkins bot into the target Slack channel.

Then use:

```text
Test Connection
```

The official Slack plugin documentation recommends testing the connection after installing the app and configuring the credential. :contentReference[oaicite:12]{index=12}

---
<img width="1637" height="501" alt="image" src="https://github.com/user-attachments/assets/61d865f3-bcce-4c77-a14a-a8a5fcc7561a" />

# PHASE 12 — Jenkins Pipeline

The final pipeline can be implemented using Jenkins Declarative Pipeline.

The following example demonstrates the complete execution model.

> Replace all placeholder values such as repository URL, Nexus host, repository name, artifact coordinates and credential IDs with values from your environment.

---

# 🚀 Complete Pipeline

```groovy
def COLOR_MAP = [
    'SUCCESS': 'good',
    'FAILURE': 'danger',
]

pipeline {
    agent any

    tools {
        maven "MAVEN3.9"
        jdk "JDK17"
    }

    stages {

        stage('Fetch code') {
            steps {
                git branch: 'atom',
                    url: 'https://github.com/hkhcoder/vprofile-project.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn install -DskipTests'
            }

            post {
                success {
                    echo 'Now Archiving it...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage('UNIT TEST') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Checkstyle Analysis') {
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
        }

        stage('Sonar Code analysis') {
            environment {
                scannerHome = tool 'sonar8.0'
            }

            steps {
                withSonarQubeEnv('sonarserver') {
                    sh '''${scannerHome}/bin/sonar-scanner \
                        -Dsonar.projectKey=vprofile \
                        -Dsonar.projectName=vprofile \
                        -Dsonar.projectVersion=1.0 \
                        -Dsonar.sources=src/ \
                        -Dsonar.java.binaries=target/classes \
                        -Dsonar.junit.reportsPath=target/surefire-reports \
                        -Dsonar.coverage.jacoco.xmlReportPaths=target/site/jacoco/jacoco.xml \
                        -Dsonar.java.checkstyle.reportPaths=target/checkstyle-result.xml'''
                }
            }
        }

        stage('Quality Gate') {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }

        stage('Publish to Nexus') {
            steps {
                nexusArtifactUploader(
                    nexusVersion: 'nexus3',
                    protocol: 'http',
                    nexusUrl: '172.31.19.112:8081',
                    groupId: 'QA',
                    version: "${env.BUILD_ID}-${BUILD_TIMESTAMP}",
                    repository: 'vprofile-repo',
                    credentialsId: 'nexuslogin',
                    artifacts: [
                        [
                            artifactId: 'vproapp',
                            classifier: '',
                            file: 'target/vprofile-v2.war',
                            type: 'war'
                        ]
                    ]
                )
            }
        }
    }

    post {
        always {
            echo 'Slack Notifications.'

            slackSend(
                channel: '#all-jenkinsnotifier',
                color: COLOR_MAP[currentBuild.currentResult],
                message: "*${currentBuild.currentResult}:* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER} \n More info at: ${env.BUILD_URL}"
            )
        }
    }
}
```

The SonarQube `withSonarQubeEnv` + `waitForQualityGate` sequence follows Jenkins' documented integration pattern. :contentReference[oaicite:13]{index=13}

The `nexusArtifactUploader` syntax is provided by the Jenkins Nexus Artifact Uploader Pipeline step. :contentReference[oaicite:14]{index=14}

The `slackSend` step and `tokenCredentialId` approach are documented by the Jenkins Slack plugin. :contentReference[oaicite:15]{index=15}

---
<img width="1908" height="779" alt="image" src="https://github.com/user-attachments/assets/3c2ec9e8-4f76-4921-ad1d-056fd26eecdd" />
<img width="1913" height="875" alt="image" src="https://github.com/user-attachments/assets/ef987ee9-0660-4aa5-bcf3-02411c9db9a7" />

# 🧪 Checkstyle XML

After the Maven build, inspect:

```text
workspace/
    |
    +-- target/
          |
          +-- *.xml
```

Depending on your project and Maven configuration, Checkstyle-related reports may be produced under the `target` directory.

For example:

```text
target/checkstyle-result.xml
```

You can verify from the Jenkins agent:

```bash
find target -type f -name "*.xml"
```

---

# 🚦 Quality Gate Behavior

The most important decision point in this pipeline is:

```text
SonarQube
     |
     v
Quality Gate
     |
     +-----------+
     |           |
     v           v
   PASS        FAIL
     |           |
     v           v
  Nexus        STOP
     |
     v
  Slack
```

This is more valuable than simply running a SonarQube scan.

The pipeline is making a delivery decision based on code quality.

---
<img width="1431" height="465" alt="image" src="https://github.com/user-attachments/assets/0c7f0139-93d8-40e5-9d7b-8dcbff93c3cb" />
<img width="1585" height="392" alt="image" src="https://github.com/user-attachments/assets/a69dd89a-6bd2-45d8-b870-764e699a5cde" />

# 📤 Nexus Artifact Flow

Once the quality gate passes:

```text
Maven
  |
  v
target/vprofile-v2.war
  |
  v
Jenkins
  |
  v
Nexus Maven Hosted Repository
```

Nexus then becomes the centralized location for the artifact.

Example:

```text
Nexus
  |
  +-- vprofile-releases
          |
          +-- vprofile
              |
              +-- v1.0
                  |
                  +-- vprofile-v2.war
```

Nexus is designed to host Maven-formatted components and internally produced artifacts. :contentReference[oaicite:16]{index=16}

---
<img width="1578" height="445" alt="image" src="https://github.com/user-attachments/assets/1466e955-fe53-4f69-91c1-6195cc4ed34d" />

# 📢 Slack Notification Flow

The final notification flow is:

```text
Jenkins
   |
   +-------- SUCCESS --------+
   |                         |
   v                         v
Nexus                     Slack
Artifact                  Notification


Jenkins
   |
   +--------- FAIL ---------+
                             |
                             v
                           Slack
                         Notification
```

Example Slack message:

```text
✅ Jenkins Build Successful

Project: vprofile
Build: #42
Quality Gate: PASSED
Artifact: vprofile-v2.war
Repository: vprofile-releases

Build URL:
https://jenkins.example.com/job/vprofile/42/
```

Failure example:

```text
❌ Jenkins Build Failed

Project: vprofile
Build: #43
Reason: Quality Gate FAILED

Review:
https://jenkins.example.com/job/vprofile/43/
```

---
<img width="1913" height="875" alt="image" src="https://github.com/user-attachments/assets/3f69a5f7-2b3e-4b71-a583-e7f1ff188a98" />

# 🔐 Security Architecture

```text
                         AWS VPC
                            |
       +--------------------+--------------------+
       |                    |                    |
       v                    v                    v
   Jenkins               SonarQube             Nexus
    :8080                  :80                  :8081
       |                    ^                    ^
       |                    |                    |
       |------ Analysis ----|                    |
       |-----------------------------------------|
                            |
                            v
                          Slack
```

---

# 🔒 Security Controls

## Jenkins

Restrict:

```text
TCP 8080
```

to trusted users or a controlled reverse proxy.

---

## SonarQube

Allow:

```text
Jenkins SG → SonarQube SG :80
```

rather than opening the SonarQube server unnecessarily to the entire Internet.

---

## Nexus

Allow:

```text
Jenkins SG → Nexus SG :8081
```

rather than exposing Nexus broadly.

---

## Credentials

Use Jenkins Credentials for:

```text
SonarQube Token
Nexus Username/Password
Slack Bot Token
GitHub Credentials
```

Never place secrets in:

```text
Jenkinsfile
README.md
GitHub
Screenshots
Shell scripts
```

---

# 🔑 Credential Reference

| Credential | Jenkins Type | Example ID |
|---|---|---|
| SonarQube Token | Secret text | `sonar-token` |
| Nexus Credentials | Username/password | `nexus-login` |
| Slack Bot Token | Secret text | `slack-token` |
| GitHub SSH | SSH Username with private key | `github-ssh` |

---

# 🧪 Verification Checklist

```text
[✓] Jenkins operational

[✓] Nexus EC2 created

[✓] Nexus service running

[✓] Nexus accessible on 8081

[✓] SonarQube EC2 created

[✓] SonarQube accessible

[✓] Jenkins → SonarQube connectivity verified

[✓] Jenkins → Nexus connectivity verified

[✓] SonarQube token generated

[✓] Jenkins Sonar credential created

[✓] Nexus repository created

[✓] Nexus credential created

[✓] Slack app created

[✓] Slack bot installed

[✓] Slack token stored in Jenkins Credentials

[✓] SonarQube webhook configured

[✓] Jenkins pipeline created

[✓] Git checkout successful

[✓] Maven build successful

[✓] Unit tests executed

[✓] SonarQube analysis completed

[✓] Quality Gate evaluated

[✓] Artifact uploaded to Nexus

[✓] Slack notification received
```

---

# 🚨 Troubleshooting

## SonarQube Analysis Fails

Check Jenkins connectivity:

```bash
curl -I http://<SONARQUBE-PRIVATE-IP>:80
```

Check:

```text
SonarQube Security Group
```

allows:

```text
Jenkins SG → TCP 80
```

---

# Quality Gate Waits Forever

Verify the SonarQube webhook.

It should be:

```text
<JENKINS-URL>/sonarqube-webhook/
```

The trailing slash is required by the Jenkins SonarQube integration. :contentReference[oaicite:17]{index=17}

Also check that:

```text
SonarQube SG
      |
      | TCP 8080
      v
Jenkins
```

is permitted.

---

# Nexus Upload Fails

Check:

```text
Nexus URL
Repository name
Credential ID
Artifact path
Group ID
Artifact ID
Version
```

Verify the artifact exists:

```bash
ls -lh target/
```

Example:

```text
target/vprofile-v2.war
```

The Nexus uploader requires the Nexus URL, repository, credentials and artifact metadata. :contentReference[oaicite:18]{index=18}

---

# Slack Notification Fails

Check:

```text
Manage Jenkins
    ↓
System
    ↓
Slack
```

Verify:

```text
Workspace
Credential
Channel
Bot User option
```

Make sure the Jenkins bot is a member of the target Slack channel.

The current Slack plugin setup expects the bot OAuth token to be stored securely as a Jenkins Secret Text credential. :contentReference[oaicite:19]{index=19}

---

# 💰 Cost Considerations

This architecture introduces three principal application servers:

```text
Jenkins
+
SonarQube
+
Nexus
```

Potential AWS costs include:

```text
EC2
+
EBS
+
Public IPv4
+
Data Transfer
```

The actual cost depends on:

- Region
- Instance size
- Running hours
- Build frequency
- SonarQube analysis workload
- Nexus artifact storage
- Network traffic

For a learning environment, these resources can be kept small and stopped when not in use.

For production:

```text
Performance
+
Availability
+
Backup
+
Security
```

must be balanced against cost.

---

# 📈 Production Improvements

## 1. HTTPS

Replace:

```text
http://jenkins:8080
```

with:

```text
https://jenkins.example.com
```

and similarly provide secure endpoints for SonarQube and Nexus where appropriate.

---

## 2. Private Networking

Preferred production pattern:

```text
Internet
   |
   v
Reverse Proxy / Load Balancer
   |
   v
Jenkins

Jenkins
  |
  +---- Private IP ----> SonarQube
  |
  +---- Private IP ----> Nexus
```

---

## 3. Dedicated Deployment User in Nexus

Do not publish artifacts with:

```text
admin
```

Create:

```text
jenkins-nexus-publisher
```

with only the permissions required to upload artifacts.

---

## 4. Quality Gate Based on New Code

A mature quality policy should focus heavily on:

```text
New Bugs
New Vulnerabilities
New Code Smells
Coverage
Duplications
```

rather than only total historical issues.

---

## 5. Pipeline as Code

The pipeline should live alongside application source code as:

```text
Jenkinsfile
```

This makes the delivery process:

```text
Version Controlled
Auditable
Repeatable
Reviewable
```

---

## 6. Artifact Versioning

Instead of:

```text
1.0
```

for every build, use:

```text
1.0.${BUILD_NUMBER}
```

or a Git-derived version strategy.

---

## 7. Secrets Management

Future production architecture can use:

```text
AWS Secrets Manager
```

or another centralized secrets platform.

---

# 🧠 Skills Demonstrated

## AWS

- Amazon EC2
- Security Groups
- VPC networking
- Private IP communication
- Cloud infrastructure management
- Cost awareness

## Jenkins

- CI/CD
- Pipeline as Code
- Jenkins Credentials
- Plugin management
- Maven integration
- Quality Gate integration
- Artifact management
- Slack notifications

## SonarQube

- Static code analysis
- Quality profiles
- Quality Gates
- Authentication tokens
- Webhooks
- Jenkins integration

## Nexus

- Repository Manager
- Maven hosted repository
- Artifact publishing
- Repository credentials
- Artifact lifecycle

## Maven

- Build
- Unit testing
- Packaging
- WAR generation

## Slack

- Slack App
- Bot user
- OAuth token
- Build notifications

## Security

- Least privilege
- Secret management
- Security Groups
- Private networking
- SSH
- Webhook security

---

# 📂 Project Structure

```text
jenkins-sonarqube-nexus-slack/
│
├── README.md
│
├── Jenkinsfile
│
├── architecture/
│   └── ci-cd-quality-gate-architecture.png
│
├── infrastructure/
│   ├── nexus-user-data.sh
│   ├── sonarqube-user-data.sh
│   └── security-groups.md
│
├── docs/
│   ├── jenkins.md
│   ├── sonarqube.md
│   ├── nexus.md
│   ├── slack.md
│   └── troubleshooting.md
│
└── screenshots/
    ├── jenkins-pipeline.png
    ├── sonarqube-analysis.png
    ├── quality-gate.png
    ├── nexus-artifact.png
    └── slack-notification.png
```

---

# 🔐 Recommended `.gitignore`

```gitignore
# AWS private keys
*.pem
*.key

# SSH keys
id_rsa
id_ed25519

# Environment variables
.env
.env.*

# Credentials
credentials/
secrets/

# Logs
*.log

# SonarQube tokens
sonar-token*

# Nexus passwords
nexus-password*

# Slack tokens
slack-token*
```

---

# 🧠 Lessons Learned

## 1. A Successful Build Is Not Enough

A Maven build can pass while the code still contains serious quality problems.

Therefore:

```text
BUILD SUCCESS
        ≠
PRODUCTION READY
```

SonarQube introduces an explicit quality decision.

---

## 2. Quality Gates Turn Analysis Into Enforcement

A scan produces information.

A quality gate produces a decision:

```text
PASS
   or
FAIL
```

This makes code quality part of the delivery pipeline.

---

## 3. Nexus Separates Build from Delivery

The pipeline no longer treats the WAR file as an endpoint.

It becomes:

```text
Build
  ↓
Artifact
  ↓
Nexus
  ↓
Future Deployment
```

This creates a cleaner separation between:

```text
Build
Artifact Storage
Deployment
```

---

## 4. Slack Makes Pipeline State Visible

Developers do not need to constantly refresh Jenkins.

The pipeline can communicate:

```text
Build Started
Build Passed
Quality Gate Failed
Artifact Published
Build Failed
```

directly into the team's collaboration channel.

---

## 5. Webhooks Make Quality Gates Event-Driven

Instead of repeatedly polling SonarQube, Jenkins can wait for the SonarQube webhook to notify it that analysis has completed. Jenkins documents this model through `waitForQualityGate`. :contentReference[oaicite:20]{index=20}

---

# 🏆 Portfolio Value

This project demonstrates a significant progression from basic Jenkins administration to an integrated CI/CD quality system.

It connects:

```text
SOURCE CONTROL
      ↓
    GitHub
      ↓
CI/CD ORCHESTRATION
      ↓
    Jenkins
      ↓
BUILD & TEST
      ↓
    Maven
      ↓
CODE QUALITY
      ↓
  SonarQube
      ↓
QUALITY DECISION
      ↓
 Quality Gate
      ↓
ARTIFACT MANAGEMENT
      ↓
    Nexus
      ↓
TEAM COMMUNICATION
      ↓
    Slack
```

This demonstrates not only tool knowledge, but an understanding of how the tools combine to support a software delivery process.

---

# 🔮 Future CI/CD Evolution

The next stage can extend this architecture to containerized AWS deployment.

```text
GitHub
   ↓
Jenkins
   ↓
Maven
   ↓
Unit Test
   ↓
SonarQube
   ↓
Quality Gate
   ↓
Nexus
   ↓
Docker Build
   ↓
Amazon ECR
   ↓
Amazon ECS
   ↓
Production
   ↓
Slack
```

This turns the current project into a complete:

> **Build → Analyze → Validate → Store → Package → Deploy → Notify**

CI/CD lifecycle.

---

# 📌 Project Summary

### Project

**Jenkins with SonarQube, Nexus & Slack Notification**

### Pipeline

```text
GitHub
   ↓
Maven
   ↓
Unit Test
   ↓
SonarQube
   ↓
Quality Gate
   ↓
Nexus
   ↓
Slack
```

### Infrastructure

```text
AWS EC2
   |
   +-- Jenkins
   |
   +-- SonarQube
   |
   +-- Nexus
```

### Core DevOps Concepts

```text
Continuous Integration
Code Quality
Quality Gates
Artifact Management
Pipeline as Code
Security
Observability
Team Notification
AWS Infrastructure
```

---

# 📚 Official Documentation

### Jenkins SonarQube Integration

https://www.jenkins.io/doc/pipeline/steps/sonar/

### SonarQube Scanner Plugin

https://plugins.jenkins.io/sonar/

### Nexus Artifact Uploader

https://plugins.jenkins.io/nexus-artifact-uploader/

### Nexus Artifact Uploader Pipeline Step

https://www.jenkins.io/doc/pipeline/steps/nexus-artifact-uploader/

### Sonatype Nexus Repository

https://help.sonatype.com/

### Slack Notification Plugin

https://plugins.jenkins.io/slack/

### Jenkins Slack Pipeline Steps

https://www.jenkins.io/doc/pipeline/steps/slack/

### Maven

https://maven.apache.org/

### GitHub

https://github.com/

### Amazon EC2

https://docs.aws.amazon.com/ec2/

---

# 👨‍💻 Project Author

## Zhibrad

**Cloud & DevOps Portfolio**

Areas of focus:

```text
AWS
Jenkins
Linux
Docker
CI/CD
SonarQube
Nexus
GitHub
Maven
Cloud Security
Infrastructure Automation
DevOps
```

---

# ⭐ Final Architecture

```text
                             DEVELOPER
                                 |
                                 v
                              GitHub
                                 |
                                 v
                         Jenkins Controller
                                 |
                                 v
                         Maven Build/Test
                                 |
                                 v
                           SonarQube
                                 |
                                 v
                           Quality Gate
                          /            \
                       PASS             FAIL
                        |                 |
                        v                 v
                      Nexus             STOP
                        |
                        v
                Artifact Repository
                        |
                        v
                     Slack
                  Notification
```

> **Built to demonstrate production-oriented CI/CD engineering: automated builds, code-quality enforcement, artifact management, secure credential handling and real-time delivery notifications.**
