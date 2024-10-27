Optional: Create custom storage class for the PVC

```bash
kubectl apply -f storage-class.yaml
```

```yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: gp3
provisioner: ebs.csi.aws.com
volumeBindingMode: WaitForFirstConsumer
parameters:
  type: gp3
  fsType: ext4
  # Optional: Specify IOPS and throughput if needed
  # iops: "3000"  # Default is 3000 for gp3
  # throughput: "125"  # Default is 125 MiB/s for gp3
```

We choose to use default StorageClass when provisioning EKS v1.30. Default StorageClass is gp2.
