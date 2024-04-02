# PHASE-1 | Setup Repo

# Fork the Repo

1.	Navigate to the Repository: Go to the repository you want to fork. This can be done through the platform's search feature or by directly accessing the repository's URL.

2.	Locate the Fork Button: Look for the "Fork" button on the repository's page. This button is usually located in the top-right corner of the page. Click on it.

3.	Choose the Destination: When you click on the "Fork" button, you'll be prompted to choose where you want to fork the repository. This is typically your personal account or an organization you belong to. Select the appropriate destination.

4.	Wait for the Fork to Complete: The platform will start the forking process, creating a copy of the repository under your account. Depending on the size of the repository, this process may take a few moments.

# PHASE-2 | Infra Setup

# Setting Up Kubernetes Cluster on AWS EC2 Instances

# 1.	Creating VMs:

•	Log in to the AWS Management Console.

•	Navigate to the EC2 dashboard.

•	Click on "Launch Instance".

•	Choose an Amazon Machine Image (AMI), select the appropriate instance type

(t2.medium), configure instance details, add storage (20GB), and configure security groups to allow SSH access.

•	Repeat the above steps to create the second VM.

# 2.	Connecting to VMs via SSH(using Mobaexterm or any other Terminal):

•	Use an SSH client like mobaxterm (for Windows) or Terminal (for macOS/Linux) to connect to the VMs using their public IP addresses and SSH key pair.

# 3.	Updating Packages:
````
sudo apt update && sudo apt upgrade -y
```
# 4. Create and Execute Script on Both Master & Worker VM:

# Script (setup.sh):
````
sudo apt install docker.io -y

sudo chmod 666 /var/run/docker.sock

sudo apt-get install -y apt-transport-https ca-certificates curl gnupg sudo mkdir -p -m 755 /etc/apt/keyrings

curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.28/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg

echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.28/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list

sudo apt update

sudo apt install -y kubeadm=1.28.1-1.1 kubelet=1.28.1-1.1 kubectl=1.28.1-1.1
````
