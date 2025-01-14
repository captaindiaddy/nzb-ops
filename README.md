# Setting Up Docker Bind Mounts and Directories for Plex and Related Services

This guide explains how to configure bind mounts for your Docker setup, detailing paths and steps for creating necessary directories, identifying your Docker ID, and deploying your stack.

---

## **Understanding Bind Mounts**

Bind mounts pass data from the host machine into the Docker container. Any paths separated by a colon (`:`) indicate the host path on the left and the container path on the right.

### Example:

```text
/volume1/docker/plex/config:/config
```

- `/volume1/docker/plex/config`: Path on the **host** machine.
- `:/config`: Path inside the **container**.

### **Key Terms**:
- **Host**: The machine where Linux and Docker are running.
- **Container**: The isolated environment managed by Docker.

---

## **Paths on Your Host Machine**

### Media Directory:
```bash
/volume1/Media
```

### Plex Directories:
```bash
/volume1/docker/plex/config
/volume1/docker/plex/transcode
```

### Other Service Directories:
```bash
/volume1/docker/sonar
/volume1/docker/radar
/volume1/docker/sabnzbd
/volume1/docker/ombi
```

---

## **Steps to Set Up**

### 1. Create Necessary Directories on the Host
Ensure you create the directories before running the stack. Use the following commands or navigate in your file explorer:

```bash
mkdir -p /volume1/docker/plex/config
mkdir -p /volume1/docker/plex/transcode
mkdir -p /volume1/docker/sonar
mkdir -p /volume1/docker/radar
mkdir -p /volume1/docker/sabnzbd
mkdir -p /volume1/docker/ombi
```

### Example Path:
```bash
/home/<username>/docker/plex
```

Replace `<username>` with your actual username.

---

### 2. Find Your Docker User and Group ID
To determine your Docker user and group ID:
1. SSH into your host machine.
2. Type the following command and hit Enter:
   ```bash
   id
   ```
3. Note the **UID** (User ID) and **GID** (Group ID).

---

### 3. Install Portainer CE
Portainer CE is a user-friendly management interface for Docker.

- Follow the [Portainer installation guide](https://docs.portainer.io/start/install-ce/server/docker/linux) to install Portainer CE.

---

### 4. Deploy Your Docker Compose Stack
1. Log in to Portainer CE.
2. Navigate to:
   ```text
   Home > Environments > <Your Environment> > Stacks > Add stack
   ```
3. Paste your Docker Compose YAML into the **stack editor**.
4. Save and deploy the stack.

---

## **Final Notes**

- Ensure all directories have the correct permissions based on your Docker user and group ID.
- Bind mounts are critical for persisting data across container updates or restarts.

Let me know if you’d like assistance with creating the Docker Compose file or anything else!