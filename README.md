# Setting up and configuring GoCD on k8s

## Prerequisites

1. Ensure that you have an SSH client installed on your machine. If you are running on linux or macOS, you probably already have it installed. If you're running on Windows, see [this link](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).
2. SSH into the remote host using the credentials given to you. This host has `kubectl` and `helm` preinstalled for your convenience.

    ```bash
    ssh user-${N}@ip.add.re.ss
    ```

3. Run `kubectl get nodes` to make sure everything works as expected.

## Install GoCD on the k8s cluster

1. Setup GoCD using the helm chart:

    ```shell
    helm install --name gocd --namespace gocd stable/gocd
    ```
