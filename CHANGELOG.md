# Changelog
## pre 1.0.0

### 0.8.1

- add default resource requests and limits for initIP container
- add default resource requests and limits for pingExporter container
- change pcap container image to version `1.0.1` for a bugfix

### 0.8.0

- add support for Router Advertisement Daemon (radvd)
- add support for pcap capturing using *tshark*
- change *ping-exporter* to version 0.5.0

### 0.7.0

- change name of ipsec container
- add flag to enable ipsec component
- add documentation for using `iptables` with CGW
- add support for certificate based VPN
- add support for using VRRP for internal router redundancy [alpha]
- update version of `vnf-ipsec` to `1.3.1` to fix problem with enabled
  `farp` plugin
- [breaking] update VXLAN-Controller to use image from new docker repository and
  use corresponding annotations
  - from `aialferov/kube-vxlan-controller-agent` to `openvnf/kube-vxlan-controller-agent`
  - If the default settings have been used on current clusters, the value file has to be changed to set the old names explicitly
- [bugfix] strongswan configmap will not be created, if ipsec is disabled
- [bugfix] pingExporter configmap will not be created, if pingExporter is disabled
- add `selector` to deployment spec, which is required in newer versions of Kubernetes and encouraged in older ones
  - see <https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#selector>
- disable `init-ip` init container to set local ping endpoint if `ipsec` is not enabled
- update vnf-ipsec to 1.4.0
  - also fixes *CVE-2018-17540*
- add parameter for additional pod annotations

### 0.6.0

- add flag to use manual configuration for ipsec-config of Strongswan
- add usage of iptables container to firewall pod, disabled by default
- add flag to disable ping-prober if not needed or ping-exporter is used
- add debug container as first container including networking tools
- add init script container to run custom initialization
- add BIRD as BGP daemon
- add bird_exporter to expose BIRD metrics in prometheus format
- add checksums of configmaps and secrets to deployment to redeploy and restart
  them when the configuration changes

### 0.5.0

- add configurable keys for vxlan controller annotations
- add ping-exporter to expose metrics for ICMP Echo requests
- add feature to set static IP addresses outside of the scope of
  vxlan-controller
- add option to disable usage of VTI interfaces for IPSEC

### 0.4.0
-  add cgw-exporter to expose ICMP echo metrics for the service
