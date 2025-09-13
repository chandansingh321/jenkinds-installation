# jenkinds-installation in ec2 instance

# Step 1: Install Java Before we can install Jenkins, we need to make sure Java is installed on our system. Follow these simple commands to update your system and install Java:

sudo apt update
sudo apt install openjdk-11-jre

# After installation, validate the installation by checking the Java version:

java -version

#You should see an output similar to this:

openjdk version "11.0.12" 2021-07-20
OpenJDK Runtime Environment (build 11.0.12+7-post-Debian-2)
OpenJDK 64-Bit Server VM (build 11.0.12+7-post-Debian-2, mixed mode, sharing)

# Step 2: Install Jenkins Now that Java is installed, let’s move on to installing Jenkins. Run the following commands in your terminal:

curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins

# Step 3: Start Jenkins With Jenkins installed, it’s time to start the service and ensure it’s running correctly:

sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins

# Step 4: Open Port 8080 in AWS Console To access Jenkins through your browser, you’ll need to open port 8080 on your AWS EC2 instance. This can be done through the AWS Management Console under the “Security Groups” settings.


# Last step: To get the admin password.

sudo cat /var/lib/jenkins/secrets/initialAdminPassword


# Second method: Using docker

# step 1. install docker 

sudo apt-get update
sudo install docker.io
docker 

# step 2. pull docker image

docker pull jenkins/jenkins

# step 3. run docker image

docker run -d -p 8080:8080 jenkins/jenkins:latest
