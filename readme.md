# EJBCA DOCKER CONTAINER TEMPLATE
Run a production-ready [EJBCA docker container][1] using *Terraform* and a Nginx reverse proxy. Optionally, setup the nginx reverse proxy with *ansible*.

Other deployement scenario are covered elsewhere:
- [Using an external database][1]
- [Using httpd proxy](https://github.com/Keyfactor/keyfactorcommunity/tree/main/deployment-examples/docker-engine/ejbca-ce-three-level-architecture)

Full instruction for the docker container can be found on [Docker Hub][1].


## Prerequisites
For this example you will need:
- [Nginx](http://nginx.org/) reverse proxy as a front-end. Use *main.yaml* ansible playbook to install and setup Nginx if it's not installed yet.
- [Terraform](https://developer.hashicorp.com/terraform/install)
- [Ansible](https://docs.ansible.com/) (Optional)

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

## Features
- [ ] Support nginx container and bare metal installation

---

## Resources
- [EJBCA Community Edition][2]
- [Mariadb container][3]

[1]: https://hub.docker.com/r/keyfactor/ejbca-ce
[2]: https://github.com/Keyfactor/ejbca-ce
[3]: https://hub.docker.com/_/mariadb
