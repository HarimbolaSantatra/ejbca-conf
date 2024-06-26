# DEPLOY EJBCA QUICKLY USING TERRAFORM
Run a production-ready [EJBCA docker container][1] using Terraform, an external MariaDB database and a Nginx reverse proxy.
Other deployement scenario are covered elsewhere:
- [Using docker database](https://docs.keyfactor.com/ejbca/latest/tutorial-start-out-with-ejbca-docker-container) with compose
- [Using httpd proxy](https://github.com/Keyfactor/keyfactorcommunity/tree/main/deployment-examples/docker-engine/ejbca-ce-three-level-architecture)

Docker container environment variables:
- `TLS_SETUP_ENABLED=later`
- `PROXY_HTTP_BIND`

Full instruction for the docker container can be found on [Docker Hub][1].

## Prerequisites
For this example you will need:
- [Nginx](http://nginx.org/) reverse proxy as a front-end
- External [MariaDB](https://mariadb.com/) database
- [Terraform](https://developer.hashicorp.com/terraform/install)

## Setup 
```
git clone https://github.com/Keyfactor/keyfactorcommunity.git
cd keyfactorcommunity/deployement-examples/terraform
```

Copy and edit the nginx configuration file:
```
cp mysite /etc/sites-available
ln -s /etc/sites-available/mysite /etc/sites-enabled
nginx -s reload
```

Setup your own terraform variable:
```
cp example.tfvars.sample production.tfvars
```

Deploy 🚀:
```
terraform init .
terraform apply -var-file production.tfvars
```

---

[1]: https://hub.docker.com/r/keyfactor/ejbca-ce
[2]: https://github.com/Keyfactor/ejbca-ce
