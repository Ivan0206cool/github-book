# 用docker安裝jenkins

1. 查看docker有無安裝  (<mark style="color:red;">**docker --version**</mark>)

```bash
docker --version
```

2. 創建docker volumn ( <mark style="color:red;">docker volume create jenkins\_home</mark>）

```bash
docker volume create jenkins_home
```

3. 拉取docker images  LTS Jenkins(<mark style="color:red;">docker pull jenkins/jenkins</mark>）

```bash
docker pull jenkins/jenkin
```

4. 運行jenkins docker container

```bash
docker run -d \
  --name jenkins-blueocean \
  -p 8080:8080 \
  -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  jenkins/jenkins
```

* `-d`: Runs the container in detached mode (in the background).
* `--name jenkins-blueocean`: Assigns a readable name to your container. You can choose any name you like.
* `-p 8080:8080`: Maps port 8080 on your host machine to port 8080 in the container (Jenkins web UI).
* `-p 50000:50000`: Maps port 50000 on your host to port 50000 in the container. This port is used for Jenkins agents to communicate with the master.
* `-v jenkins_home:/var/jenkins_home`: Mounts the `jenkins_home` Docker volume to `/var/jenkins_home` inside the container. This is crucial for data persistence.
* `jenkins/jenkins:lts-jdk17`: The Jenkins image and tag you pulled.

5. 確認Jenkins URL

```url
http://localhost:8080
```
