# Setting up and configuring GoCD on k8s

1. Ensure that you download and install kubectl. See [this link](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-on-linux) for instructions.
2. Copy the kubectl config file to `$HOME/.kube/config`. If the file already exists file there, set the variable `export KUBECONFIG=/path/to/kube/config`
3. Install GoCD via helm

    ```
    helm install --name gocd-app --namespace gocd stable/gocd
    ```

4. Follow instructions after helm install to get your GoCD server IP address

    ```
    echo "GoCD server public IP: http://$(kubectl get ingress gocd-app-server --namespace=gocd  -o jsonpath='{.status.loadBalancer.ingress[0].ip}')"
    ```