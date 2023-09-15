# Deploying wordpress on AWS/Azure with RDS using Terraform, and Docker

# First install Terraform :
$ wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
$ echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
$ sudo apt update && sudo apt install terraform

# Install the aws configure and aws CLI:
$ apt install awscli
$ aws configure

# AWS Access Key ID and Secret Access Key. Once you have successfully created the environmental variables
export AWS_ACCESS_KEY_ID : AKIAT4ZKQDXXXXXX
export AWS_SECRET_ACCESS_KEY= dlByjJ/XA8iwcvIDxgXXX

Create a folder with whatever name you want. Let’s name it Terraform. Inside the Terraform folder, create a file named main.tf


 

 ![Screenshot (61)](https://github.com/hariharanhh/100-Points-Description-Leaderboard-Deploying-wordpress-on-AWS/assets/110392389/a8a43d7f-7704-4cc2-bc8e-1a32ea798b89)



Then, run the following command to install all of the necessary plugins 



$ Terraform init

 ![Screenshot (67)](https://github.com/hariharanhh/100-Points-Description-Leaderboard-Deploying-wordpress-on-AWS/assets/110392389/dbb9982a-88c5-43f9-947c-f380ac62df8c)

$ Terraform plan


 
![Screenshot (62)](https://github.com/hariharanhh/100-Points-Description-Leaderboard-Deploying-wordpress-on-AWS/assets/110392389/1b942a71-32a3-45fd-8b1e-2be5cc93eb57)

$ Terraform apply

 ![Screenshot (69)](https://github.com/hariharanhh/100-Points-Description-Leaderboard-Deploying-wordpress-on-AWS/assets/110392389/0c7262c0-26dc-4b88-9f2a-c0dfb7b0b2fa)


After running the $ terraform apply command, it will take some time for the infrastructure to be created. During this time, you can open the AWS Console and see all of the resources being created.

![WhatsApp Image 2023-09-15 at 16 04 05](https://github.com/hariharanhh/100-Points-Description-Leaderboard-Deploying-wordpress-on-AWS/assets/110392389/5e1e4293-4356-4552-9fd8-4d0693acb036)

 

After creating all resources over Terraform. Now, go to the EC2 instance that you have created

 ![WhatsApp Image 2023-09-15 at 16 09 21](https://github.com/hariharanhh/100-Points-Description-Leaderboard-Deploying-wordpress-on-AWS/assets/110392389/72467d60-526d-434a-870e-a9d79d54e874)


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


![WhatsApp Image 2023-09-15 at 19 55 18](https://github.com/hariharanhh/100-Points-Description-Leaderboard-Deploying-wordpress-on-AWS/assets/110392389/eb9321d1-ac46-47a0-b42b-05eed17a2be7)


 
![WhatsApp Image 2023-09-15 at 19 55 18 (1)](https://github.com/hariharanhh/100-Points-Description-Leaderboard-Deploying-wordpress-on-AWS/assets/110392389/d3543961-e9a2-4932-a8ab-b838879c5d99)

 

Finally, go to your Docker Hub account at and navigate to your repository. You should see the pushed image listed in the repository.

 
![WhatsApp Image 2023-09-15 at 21 10 56 (1)](https://github.com/hariharanhh/100-Points-Description-Leaderboard-Deploying-wordpress-on-AWS/assets/110392389/0b7b3461-577d-404c-bfea-caa5480c1afe)



Finally, run the following command to deploy the WordPress stack. Make sure that you are running below command where the docker-compose.yml  file saved.

$ docker-compose up -d

Enter the EC2 public ip


 ![56](https://github.com/hariharanhh/100-Points-Description-Leaderboard-Deploying-wordpress-on-AWS/assets/110392389/3f3cf910-3670-434f-8419-c8f39e8d8247)


Click on continue button, it will take you to next step.


 ![2](https://github.com/hariharanhh/100-Points-Description-Leaderboard-Deploying-wordpress-on-AWS/assets/110392389/4b2419c5-ac1b-4cda-a085-a49cb620b453)


Fill the required details and login into it.

 

 
![3](https://github.com/hariharanhh/100-Points-Description-Leaderboard-Deploying-wordpress-on-AWS/assets/110392389/244f357c-57b1-4746-8566-8cb0e0fea139)

 ![4](https://github.com/hariharanhh/100-Points-Description-Leaderboard-Deploying-wordpress-on-AWS/assets/110392389/e2839d80-325a-4580-acaf-3eb983041d6d)



![6](https://github.com/hariharanhh/100-Points-Description-Leaderboard-Deploying-wordpress-on-AWS/assets/110392389/4901a11b-b32d-404a-bea8-5ede63b5aee0)
