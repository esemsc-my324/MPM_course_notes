2024.10.15

# The Cloud and Countinuous Integration

## Public Cloud and Private Cloud

### Public Cloud

- Microsoft Azure 
- Amazon AWS
- Goolge Cloud Service
- Alibaba cloud

### Private Cloud

Full infrastructure is purchased and controlled by the company. Have fully controlled over hardware, policy and configuration.

e.g. College HPC clusters

### Hybrid Cloud

In principle, this allows the organization to combine the control and intellectual property advantages of private cloud with the availability and scalability advantages of the public cloud.

## Infrastructure, Platform and Software as a Service

### Iaas

You purchase time on a entire computer or a virtual machine, then set up the entire system from scratch.

### Paas

The Provider configures the core OS and programming environment, leave use only focus on code writing for the actual application.

### SaaS

Download APP and use.

## Setting Up VM

Copy the `Public IP Address`

20.120.181.220

```bash
# connect to the server
ssh my324@20.120.181.220
# enter the password

# open the HTTP port
sudo python3 -m http.server 80
# then the VM can be accessed via Browser

sudo apt update && sudo apt upgrade -y
sudo apt install python3-pip

export PATH=./local/bin:$PATH  ## append the path to the $PATH variable

# Create a new venv to install jupyer notebook
sudo apt install python3-venv
python3 -m venv ~/jupyterhub
source ~/jupyterhub/bin/activate

# Install packages
pip install jupyter-core jupyterhub notebook
sudo apt install npm
sudo npm install -g configurable-http-proxy

# make allowence to use port 8080
sudo ufw allow 8080

# open jupyter notebook
```

