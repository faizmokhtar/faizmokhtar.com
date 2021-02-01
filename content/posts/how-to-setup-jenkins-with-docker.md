---
title: "How to setup Jenkins with Docker"
date: 2020-09-26T08:57:56.525Z
tags:
  - tools
comments: true
---
Here is an easy way to setup [Jenkins][1] with [Docker][2]

1. Run the following commands in your terminal

```bash
docker pull jenkins/jenkins:lts
docker run --detach --publish 8080:8080 --volume
jenkins_home:/var/jenkins_home --name jenkins jenkins/jenkins:lts
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

2. The above command will generate a password. Copy said password

3. Open `localhost:8080` and paste in the password

4. Setup your user account and install suggested plugins.

That's it!

[1]: https://www.jenkins.io/
[2]: https://www.docker.com/
