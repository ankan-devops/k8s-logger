# k8s-logger
CLI logger for K8s clusters to display container logs of deployments. Intended for developers.
============================================================================

## Prequisities for EKS Cluster Admin:

### Creating AWS users and adding RBAC rules for the users on K8s to view container logs:-

1. In AWS EKS create a CLI user with **eks:DescribeCluster** policy
2. Create Access & secret key for the user.
3. Edit the EKS configmap  and add the user in k8s using eksctl cmd-line
> eksctl create iamidentitymapping --cluster <Cluster name> --region=<region-code> --_<replace with user arn>_ --username _<replace with user-name>_
4. Edit the kustomization.yaml wuth:
    * Namespace for the users to access
    * Namespace suffix on the Role and role binding
    * The name of the AWS user added on k8s configmap to view the logs
5. Finally, run 'kubectl apply -k <path to this folder>'
===========================================================================

## Setting up the Logger on User/Developer end

### Variables needed:
* AWS Access Key with 'eks:DescribeCluster' policy
* AWS Secret Key
* AWS Refion of the EKS Cluster
* AWS EKS Cluster name
* K8S Namespace to be given access to the user

### Setting up the Logger

1. Install **Docker** on the machine
2. Run the **./k8s-logger** bash file
3. Enter the values asked for in the cmd-line prompts

## Running the Logger

1. Run the command ***sudo docker run -it --rm k-logs***
2. Enter the namespace the user/developer will access
3. Enter the number from the list of pods to view it's logs
========================================================================