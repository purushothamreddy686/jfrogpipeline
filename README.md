
# Jenkins Setup on AWSEC2 (http://ec2-52-200-236-148.compute-1.amazonaws.com:8080/job/jfrogpipeline/):
# Artifacotry Setup on AWSEC2 (http://ec2-52-200-236-148.compute-1.amazonaws.com:8081/):

## Pre-requisites:
1. An AWS T3.large EC2 instance (Linux)
2. Open port 8081 and 8082 in the security group
3. installing jfrog artifactory on ec2
4. installation of jenkins on Ec2.
5. Configure that box with docker software.
6. install maven 3.5.0 to support project.
7. install java and stup java home to support project and jenkins.


## Installation Steps jfrog on EC2.
1. Login to instance as a root user and install Java  yum install java-1.8* -y  
2. Path download. cd /opt 
3. wget https://jfrog.bintray.com/artifactory/jfrog-artifactory-oss-6.9.6.zip 
4. extract artifactory tar.gz file unzip jfrog-artifactory-oss-6.9.6.zip 
5. Go to bin directory and start the services cd /opt/jfrog-artifactory-oss-6.9.6/bin
6. ./artifactory.sh start 
7. access artifactory from browser http://<PUBLIC_IP_Address>:8081  

Provide credentials for jfrog. 
```
username: admin
password: admin@123
 ## Artifactory url :  http://ec2-52-200-236-148.compute-1.amazonaws.com:8081/artifactory/webapp/#/home 
```
 
Provide credentials Jenkins.
```
User name : admin
Password: admin@123
##Jenkins url : http://ec2-52-200-236-148.compute-1.amazonaws.com:8080/
```
## Implementation steps:

### Settingup code in my local system and try to build the code to check any dependencies with maven created docker file to build docker image.

## Created jenkins pipeline using pipeline script to build and push the image to artifactory.(jenkinsfile in repo )
```
step 1: (git cloning code for spring-petclinic)
step 2: (mvn compile code stage)
step 3: (mvn test execution stage)
step 4: (After adding that docker file build image to push to artifactory )
step 5: (pushing that inage to artifactory)
```

## Runnable docker image and commands: 
```
docker command to build      : docker build -f Dockerfile  -t spring-petclinic
docker command to run image : docker run -p 8080:8080 -t spring-pet-clinic

```

