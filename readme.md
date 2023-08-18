<a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-purple.svg?labelColor=303030" /></a>
<br />

## About The Project
<div>
  <a href="https://raw.githubusercontent.com/h1zardian/cluster-provisioning-pipeline/main/docs/app-pipeline.png">
  <img src="https://raw.githubusercontent.com/h1zardian/cluster-provisioning-pipeline/main/docs/app-pipeline.png">
  </a>
</div>

</br>

> **Detailed Pipeline Workflow**
>
> 1. **Initiating the Development Environment**: The software developer accesses a specially prepared development environment. This virtual container has all the necessary tools, packages, and settings pre-configured to facilitate the creation of the software pipeline.
>
> 2. **Application Cluster Provisioning**: Through the use of a scripted process called an Ansible playbook, the developer commands the creation of the application environment within Amazon's Kubernetes Service (EKS).
>
> 3. **Applying Infrastructure Changes**: Using a common automation tool named Terraform, the playbook provisions the necessary resources on AWS, including the EKS cluster and associated databases.
>
> 4. **Cluster Configuration**: Terraform connects to AWS and assembles the different parts required for the software to operate in unison.
>
> 5. **Deployment Configuration**: Using Ansible, the playbook updates essential configuration files (kubeconfig) and utilizes the Helm tool to install various software packages on the cluster.
>
> 6. **Finalizing Deployment Elements**: Helm takes charge of finalizing the deployment, including configuring storage volumes, essential settings, and security measures.
>
> 7. **Launching the Application**: Finally, the EKS cluster retrieves the container image from Docker Hub and brings the software to life, creating the necessary instances to serve users and ensure smooth operation.

## How to Use
Update the variables in the terraform `.tfvars` file and both the `user-values.yaml` files inside the helm-charts directory.

Check if the aws access key is present in the `~/.aws/credentials` file. If not, create the access key for your IAM user and add it to the file.

Add the ec2 key-pair file in the ansible folder.  
e.g: build-pipeline-ec2.key

Change the permission of the key-pair file to 600
```bash
chmod 600 build-pipeline-ec2.key
```

Check the `ansible.cfg` file and change the `private_key_file` to the key file name.

Execute the ansible playbook
```bash
ansible-playbook playbooks/application-pipeline.yml
```

When the playbook is executed successfully, copy the load balancer endpoint from the output and access the django app.

### Destroy the Terraform Resources
To destroy the terraform provisioned resources, change directory to `terraform/buildah-server` and execute the following command
```bash
terraform destroy --auto-approve
```
> Note: The loadbalancer is not destroyed by the terraform script. You have to manually terminate the loadbalancer from the AWS console.
