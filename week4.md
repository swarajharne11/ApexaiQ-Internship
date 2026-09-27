---
layout: default
title: "Week 4"
---

# Linux Architecture, DevOps Basics, and Docker Containerization

---

## Table of Contents

1. Linux Core Concepts
2. Linux Command Glossary (Selected Commands)
3. DevOps Basics
4. Why Docker? Containerization Basics
5. Hands-On Project: Node.js Express App in Docker

---

## 1. Linux Core Concepts: Operating System vs. Kernel

**The Linux Kernel:** The kernel is the foundational core of the operating system. It acts as an invisible intermediary between computer hardware (CPU, RAM, hard drives, network cards) and the software running on it. The kernel handles memory allocation, process scheduling, security restrictions, and hardware communication via device drivers.

**The Linux Operating System (Distribution):** What we normally call "Linux" is actually a complete distribution built on top of the Linux kernel, wrapped with a shell (Bash, Zsh), package managers (apt, dnf), and application packages. Examples: Kali Linux (penetration testing), Ubuntu (general usability), Debian (stability).

**Why We Use Linux in Modern Tech Infrastructure**
- **Open Source & Free** — inspectable, modifiable, no licensing costs.
- **Stability & Performance** — runs for years without slowdowns or forced reboots.
- **Unmatched Automation** — native scripting for server scaling and deployment.
- **Granular Security** — native multi-user permissions resist privilege escalation.

---

## 2. Linux Command Glossary (Selected Commands)

### A. File System Navigation & Operations

| Command | Primary Function | Example |
|---|---|---|
| `pwd` | Print Working Directory (shows current path) | `pwd` |
| `ls` | List directory contents (`-la` shows hidden files/permissions) | `ls -la` |
| `mkdir` | Make a new directory | `mkdir -p project/src` |

### B. Content Inspection & Text Processing

| Command | Primary Function | Example |
|---|---|---|
| `cat` | Print full file contents to screen | `cat app.js` |
| `tail` | View the last few lines of a file | `tail -n 20 error.log` |
| `grep` | Search for text patterns in a file | `grep 'require' app.js` |

### C. System Permissions & Privileges

| Command | Primary Function | Example |
|---|---|---|
| `sudo` | Run a command with root privileges | `sudo apt update` |
| `chmod` | Change file read/write/execute permissions | `chmod +x app.sh` |
| `whoami` | Display current logged-in user | `whoami` |

### D. Network Analysis & Troubleshooting

| Command | Primary Function | Example |
|---|---|---|
| `ping` | Test live connectivity to a host | `ping 8.8.8.8` |
| `curl` | Transfer data to/from a server | `curl -fsSL https://get.docker.com` |
| `ss` | List active network sockets and ports | `ss -tulpn` |

---

## 3. DevOps Basics

DevOps is a set of practices that bring software development (Dev) and IT operations (Ops) together, aiming to build, test, and release software faster and more reliably.

### Core Philosophy

Traditionally, developers wrote code and "threw it over the wall" to operations teams to deploy and maintain. This created friction, slow releases, and finger-pointing when things broke. DevOps breaks down that wall by making one team (or closely collaborating teams) responsible for the whole lifecycle: writing, testing, deploying, and running the software.

### Key Principles

- **Collaboration** — Dev, Ops, QA, and security work together from the start rather than in silos.
- **Automation** — Manual, repetitive tasks (building, testing, deploying, provisioning) are automated to reduce error and speed delivery.
- **Continuous Integration (CI)** — Developers merge code frequently into a shared repository, where automated builds and tests catch problems early.
- **Continuous Delivery/Deployment (CD)** — Code that passes tests is automatically prepared for release (Delivery) or pushed straight to production (Deployment).
- **Infrastructure as Code (IaC)** — Servers and environments are defined in code (Terraform, Ansible) instead of manually configured, making infrastructure reproducible and version-controlled.
- **Monitoring and Feedback** — Production systems are constantly watched so teams can catch issues quickly and feed insights back into development.

### The DevOps Lifecycle

An infinite loop with these stages: **Plan → Code → Build → Test → Release → Deploy → Operate → Monitor** → back to Plan.

### Common Tools by Category

- **Version control:** Git, GitHub, GitLab
- **CI/CD:** Jenkins, GitHub Actions, GitLab CI, CircleCI
- **Containerization:** Docker
- **Orchestration:** Kubernetes
- **Configuration/IaC:** Ansible, Terraform, Chef, Puppet
- **Monitoring:** Prometheus, Grafana, Datadog
- **Cloud platforms:** AWS, Azure, Google Cloud

### Why It Matters

- Faster release cycles
- Fewer failed deployments
- Quicker recovery when things go wrong
- Better collaboration and less blame-shifting
- More stable, reliable systems

---

## 4. Core Containerization Framework: Why Docker?

Docker addresses a classic engineering flaw: software failing because of environmental disparities between a developer's laptop and a production server. It bundles application components together into an automated pipeline.

### What is Docker?

Docker is a platform that packages an application together with everything it needs to run — code, runtime, system libraries, and settings — into a single unit that behaves the same way on any machine. It removes the "it works on my machine" problem by standardizing how software is built, shipped, and run.

### What is a Docker Image?

A Docker image is a read-only blueprint or template. It contains the application code, dependencies, and instructions for how the app should run, all baked in as layers. Images are built once (using a Dockerfile) and can then be reused to create any number of containers. Think of an image as a snapshot or recipe — it doesn't run by itself.

### What is a Docker Container?

A Docker container is a running instance of an image. It's a live, isolated process on the host machine, with its own filesystem, network, and process space, but it shares the host's kernel instead of needing its own OS. If an image is the recipe, a container is the actual dish made from it — you can spin up many identical containers from the same image.

### Benefits of Docker

- **Consistency** — the same image runs identically on a laptop, test server, or production cloud.
- **Lightweight & Fast** — containers share the host kernel, so they start in seconds and use far less CPU/RAM than a full VM.
- **Isolation** — each container runs in its own sandbox, so dependency conflicts between apps disappear.
- **Portability** — an image built once can run on any system that has Docker installed, regardless of the underlying OS.
- **Scalability** — containers can be spun up or torn down quickly, making them ideal for scaling applications up or down on demand.
- **Version Control for Environments** — Dockerfiles are just text, so environment setup can be tracked in Git like any other code.

---

## 5. Task: Run a Python Program on Localhost Using Docker

This task packages a simple Python (Flask) web app into a Docker image and runs it so it's accessible on `localhost`. Each step below explains *what* is happening and *why*, followed by the exact command(s) to run.

### Step 1 — Prepare the network so Docker can pull images

Before building anything, Docker needs to reach the internet to download the base Python image and packages. On some systems (especially inside VMs or Kali), the default DNS can time out. Setting public DNS servers avoids this:

```bash
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo systemctl restart docker
```

The first command writes Google's public DNS servers into the system's resolver file, and the second restarts the Docker service so it picks up the new network settings.

### Step 2 — Create a clean project workspace

Keeping the project in its own folder ensures the Dockerfile only sees the files it actually needs (Docker copies the whole build context, so a messy folder means a bloated image):

```bash
rm -rf ~/python-web-project
mkdir -p ~/python-web-project && cd ~/python-web-project
```

The `rm -rf` removes any leftover folder from a previous attempt, `mkdir -p` creates a fresh one, and `cd` moves into it so every following command runs in the right place.

### Step 3 — Write the Python application code

This is the actual program that will run inside the container. It starts a small web server using Flask, and every time someone visits the page, it responds with the current server time:

```bash
nano app.py
```

Inside the editor, type:

```python
from flask import Flask
from datetime import datetime

app = Flask(__name__)

@app.route('/')
def home():
    current_time = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
    return f"""
    <html>
        <body style="background-color:#0d1117; color:#58a6ff; font-family:sans-serif; text-align:center; padding-top:100px;">
            <h1>🚀 Live Python Web Application Inside Docker!</h1>
            <p style="color:#ffffff; font-size:20px;">Project Status: Running Successfully</p>
            <p style="color:#8b949e;">Container Live Clock: {current_time}</p>
        </body>
    </html>
    """

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```

Save and exit nano (`Ctrl+O`, `Enter`, then `Ctrl+X`). Note that the app binds to `0.0.0.0` rather than `127.0.0.1` — this is required so the server accepts connections coming from outside the container (i.e., from your host machine's browser).

### Step 4 — Write the Dockerfile (the image's build recipe)

The Dockerfile tells Docker exactly how to assemble the environment this app needs — which base OS/runtime to start from, what to install, and what to run when the container starts:

```bash
nano Dockerfile
```

Type the following:

```dockerfile
# 1. Start from a small, official Python 3.11 base image
FROM python:3.11-slim

# 2. Set /app as the working directory inside the container
WORKDIR /app

# 3. Install Flask, the only dependency this app needs
RUN pip install flask

# 4. Copy our app.py file from the host into the container's /app folder
COPY app.py .

# 5. Document that the app listens on port 5000 (informational only)
EXPOSE 5000

# 6. Define the command that runs automatically when the container starts
CMD ["python", "app.py"]
```

Each instruction becomes a "layer" in the final image, executed top to bottom in order.

### Step 5 — Build the Docker image

This command reads the Dockerfile and actually assembles the image, downloading the base Python layer, installing Flask, and copying in the app code:

```bash
sudo docker build -t python-web-app .
```

- `-t python-web-app` tags (names) the image so it's easy to reference later.
- The trailing `.` tells Docker to use the current folder as the build context (where it looks for the Dockerfile and `app.py`).

### Step 6 — Run a container from the image

This takes the built image and starts it as a live, running process:

```bash
sudo docker run -d -p 5000:5000 --name python_app_container python-web-app
```

- `-d` runs the container in detached mode (in the background, so your terminal stays free).
- `-p 5000:5000` maps port 5000 on your host machine to port 5000 inside the container, which is what makes the app reachable via `localhost`.
- `--name python_app_container` gives the running container a friendly name for future reference (e.g., to stop or inspect it later).
- `python-web-app` is the image to run it from.

### Step 7 — Verify the app is live on localhost

Open a web browser and navigate to:

```
http://localhost:5000
```

You should see the styled page with a live timestamp. Refresh the page a few times — the clock should update on each request, confirming that the Flask app is actively running inside the Docker container and responding to real requests through the mapped port.

### Step 8 — (Optional) Check status and stop the container

Useful follow-up commands once the container is running:

```bash
sudo docker ps                        # Lists all currently running containers
sudo docker logs python_app_container # Shows the app's console output
sudo docker stop python_app_container # Stops the running container
```
