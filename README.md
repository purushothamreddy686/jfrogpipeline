
# jenkins url (http://ec2-52-200-236-148.compute-1.amazonaws.com:8080/job/jfrogpipeline/):
# Artifacotry Setup on AWSEC2 (http://ec2-52-200-236-148.compute-1.amazonaws.com:8081/):

## Pre-requisites:
1. An AWS T2.small EC2 instance (Linux)
2. Open port 8081 and 8082 in the security group

## Installation Steps
1. Login to instance as a root user and install Java  yum install java-1.8* -y  
2. Path download. cd /opt 
3. wget https://jfrog.bintray.com/artifactory/jfrog-artifactory-oss-6.9.6.zip 
4. extract artifactory tar.gz file unzip jfrog-artifactory-oss-6.9.6.zip 
5. Go inside to bin directory and start the services cd /opt/jfrog-artifactory-oss-6.9.6/bin
6. ./artifactory.sh start 
7. access artifactory from browser http://<PUBLIC_IP_Address>:8081  
```

9. Provide credentials username: admin
10. password: admin@123
 ## Artifactory url :  http://ec2-52-200-236-148.compute-1.amazonaws.com:8081/artifactory/webapp/#/home 
 ```
 
## Jenkins setup on AWSec2 box.
```

Jenkins url : http://ec2-52-200-236-148.compute-1.amazonaws.com:8080/
User name : admin
Password: admin@123
```

## Settingup code in my local and creating docker file and building it like docker images to push to artifactory:

### 1)create dockerfile to build spring-petclinic as docker image.
### 2)run "mvn clean install (complie the code)
### 3)run "mvn test" (intigrating test)

## Creating jenkins file to create automated pipeline and push the image to artifactory:
```
### STAGES :(script is located in jenkins file)https://github.com/purushothamreddy686/jfrogpipeline/blob/main/jenkinsfile
1)clone code from git hub .
2)compile code with (mvn clean install).
3)run the tests("mvn test")
4)package the package as runnible docker image (add docker file for that repo.)
5)push that docker file to artifactory server.


![pipeline!]https://user-images.githubusercontent.com/12862506/163022148-4bfaa3e0-74e7-4329-8d52-2a1c9f7e3cdb.png


```

