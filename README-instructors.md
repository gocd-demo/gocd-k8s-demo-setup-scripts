# Setup a set of k8s clusters for GoCD workshop participants

  ```bash
  ./setup --help
  ```

  The above command will setup a specified number of cluster in GKE. It will also create an SSH "jump box" with usernames `user-1...user-N` pre-configured. The password for each of the users is `123456789`. All participants should login using different usernames to avoid stepping on each other's shoes.

# Tear down the k8s clusters

  ```bash
  ./teardown --help
  ```
