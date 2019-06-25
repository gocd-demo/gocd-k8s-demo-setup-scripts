# Setting up and configuring GoCD on k8s

## Prerequisites

1. Ensure that you have an SSH client installed on your machine. If you are running on linux or macOS, you probably already have it installed. If you're running on Windows, see [this link](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).
2. SSH into the remote host using the credentials given to you. This host has `kubectl` and `helm` preinstalled for your convenience.

    ```bash
    ssh user-${N}@ip.add.re.ss
    ```

3. Run `kubectl get nodes` to make sure everything works as expected.

## To get access to the kubernetes dashboard

1. Run the following (on remote machine) command get your API token to login to the k8s dashboard. Copy this key to a file on your local machine, you'll need it to login for step 3.

    ```bash
    kubectl -n kube-system describe secrets $(kubectl -n kube-system get secrets | grep kubernetes-dashboard-token | awk '{print $1}')
    ```
2. In a separate window on your local machine run the following command (choose a random port for your needs). This will open the kubernetes dashboard on the port specified by `RANDOM_PORT`.

    ```bash
    ssh -L ${RANDOM_PORT}:localhost:${RANDOM_PORT} user-${N}@ip.add.re.ss /snap/bin/kubectl proxy -p ${RANDOM_PORT}
    ```

3. Open the dashboard by opening [this link](http://localhost:12344/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/#!/overview?namespace=default). Substitute the port number in the URL.


## Install GoCD on the k8s cluster

1. Setup GoCD using the helm chart:

    ```
    helm install --name gocd-app --namespace gocd stable/gocd
    ```