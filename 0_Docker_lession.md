# Step-by-Step Guide to Install Docker on Linux (Ubuntu and CentOS)

## Installing Docker on Ubuntu

1. **Update the Package Index**  
    ```bash
    sudo apt-get update
    ```

2. **Install Required Packages**  
    ```bash
    sudo apt-get install -y ca-certificates curl gnupg
    ```

3. **Add Docker’s Official GPG Key**  
    ```bash
    sudo install -m 0755 -d /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    sudo chmod a+r /etc/apt/keyrings/docker.gpg
    ```

4. **Set Up the Docker Repository**  
    ```bash
    echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    ```

5. **Install Docker Engine**  
    ```bash
    sudo apt-get update
    sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
    ```

6. **Verify Installation**  
    ```bash
    sudo docker --version
    ```

---

## Installing Docker on CentOS

1. **Update the System**  
    ```bash
    sudo yum update -y
    ```

2. **Install Required Packages**  
    ```bash
    sudo yum install -y yum-utils
    ```

3. **Set Up the Docker Repository**  
    ```bash
    sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
    ```

4. **Install Docker Engine**  
    ```bash
    sudo yum install -y docker-ce docker-ce-cli containerd.io
    ```

5. **Start and Enable Docker**  
    ```bash
    sudo systemctl start docker
    sudo systemctl enable docker
    ```

6. **Verify Installation**  
    ```bash
    sudo docker --version
    ```

---

## Post-Installation Steps (Optional)

- **Run Docker as a Non-Root User**  
    ```bash
    sudo groupadd docker
    sudo usermod -aG docker $USER
    newgrp docker
    ```

- **Test Docker**  
    ```bash
    docker run hello-world
    ```
