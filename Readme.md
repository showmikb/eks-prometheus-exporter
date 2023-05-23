# Installing and Deploying Node Exporter in Kubernetes

This guide provides step-by-step instructions on how to install and deploy the Node Exporter in a Kubernetes cluster using Ansible.

## Prerequisites

Before proceeding, ensure you have the following prerequisites:

- Ansible installed on your local machine.
- Access to a Kubernetes cluster with the necessary permissions.

## Instructions

1. Clone the repository:

   ```bash
   git clone <repository_url>
    ```

2. Navigate to the cloned repository:

```
cd <repository_directory>
```


3. Edit the Ansible playbook file install_node_exporter.yaml to customize any variables or settings as per your requirements.

Run the Ansible playbook:

```
ansible-playbook install_node_exporter.yaml
```

This playbook will install the Node Exporter using the package manager, create a namespace, deploy the Node Exporter as a pod within the namespace, wait for the pod to be in the "Running" state, check the Node Exporter metrics, and print the metrics.

4. Verify the installation:

After the playbook execution is complete, you can verify the installation by accessing the Node Exporter metrics endpoint. Assuming the Kubernetes cluster is accessible from your local machine, run the following command:

```
kubectl port-forward -n node-exporter pod/node-exporter 9100:9100
```


Note: Keep the port-forwarding command running in a separate terminal while you want to access the metrics. Press Ctrl+C to stop port-forwarding.

Cleanup (Optional):

If you want to remove the deployed Node Exporter, run the following command:
```
kubectl delete -n node-exporter pod/node-exporter
```
This will delete the Node Exporter pod.

