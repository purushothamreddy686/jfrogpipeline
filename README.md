Artifacotry Setup
An artifact repository manages your end-to-end artifact lifecycle and supports different software package management systems while providing consistency to your CI/CD workflow. An artifact repository is both a source for artifacts needed for a build and a target to deploy artifacts generated in the build process.
JFrog Artifactory is a universal DevOps solution providing end-to-end automation and management of binaries and artifacts through the application delivery process that improves productivity across your development ecosystem. It enables freedom of choice supporting 25+ software build packages, all major CI/CD platforms, and DevOps tools you already use.

Pre-requisites:
1. An AWS T2.small EC2 instance (Linux)
2. Open port 8081 and 8082 in the security group

Installation Steps
1. Login to instance as a root user and install Java  yum install java-1.8* -y  
2. Path download. cd /opt 
3. wget https://jfrog.bintray.com/artifactory/jfrog-artifactory-oss-6.9.6.zip 
4. extract artifactory tar.gz file unzip jfrog-artifactory-oss-6.9.6.zip 
5. Go inside to bin directory and start the services cd /opt/jfrog-artifactory-oss-6.9.6/bin
6. ./artifactory.sh start 
7. access artifactory from browser http://<PUBLIC_IP_Address>:8081  
8. Provide credentials username: admin
9. password: admin@123
10. 
11. Artifactory url :  http://ec2-52-200-236-148.compute-1.amazonaws.com:8081/artifactory/webapp/#/home //////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

Jenkins setup:/ on ec2 box.

Jenkins url : http://ec2-52-200-236-148.compute-1.amazonaws.com:8080/

User name : admin
Password: admin@123


Settingup code in my local and creating docker file and building it like docker images to push to artifactory:

1)create dockerfile to build spring-petclinic as docker image.
2)run "mvn clean install (complie the code)
3)run "mvn test" (intigrating test)

creating jenkins file to create automated pipeline:
STAGES :
1)clone code from git hub .
2)compile code with (mvn install).
3)run the tests("mvn test")
4)package the package as runnible docker image (add docker file for that repo.)
5)push that docker file to artifactory server.

Integrating Artifactory with Jenkins to push docker image: 
