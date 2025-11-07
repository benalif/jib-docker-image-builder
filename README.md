# 🚀 Jib Docker Image Builder — Spring Boot Demo

This project demonstrates how to **build and push Docker images without Docker installed**, using the powerful [Jib Maven Plugin](https://github.com/GoogleContainerTools/jib).

---

## 🧩 Overview

Instead of writing a `Dockerfile`, Jib integrates directly into your **Maven build** to:

- Build optimized Docker and OCI images for Java applications
- Layer your Spring Boot JAR intelligently (faster rebuilds 🏎️)
- Push directly to any container registry (securely 🔐)
- Work **without needing Docker or root privileges**

---

## ⚙️ Tech Stack

- **Java:** 21
- **Spring Boot:** 3.5.7
- **Jib Maven Plugin:** 3.4.6
- **Spring Boot Starter Web** + **Actuator**

---

## 📦 POM Configuration

Here’s the relevant part of the `pom.xml`:

```xml
<plugin>
    <groupId>com.google.cloud.tools</groupId>
    <artifactId>jib-maven-plugin</artifactId>
    <version>3.4.6</version>
    <configuration>
        <allowInsecureRegistries>true</allowInsecureRegistries>
        <to>
            <image>localhost:5003/${project.artifactId}:${project.version}</image>
            <auth>
                <username>${env.YOUR_REGISTRY_USER}</username>
                <password>${env.YOUR_REGISTRY_PWD}</password>
            </auth>
        </to>
        <from>
            <image>localhost:5002/eclipse-temurin:21-jre</image>
        </from>
        <container>
            <ports>
                <port>8080</port>
            </ports>
        </container>
    </configuration>
</plugin>
```

> 🧠 **Tip:** Replace `localhost:5002` and `localhost:5003` with your actual Docker registry endpoints.  
> You can use Nexus, Harbor, or any private Docker registry.

---

## 🏗️ Build and Push in One Command

You can build and push your Spring Boot app as a container image with:

```bash
mvn clean compile jib:build
```

Or, to build locally (without pushing):

```bash
mvn compile jib:dockerBuild
```

---

## 🔍 Why Use Jib?

✅ **No Dockerfile needed** — it handles everything internally.  
✅ **Layered image caching** — rebuilds are much faster.  
✅ **Secure** — avoids using Docker Daemon directly.  
✅ **CI/CD friendly** — integrates seamlessly with Jenkins, GitLab, or GitHub Actions.

---

## 📊 Example Output

When you run the build:

```
[INFO] Containerizing application to localhost:5003/jib-image-builder:0.0.1...
[INFO] Built image to Docker daemon as localhost:5003/jib-image-builder:0.0.1
[INFO] Pushed image successfully!
```

---

## 🧠 Key Takeaways

- Jib simplifies Java containerization.
- It’s a **developer-friendly**, **Dockerless**, and **repeatable** approach.
- Ideal for **Spring Boot microservices** in **enterprise CI/CD pipelines**.

---

## 👨‍💻 Author

**Farid BENALI**  
💼 Software Engineer | Backend Developer | Spring & Cloud Enthusiast  
📍 Algiers, Algeria  
🔗 [LinkedIn Profile](https://www.linkedin.com/in/farid-benali-6547a5139/)

---

## 🗨️ Share Your Thoughts

If you’ve tried Jib or plan to integrate it in your projects, feel free to share your experience or questions in the comments — I’d love to discuss it! 🙌  
