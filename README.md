# Role: k3s

Configure k3s on a single node in rootless mode or as a cluster in root mode.

## Configuration
| Variable                | Default vaule   | Description                                                           |
|-------------------------|-----------------|-----------------------------------------------------------------------|
| `k3s_cluster`           | `False`         | Whether to enable clustering support                                  |
| `k3s_cluster_cidr`      | `10.42.0.0/16`  | CDIR to use for K8S cluster network                                   |
| `k3s_service_cidr`      | `10.43.0.0/16`  | CIDR to use for K8S service IPs                                       |
| `k3s_cluster_domain`    | `cluster.local` | Cluster domain to use for K8S                                         |
| `k3s_cluster_dns`       | `10.43.0.10`    | Address of the DNS service inside K8S (must be in `k3s_service_cidr`) |
| `k3s_root`              | `False`         | Whether to run K3S as root (applicable to single-node only)           |
| `k3s_feature_toggles`   | `""`            | Extra feature toggles to set (passed as CLI arguments)                |
| `k3s_cluster_secret`    | `unset`         | Secret to use for joining nodes in cluster mode                       |
| `k3s_cluster_init_node` | `unset`         | Node to use for bootstrapping a cluster (FQDN)                        |


This role unfortunately is quite invasive:
 * It will enable cgroups v2. This requires a reboot, if a reboot is required it'll fail the playbook
 * It will enable cgroup delegation for more than just the default controllers
 * It enables IPv4 forwarding

**Compatibility tested with:**
  * Debian 11

## License
GPLv3
