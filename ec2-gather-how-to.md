1. Login to your ec2 instance, create your playbook
2. Let's put your ec2.py in same directory also ec2.private-ip.ini
cp ec2.py ec2.private-ip.ini ~/provisioning/
3. Let's test add some information for it

export ANSIBLE_HOST_KEY_CHECKING=False

export EC2_INI_PATH=./ec2.private-ip.ini

export AWS_ACCESS_KEY={your aws access key}

export AWS_SECRET_KEY={your aws secret key}</code>

~/provisioning/ec2.py --refresh-cache

ansible-playbook -i local, provisioning/ec2-gather.yml --extra-vars="aws_access_key=$AWS_ACCESS_KEY aws_secret_key=$AWS_SECRET_KEY" -vvvv
