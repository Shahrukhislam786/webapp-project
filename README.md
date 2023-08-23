# Project: - "Automated CI/CD Pipeline for java web application to deploy on kubernetes cluster."

## **Tools and software’s:-** AWS, Jenkins, Ansible, Docker, Kubernetes, Git, Github.

## **Pre-requisites:-** 

1.	Create two ubuntu instances for testing purpose.  
   •	Create two t2.micro 8GB EC2 instance called QA-1 and QA-2.  
   •	Login to QA-1.  
   •	sudo passwd ubuntu  
   •	sudo vim /etc/ssh/sshd_config (Change PasswordAuthentication from no to yes).  
   •	sudo service ssh restart to restart the ssh service.  
   •	Repeat the same process for QA-2 server.  

2.	Create an ubuntu instance called Ansible-Controller and install ansible and pre-requisites S/w’s on it.  
   •	Login to Ansible-Controller.  
   •	ssh-keygen  
   •	ssh-id-copy ubuntu@Private_IP_of_QA-1  
   •	ssh-id-copy ubuntu@Private_IP_of_QA-2  
   •	sudo apt-get update  
   •	sudo apt-get install  –y software-properties-common  
   •	sudo apt-add-repository ppa:ansible/ansible  
   •	sudo apt-get install –y ansible  
   •	sudo vim /etc/ansible/hosts (Add private IP of QA-1 and QA-2 in this inventory file to make them ansible nodes)  
   •	sudo passwd ubuntu  
   •	sudo vim /etc/ssh/sshd_config (Change PasswordAuthentication from no to yes).  
   •	sudo service ssh restart to restart the ssh service.  

3.	Create an ubuntu instance called kops-server and install kubernetes on it and also create one master and two managed nodes.  
   •	Connect to master machine.  
   •	sudo passwd ec2-user  
   •	sudo vim /etc/ssh/sshd_config (Change PasswordAuthentication from no to yes).  
   •	sudo service sshd restart to restart the ssh service.  

4.	Create an ubuntu instance and install Jenkins and pre-requisites S/w’s on it and also install docker.
   •	Create a t2.micro 8GB EC2 instance and login to it.  
   •	Run sudo apt-get update to update the repository.  
   •	Run sudo apt-get install –y openjdk-11-jdk git maven to install java, git and maven.  
   •	curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
/usr/share/keyrings/jenkins-keyring.asc > /dev/null   
   •	echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null  
   •	sudo apt-get update  
   •	sudo apt-get install jenkins –y  
   •	curl -fsSL https://get.docker.com -o install-docker.sh  
   •	sudo sh install-docker.sh  
   •	ssh-keygen  
   •	ssh-id-copy ubuntu@Private_IP_of_Ansible-Controller.  
   •	ssh-id-copy ec2-user@Private_IP_of_kops_master-machine.
  	
6. Create a kubernetes cluster having one master and two node machines in AWS.

## **Completed password-less ssh connections we created:-**

![image](https://github.com/Shahrukhislam786/webapp-project/assets/120633106/a3ee38ad-a1cd-4fd4-bbbf-c50b337b70e3)

7.	Create a playbook in ansible controller to install pip, docker-py and docker in QA servers.  
   •	Connect to Ansible controller.  
   •	Create a playbook called install_s/w’s.yml file to install required s/w’s in QA Servers.  
   •	Create a playbook called deployment_QA.yml file to run the docker image we are going to create in QA Servers.  

8.	Create deployment and service manifest files in kubernetes master machine to deploy the application in  production environment i.e. Node 1 & 2.  
   •	Connect to Kubernetes master machine.  
   •	Create a deployment definition file called myapp-deployment.yml   
   •	Create a service definition file called myapp-service.yml  

9.	Create a pipeline script in Jenkins Server to run all the processes automatically.  
   •	Connect to Jenkins Server.  
   •	Create a user ID, Password and install suggested plugins.  
   •	Create a pipeline job called myapp.  
   •	Copy the contents of jenkins-pipeline in java-app job’s pipeline.  

## **Complete architecture we are going to created :-**

![image](https://github.com/Shahrukhislam786/webapp-project/assets/120633106/a24b1df8-4cb2-42a2-a4dc-eb62a4a8aa9d)

10. Create two playbooks in Ansible Controller.  
    •  pip&docker_setup.yml - (Run it to install the dependencies)  
    •	 testing_artifact.yml - (We will run it from Jenkins Pipeline)  

11. Create two kubernetes menifest files in Kubernetes master machine.  
    •	 myapp-deployment.yml - (We will run it from Jenkins Pipeline)  
    •  myapp-service.yml - (We will run it from Jenkins Pipeline)  

12. Create  a jenkins pipeline job called java-app and use the contents of jenkins-pipeline in it.  

13. Build the job.  

   
