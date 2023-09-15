# Deploying wordpress on AWS/Azure with RDS using Terraform, and Docker

# First install Terraform :
$ wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
$ echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
$ sudo apt update && sudo apt install terraform

Install the aws configure and aws CLI:
$ apt install awscli
$ aws configure

AWS Access Key ID and Secret Access Key. Once you have successfully created the environmental variables
export AWS_ACCESS_KEY_ID : AKIAT4ZKQDXXXXXX
export AWS_SECRET_ACCESS_KEY= dlByjJ/XA8iwcvIDxgXXX

Create a folder with whatever name you want. Let’s name it Terraform. Inside the Terraform folder, create a file named main.tf


 

 ![Screenshot (61)](https://github.com/hariharanhh/100-Points-Description-Leaderboard-Deploying-wordpress-on-AWS/assets/110392389/a8a43d7f-7704-4cc2-bc8e-1a32ea798b89)



Then, run the following command to install all of the necessary plugins 



$ Terraform init

 ![Screenshot (67)](https://github.com/hariharanhh/100-Points-Description-Leaderboard-Deploying-wordpress-on-AWS/assets/110392389/dbb9982a-88c5-43f9-947c-f380ac62df8c)

$ Terraform plan


 

$ Terraform apply

 

After running the $ terraform apply command, it will take some time for the infrastructure to be created. During this time, you can open the AWS Console and see all of the resources being created.


 

After creating all resources over Terraform. Now, go to the EC2 instance that you have created

 

Once you have successfully SSHed into your EC2 instance, install Docker and Docker Compose

Commands to build the images:

$ docker build -t my-wordpress-image -f /home/ubuntu/wordpress/Dockerfile 
$ docker build -t my-apache-php-image -f /home/ubuntu/apache-php/Dockerfile

Login to your Docker Hub account using the following command:

$ docker login

Before pushing the image to Docker Hub, you need to tag it with your Docker Hub username and the desired repository name
$ docker tag wordpress:latest hariharan/wordpress:new_version

After tagging the image, push it to Docker Hub using the following command:
$ docker push hariharan/wordpress:new_version


 

 

Finally, go to your Docker Hub account at and navigate to your repository. You should see the pushed image listed in the repository.
 



Finally, run the following command to deploy the WordPress stack. Make sure that you are running below command where the docker-compose.yml  file saved.

$ docker-compose up -d

Enter the EC2 public ip

 

Click on continue button, it will take you to next step.

 

Fill the required details and login into it.

 

 

 


