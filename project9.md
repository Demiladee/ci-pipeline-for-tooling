
## installing and configuring jenkins server

updating ubuntu

`$ sudo apt update -y`

![](images/jenkinsupdate1.png)

installing jdk 

`$ sudo apt install default-jdk-headless`

![](images/jenkinsinstalljdk2.png)

installing jenkins

`$ wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -`

`$ sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > \ /etc/apt/sources.list.d/jenkins.list'`

`$ sudo apt update -y`

`$ sudo apt-get install jenkins`

![](images/jenkinsinstalljenkins3.png)

`$ sudo systemctl status jenkins`

![](images/jenkinsstatus4.png)

opening tcp port 8080 on jenkins ec2 security group

![](images/jenkinstcpp5.png)

jenkins first test

`http://<Jenkins-Server-Public-IP-Address-or-Public-DNS-Name>:8080`

![](images/jenkinssetup6.png)

retrieving password 

`$ sudo cat /var/lib/jenkins/secrets/initialAdminPassword`

![](images/jenkinssetupp7.png)

![](images/jenkinsadmin9.png)

![](images/jenkinssetupcomp10.png)

## configuring jenkins to retrieve source codes from github using webhooks

![](images/jenkinswebhook11.png)

creating freestyle project on jenkins console

![](images/jenkinsfreestyle12.png)

configured the project with the link to my github tooling repo and proceeded to build

![](images/jenkinsbuildsuccess13.png)

configuring triggering jobs from github webhook and archiving files resulted from builds in post-build actions

![](images/jenkinsconfig14.png)

made changes to my readme file and the build was launched automatically

![](images/jenkinsgitautom15.png)

![](images/jenkinsauto16.png)

confirming artifacts are stored on jenkins server locally

`$ ls /var/lib/jenkins/jobs/tooling_github/builds/<build_number>/archive/`

![](images/jenkinsarti17.png)


## configuring jenkins to copy files to nfs server via ssh

installed 'publish over ssh' plugin

configured the job to copy artifacts via ssh to nfs server - /mnt/apps directory - and ran a test

![](images/jenkinssshtest13.png)

![](images/jenkinssshconfig14.png)

saved configuration and edited readme file to trigger the build automatically

![](images/jenkinssshtest15.png)

confirming that files on /mnt/apps have been updated

`$ cat /mnt/apps/README.md`

![](images/jenkinsfinal21.png)