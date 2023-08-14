<a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-purple.svg?labelColor=303030" /></a>
<br />

## About The Project

<div>
  <a href="https://raw.githubusercontent.com/h1zardian/cluster-provisioning-pipeline/main/docs/app-pipeline.png">
  </a>
</div>

This project is a pipeline for provisioning a Kubernetes cluster on AWS. It uses Terraform to create the infrastructure and Ansible to configure the cluster. The pipeline is built with GitHub Actions and is triggered on push to the main branch. The pipeline is also triggered on pull requests to the main branch. The pipeline is configured to run on a self-hosted runner. The runner is a t2.micro EC2 instance running Ubuntu 20.04. The runner is provisioned with Terraform and Ansible. The runner is configured to run the pipeline on a schedule. The pipeline is configured to run every 30 minutes.