### Initial Installation talos

[Talos Initial Installation](https://factory.talos.dev/?arch=amd64&board=undefined&cmdline-set=true&extensions=-&extensions=siderolabs%2Fi915&extensions=siderolabs%2Fintel-ucode&platform=nocloud&secureboot=undefined&target=cloud&version=1.10.4)

```
talosctl gen config talos-proxmox-cluster https://192.168.1.54:6443 --output-dir _out --install-image factory.talos.dev/nocloud-installer/4b3cd373a192c8469e859b7a0cfbed3ecc3577c4a2d346a37b0aeff9cd17cdb0:v1.10.4
```

![](/images/Screenshot%202025-06-26%20at%2012.15.29 PM.png)

### Create Control Plane Node

```
talosctl apply-config --insecure --nodes $CONTROL_PLANE_IP --file _out/controlplane.yaml
```

### Create Worker Node

```
talosctl apply-config --insecure --nodes $WORKER_IP --file _out/worker.yaml

```

### Using the Cluster

```
export TALOSCONFIG="_out/talosconfig"
```

```
talosctl config endpoint $CONTROL_PLANE_IP
talosctl config node $CONTROL_PLANE_IP
```

### Bootstrap Etcd
```
talosctl bootstrap

```
### Retrieve the kubeconfig

```
talosctl kubeconfig .

```

![](/images/Screenshot%202025-06-26%20at%2012.40.04 PM.png)

