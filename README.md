📘 Config Server – README
📌 Overview
This project is a Spring Cloud Config Server that centralizes external configuration for multiple microservices using a remote Git repository:
https://github.com/mjimbenz/config-repo

The server provides a single, version-controlled source of configuration, allowing services to load properties dynamically based on their application name and environment.

🚀 Features

Centralized configuration for microservices
Git-based configuration repository
Auto-clone on startup
Supports multiple profiles and branches
Runs on port 8888
Fully compatible with Spring Boot & Spring Cloud

⚙️ Configuration
application.yml

PropertyDescriptionspring.profiles.active=configserverEnables Config Server modespring.application.name=config-serverName of the serviceserver.port=8888Default port for Config Serverspring.cloud.config.server.git.uriRemote Git repository URLdefault-label=mainDefault Git branchclone-on-start=trueClones repo on startup

▶️ How to Run
Run with Maven
Shellmvn spring-boot:runMostrar más líneas
Run with JAR
Shelljava -jarMostrar más líneas

🐳 Dockerfile (Simple Runtime Image)
Your project includes a lightweight Dockerfile that runs the Spring Cloud Config Server using a pre‑built JAR located in the target directory.
    ▶️ Build Instructions
    Before building the Docker image, you must first generate the JAR:
        mvn clean package -DskipTests
This creates a file in:
    target/config-server-0.0.1-SNAPSHOT.jar
    ▶️ Build the Docker Image
    Use the following command to build the Docker image:
        docker build -t config-server:latest .
    ▶️ Run the Docker Container
    After building the image, you can run it with:
        docker run -p 8888:8888 config-server:latest

🧪 Testing the Config Server
Test with an existing file from your Git repo, for example application.yml:
http://localhost:8888/application/default

Example for specific services:
http://localhost:8888/service-a/dev

If the server returns JSON/YAML from your Git repo, it's working correctly.

📁 Recommended Git Repository Structure
config-repo/
├── application.yml
├── service-a.yml
├── service-b-dev.yml
└── service-b-prod.yml


🧩 Architecture Overview
[Microservices]  --->  [Config Server]  --->  [Git Repository]


🧰 Technologies Used
Java 17+
Spring Boot
Spring Cloud Config
Git


✨ Author
Miguel Autberto Jiménez Benzol
Centralized configuration for microservices.