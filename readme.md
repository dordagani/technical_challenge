# The actions to be performed by the playbook

1.	Create a Security Group which only allows access from the following: 
    • Inbound - Your IP address (SSH, HTTP); Ansible IP address (SSH)
    • Outbound – HTTPS & HTTP to any IP address

2.	Launches a Linux instance from an AMI (Centos 7 - t2.micro) and assign it with the Security Group

3.	Add a tag EnvName with the value “Test Environment”

4.	Deploy a Linux web-application (Apache)

5.	Present a web-page that is showing the IP address of the local IP address of machine on which it is running and have the web-app to listen on port 80

# Instructions for running the playbook

1.  Add a dedicated user for Ansible :
    ```
    sudo adduser ansible
    ```
    
2.  Set a password for the user :
    sudo passwd ansible

3.  Add sudo privileges to the user:
    sudo usermod -aG wheel ansible

4.  Log in with the user Ansible:
    sudo su - ansible

5.  Install wget, python, boto and boto3 :
    sudo yum install -y python-pip wget
    sudo pip install boto boto3

6.  Create encrypted file that will contain the keys to aws and the ec2 region :
    ansible-vault create aws_keys.yml

    Enter the following values ​​(enter your keys):
    AWS_ACCESS_KEY_ID: <your_aws_access_key_id>
    AWS_SECRET_ACCESS_KEY: <your_aws_secret_access_key>
    AWS_REGION: us-east-1

7.  Download the playbook from github using wget:



8.  Run the playbook with the following command:
    ansible-playbook --ask-vault-pass instance_prov.yaml
