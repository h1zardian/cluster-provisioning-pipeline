<a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-purple.svg?labelColor=303030" /></a>
<br />

## About The Project
<div>
  <a href="https://raw.githubusercontent.com/h1zardian/cluster-provisioning-pipeline/main/docs/app-pipeline.png">
  <img src="https://raw.githubusercontent.com/h1zardian/cluster-provisioning-pipeline/main/docs/app-pipeline.png">
  </a>
</div>

## How to Use
Update the variables in the terraform `.tfvars` file and both the `user-values.yaml` files inside the helm-charts directory.

Add the ec2 key file in the ansible folder.  
e.g: build-pipeline-ec2.key

Change the permission of the key file to 600
```bash
$ chmod 600 build-pipeline-ec2.key
```

Check the `ansible.cfg` file and change the `private_key_file` to the key file name.

Execute the ansible playbook
```bash
$ ansible-playbook playbooks/application-pipeline.yml
```

When the playbook is executed successfully, copy the load balancer endpoint from the output and access the django app.

#### Destroy the Terraform Resources
To destroy the terraform provisioned resources, change directory to `terraform/buildah-server` and execute the following command
```bash
$ terraform destroy --auto-approve
```
> Note: The loadbalancer is not destroyed by the terraform script. You have to manually terminate the loadbalancer from the AWS console.
