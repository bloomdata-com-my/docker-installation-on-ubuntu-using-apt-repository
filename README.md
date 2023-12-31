# Docker installation on Ubuntu using APT repository
Installing docker on Ubuntu 22.04 using APT repository

## 1. Set up Docker's Apt repository.
### Add Docker's official GPG key:
```
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```
### Add the repository to Apt sources:
```
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

## 2. Install the Docker packages.
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## 3. Verify that the Docker Engine installation is successful by running the hello-world image.
```
sudo docker run hello-world
```

## 4. Create the docker group.
```
sudo groupadd docker
```

## 5. Add your user to the docker group.
```
sudo usermod -aG docker $USER
```

## 6. Log out and log back in so that your group membership is re-evaluated.
```
newgrp docker
```

## 7. Verify that you can run docker commands without sudo.
```
docker run hello-world
```
