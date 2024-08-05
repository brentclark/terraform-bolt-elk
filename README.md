# terraform-bolt-elk
# ELK
A terraform and bolt solution. It creates an ELK-like infrastructure.

Deploy node comes with bolt installed, required keys to ssh to nodes and a generated inventory.

./newKeys.sh. It will generate two keypairs - Admin and Ansible - named so, accordingly to tf code.

Check /opt/terraform folder on your deploy node, it's a starting point to your bolt automation.

## Lab requirements on your client station :
 - packages : git, terraform, openstack-cli (optionnal)
 - {home}/.config/openstack/clouds.yaml holding your tenants credentials and URL

## Tenant :
 - a public network with a FIP pool
 - enough vCPU, storage, secgroup, RAM in quotas

## How to :
Set variables : Read and use terraform.tfvars.sample :
 - copy terraform.tfvars.sample to terraform.tfvars
 - edit terraform.tfvars variables as needed

Launch terraform
 - terraform init
 - terraform plan
 - terraform apply

Debug your HCL code, evaluate your plan contents, etc...
 - terraform console

Renew your public/private key pairs
 - ./newKeys.sh Warning! if you have a running or created infrastructure, keep a safe copy of AnsibleKey.pem and AdminKey.pem

```
# mandatory values
cloud = "mycloud"

# optional values
publicNetwork = "my_public_net"
infraName = "lnpp"
useTenantImage = false
operatingSystem ="debian"
nbWebNodes= 3
nbDBNodes = 2
```
## TODO:
 - internal lb 
