# Persistent Volume File Share - AKS POD

Steps to implement the File share mount based on AKS Managed user Identity

- Create AKS Cluster with Managed identity
- Create user managed identity
- Assign the identity with AKS Cluster
  `az aks update -g aksdemo -n ManagedClusterTesting --enable-managed-identity --assign-identity {identity ResourceID}`
- Create Storage Account with File Share.
- Assign RBAC Roles to UAM to access the Storage account using kubectl
  `Reader, Storage Account Key Operator Service Role, Storage File Data SMB Share Contributor`
- Apply the manifests
- Test the mount in newly created mount.
