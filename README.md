# Role: k3s

Configure k3s on a single node

## Configuration
| Variable             | Default vaule   | Description                                                           |
|----------------------|-----------------|-----------------------------------------------------------------------|
| `k3s_cluster`        | `False`         | Whether to enable clustering support (currently not implemented)      |
| `k3s_cluster_cidr`   | `10.42.0.0/16`  | CDIR to use for K8S cluster network                                   |
| `k3s_service_cidr`   | `10.43.0.0/16`  | CIDR to use for K8S service IPs                                       |
| `k3s_cluster_domain` | `cluster.local` | Cluster domain to use for K8S                                         |
| `k3s_cluster_dns`    | `10.43.0.10`    | Address of the DNS service inside K8S (must be in `k3s_service_cidr`) |


This node unfortunately is quite invasive:
 * It will enable cgroups v2. This requires a reboot, if a reboot is required it'll fail the playbook
 * It will enable cgroup delegation for more than just the default controllers
 * It sets up strongswan in preparation for clustering

**Compatibility tested with:**
  * Debian 11

## License
GPLv3
