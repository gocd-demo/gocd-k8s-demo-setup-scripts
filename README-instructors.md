# Setup a set of k8s clusters for GoCD workshop participants

  ```bash
  ./setup --help
  ```

  The above command will setup a specified number of cluster in GKE. It will also create files `~/.gocd-demo/${CLUSTER_PREFIX}/${INDEX}/kube/config` for each participant in the workshop. Each participant needs to have a copy of one of the files and they should save it under `~/.kube/config` on their computers.

  They should also ensure that they have helm and kubectl installed on their computers. Binaries for all platforms are available on GitHub.

# Tear down the k8s clusters

  ```bash
  ./teardown --help
  ```
