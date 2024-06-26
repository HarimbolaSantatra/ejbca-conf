# DEPLOY EJBCA QUICKLY USING ANSIBLE AND TERRAFORM
Run a production-ready [EJBCA docker container][1] using Terraform and a Nginx reverse proxy.
Other deployement scenario are covered elsewhere:
- [Using an external database][1]
- [Using httpd proxy](https://github.com/Keyfactor/keyfactorcommunity/tree/main/deployment-examples/docker-engine/ejbca-ce-three-level-architecture)

Full instruction for the docker container can be found on [Docker Hub][1].


## Prerequisites
For this example you will need:
- [Nginx](http://nginx.org/) reverse proxy as a front-end. The *main.yaml* playbook install Nginx if it's not installed yet.
- [Terraform](https://developer.hashicorp.com/terraform/install)

## Setup 
### Clone
```
git clone https://github.com/HarimbolaSantatra/ejbca-terraform.git
cd ejbca-terraform
```

### Setup your own terraform and ansible variable
```
cp example.tfvars.sample production.tfvars
cp inventory.ini.sample inventory.ini
```

### Deploy 🚀
```
ansible-playbook -i inventory.ini main.yaml -K
terraform init .
terraform apply -var-file production.tfvars
```

---

[1]: https://hub.docker.com/r/keyfactor/ejbca-ce
[2]: https://github.com/Keyfactor/ejbca-ce
