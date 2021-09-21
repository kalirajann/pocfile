## PreRequisite:

- AKS Cluster(1.21)
- Azure Storage (File with privatelink)
- UAMI (Connects Cluster & Storage)
- UAMI Roles (Reader/Contributer)

## Manifest

- Creates storage class (Provisioner -> file.csi.azure.com)
- creates PVC
- Deployment creates single POD (Facing mounting issue)

##### Error

```
default     36s         Warning   FailedMount             pod/myakspodcsi                        MountVolume.MountDevice failed for volume "pvc-b6f6e2f3-3c9e-4967-96e6-be5a0e6a4254" : rpc error: code = Internal desc = volume(ubs#ubskalistorage#pvc-b6f6e2f3-3c9e-4967-96e6-be5a0e6a4254#) mount "//ubskalistorage.privatelink.file.core.windows.net/pvc-b6f6e2f3-3c9e-4967-96e6-be5a0e6a4254" on "/var/lib/kubelet/plugins/kubernetes.io/csi/pv/pvc-b6f6e2f3-3c9e-4967-96e6-be5a0e6a4254/globalmount" failed with mount failed: exit status 1
Mounting command: mount
Mounting arguments: -t cifs -o dir_mode=0777,file_mode=0777,uid=0,gid=0,mfsymlinks,cache=strict,nosharesock,actimeo=30,<masked> //ubskalistorage.privatelink.fOutput: mount error: could not resolve address for ubskalistorage.privatelink.file.core.windows.net: Unknown error

default     6m49s       Normal    Scheduled               pod/myakspodcsi                        Successfully assigned default/myakspodcsi to aks-agentpool-93675800-vmss000002


default     14s         Warning   FailedMount             pod/myakspodcsi                        Unable to attach or mount volumes: unmounted volumes=[volume], unattached volumes=[volume kube-api-access-ltnbd]: timed out waiting for the condition
```
