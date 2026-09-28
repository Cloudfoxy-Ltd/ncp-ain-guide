
# Appendix A — helix-b-air.json

Save this as `helix-b-air.json` and import it in Lab 0, Task 3. It is also on the companion site (https://cloudfoxy-ltd.github.io/ncp-ain-guide/).

```
{
  "format": "JSON",
  "title": "helix-b-air",
  "ztp": null,
  "content": {
    "nodes": {
      "hxb-spine01": {"cpu": 2, "memory": 4096, "storage": 20, "os": "cumulus-vx-5.16.1"},
      "hxb-spine02": {"cpu": 2, "memory": 4096, "storage": 20, "os": "cumulus-vx-5.16.1"},
      "hxb-leaf-r1": {"cpu": 2, "memory": 4096, "storage": 20, "os": "cumulus-vx-5.16.1"},
      "hxb-leaf-r2": {"cpu": 2, "memory": 4096, "storage": 20, "os": "cumulus-vx-5.16.1"},
      "hxb-leaf-r3": {"cpu": 2, "memory": 4096, "storage": 20, "os": "cumulus-vx-5.16.1"},
      "hxb-leaf-r4": {"cpu": 2, "memory": 4096, "storage": 20, "os": "cumulus-vx-5.16.1"},
      "hxb-gpu01": {"cpu": 2, "memory": 4096, "storage": 20, "os": "generic/ubuntu2404"},
      "hxb-gpu02": {"cpu": 2, "memory": 4096, "storage": 20, "os": "generic/ubuntu2404"},
      "hxb-gpu03": {"cpu": 2, "memory": 4096, "storage": 20, "os": "generic/ubuntu2404"},
      "hxb-gpu04": {"cpu": 2, "memory": 4096, "storage": 20, "os": "generic/ubuntu2404"},
      "hxa-ibsim": {"cpu": 2, "memory": 2048, "storage": 10, "os": "generic/ubuntu2404"}
    },
    "links": [
      [{"node": "hxb-leaf-r1", "interface": "swp31"}, {"node": "hxb-spine01", "interface": "swp1"}],
      [{"node": "hxb-leaf-r1", "interface": "swp32"}, {"node": "hxb-spine02", "interface": "swp1"}],
      [{"node": "hxb-leaf-r2", "interface": "swp31"}, {"node": "hxb-spine01", "interface": "swp2"}],
      [{"node": "hxb-leaf-r2", "interface": "swp32"}, {"node": "hxb-spine02", "interface": "swp2"}],
      [{"node": "hxb-leaf-r3", "interface": "swp31"}, {"node": "hxb-spine01", "interface": "swp3"}],
      [{"node": "hxb-leaf-r3", "interface": "swp32"}, {"node": "hxb-spine02", "interface": "swp3"}],
      [{"node": "hxb-leaf-r4", "interface": "swp31"}, {"node": "hxb-spine01", "interface": "swp4"}],
      [{"node": "hxb-leaf-r4", "interface": "swp32"}, {"node": "hxb-spine02", "interface": "swp4"}],
      [{"node": "hxb-leaf-r1", "interface": "swp1"}, {"node": "hxb-gpu01", "interface": "eth1"}],
      [{"node": "hxb-leaf-r2", "interface": "swp1"}, {"node": "hxb-gpu01", "interface": "eth2"}],
      [{"node": "hxb-leaf-r1", "interface": "swp2"}, {"node": "hxb-gpu03", "interface": "eth1"}],
      [{"node": "hxb-leaf-r2", "interface": "swp2"}, {"node": "hxb-gpu03", "interface": "eth2"}],
      [{"node": "hxb-leaf-r3", "interface": "swp1"}, {"node": "hxb-gpu02", "interface": "eth1"}],
      [{"node": "hxb-leaf-r4", "interface": "swp1"}, {"node": "hxb-gpu02", "interface": "eth2"}],
      [{"node": "hxb-leaf-r3", "interface": "swp2"}, {"node": "hxb-gpu04", "interface": "eth1"}],
      [{"node": "hxb-leaf-r4", "interface": "swp2"}, {"node": "hxb-gpu04", "interface": "eth2"}]
    ],
    "oob": {"nodes": {"oob-mgmt-server": {"cpu": 2, "memory": 4096, "storage": 20}}}
  }
}
```

## Resource budget

| Nodes | Count | vCPU each | Memory each | Total vCPU | Total memory |
|---|---|---|---|---|---|
| Cumulus VX switches (20 GB disk each, Air's minimum) | 6 | 2 | 4 GiB | 12 | 24 GiB |
| Ubuntu GPU servers | 4 | 2 | 4 GiB | 8 | 16 GiB |
| hxa-ibsim | 1 | 2 | 2 GiB | 2 | 2 GiB |
| oob-mgmt-server | 1 | 2 | 4 GiB | 2 | 4 GiB |
| oob-mgmt-switch | 1 | set by Air | set by Air | ~1–2 | ~1–2 GiB |
| **Total** | | | | **about 26** | **about 48 GiB** |

This fits the free trial's 60 vCPU / 60 GiB concurrent limits. You can't run two copies at once; sleep one before starting another (Lab 6).

# Appendix B — helix-a.net (InfiniBand simulator fabric)

Used in Lab 8. Save as `~/ibsim/helix-a.net` on hxa-ibsim. The first node listed hosts the master SM.

```
# Helix-A mini InfiniBand fabric for ibsim (NCP-AIN Lab Guide)
# The first node listed hosts the Subnet Manager (the UFM server).

Hca	1 "hxa-ufm-a1 mlx5_0"
[1]	"hxa-su1-leaf-r1"[30]

Switch	36 "hxa-spine01"
[1]	"hxa-su1-leaf-r1"[33]
[2]	"hxa-su1-leaf-r2"[33]
[3]	"hxa-su2-leaf-r1"[33]
[4]	"hxa-su2-leaf-r2"[33]

Switch	36 "hxa-spine02"
[1]	"hxa-su1-leaf-r1"[34]
[2]	"hxa-su1-leaf-r2"[34]
[3]	"hxa-su2-leaf-r1"[34]
[4]	"hxa-su2-leaf-r2"[34]

Switch	36 "hxa-su1-leaf-r1"
[1]	"hxa-gpu01 mlx5_0"[1]
[2]	"hxa-gpu02 mlx5_0"[1]
[30]	"hxa-ufm-a1 mlx5_0"[1]
[33]	"hxa-spine01"[1]
[34]	"hxa-spine02"[1]

Switch	36 "hxa-su1-leaf-r2"
[1]	"hxa-gpu01 mlx5_1"[1]
[2]	"hxa-gpu02 mlx5_1"[1]
[33]	"hxa-spine01"[2]
[34]	"hxa-spine02"[2]

Switch	36 "hxa-su2-leaf-r1"
[30]	"hxa-ufm-a2 mlx5_0"[1]
[1]	"hxa-gpu03 mlx5_0"[1]
[2]	"hxa-gpu04 mlx5_0"[1]
[33]	"hxa-spine01"[3]
[34]	"hxa-spine02"[3]

Switch	36 "hxa-su2-leaf-r2"
[1]	"hxa-gpu03 mlx5_1"[1]
[2]	"hxa-gpu04 mlx5_1"[1]
[33]	"hxa-spine01"[4]
[34]	"hxa-spine02"[4]

Hca	1 "hxa-gpu01 mlx5_0"
[1]	"hxa-su1-leaf-r1"[1]

Hca	1 "hxa-gpu01 mlx5_1"
[1]	"hxa-su1-leaf-r2"[1]

Hca	1 "hxa-gpu02 mlx5_0"
[1]	"hxa-su1-leaf-r1"[2]

Hca	1 "hxa-gpu02 mlx5_1"
[1]	"hxa-su1-leaf-r2"[2]

Hca	1 "hxa-gpu03 mlx5_0"
[1]	"hxa-su2-leaf-r1"[1]

Hca	1 "hxa-gpu03 mlx5_1"
[1]	"hxa-su2-leaf-r2"[1]

Hca	1 "hxa-gpu04 mlx5_0"
[1]	"hxa-su2-leaf-r1"[2]

Hca	1 "hxa-gpu04 mlx5_1"
[1]	"hxa-su2-leaf-r2"[2]

Hca	1 "hxa-ufm-a2 mlx5_0"
[1]	"hxa-su2-leaf-r1"[30]

```

# Appendix C — Quick Reference

## Credentials used in this guide

| Node | User | Password |
|---|---|---|
| Cumulus VX switches | cumulus | `cumulus` at first login, changed to `CumulusLinux!` (Lab 0) |
| Ubuntu servers, oob-mgmt-server | ubuntu | `nvidia` (check the node panel or console banner if different) |

## Everyday commands

| Task | Command |
|---|---|
| Reach any node | `ssh cumulus@hxb-leaf-r1` / `ssh ubuntu@hxb-gpu01` from oob-mgmt-server |
| Stage, review, apply, save | `nv set …` → `nv config diff` → `nv config apply -y` → `nv config save` |
| Trial apply with auto-rollback | `nv config apply --confirm 300s -y` then `nv config apply --confirm-yes` |
| Roll back | `nv config history` → `nv config apply <revision>` |
| BGP and routes | `nv show vrf default router bgp neighbor` · `sudo vtysh -c 'show bgp summary'` |
| EVPN | `nv show evpn vni` · `sudo vtysh -c 'show bgp l2vpn evpn route'` |
| RoCE QoS | `nv set qos roce mode lossless` · `nv show qos roce` |
| Soft-RoCE | `sudo modprobe rdma_rxe` · `sudo rdma link add rxe0 type rxe netdev eth1` · `ibv_devinfo -d rxe0` |
| perftest | server `ib_write_bw -d rxe0 -R -F --report_gbits` · client `… <server-ip>` |
| ibsim tools | `ibsim-run sminfo` · `ibsim-run iblinkinfo --switches-only -l` · `ibsim-run ibqueryerrors` |
| ibsim console | `echo 'Unlink "node"[port]' > ~/ibsim/simcmd` · `ReLink` · `PerformanceSet` |
| Network Operator | `kubectl get nicclusterpolicy` · `kubectl get network-attachment-definitions` |
| Ansible | `ansible-playbook playbooks/site-vlans.yml --ask-vault-pass [--check] [--limit host]` |

# Appendix D — Troubleshooting the Lab Environment

| Problem | Likely cause | What to do |
|---|---|---|
| Air rejects the JSON | Image name not available | Pick the nearest Cumulus VX 5.x / Ubuntu 24.04 image per node in the canvas (Lab 0 version note) |
| "Quota exceeded" when starting | Another simulation is running | Sleep the other simulation first; check concurrent vCPU/memory |
| Node unreachable by name | Still booting or no OOB lease | Wait; open its console; reboot the node from the canvas |
| `apt-get` fails on a server | No internet via the OOB NAT | Check the simulation's internet setting; test `ping 8.8.8.8` from the oob-mgmt-server |
| `modprobe rdma_rxe` fails | Module in the extras package | `sudo apt-get install -y linux-modules-extra-$(uname -r)` |
| rxe0 missing after a restart | Soft-RoCE isn't persistent | Re-run `modprobe` and `rdma link add` |
| NVUE command rejected | Syntax differs by release | Press Tab to explore the path; check the Cumulus Linux guide for your version |
| Ansible "connection refused" | API listening only on localhost | `nv set system api listening-address <eth0-ip>` (Lab 12, Task 1) |
| ibsim tools hang | Simulator not running or stopped | `pgrep -af ibsim`; restart it (Lab 8, Task 2) |
| Credits running low | Simulation left running | Always sleep with a checkpoint; set a sleep date |

# Appendix E — Where Each Exam Objective Is Practised

| Objective | Labs |
|---|---|
| 1.1–1.3 AI data centre design | 0, 5, 8, 9 |
| 2.1 Spectrum-X / Cumulus configuration | 1, 2, 3 |
| 2.2 RoCE, adaptive routing, congestion control | 3, 4 |
| 2.3 BGP-EVPN multi-tenancy | 5 |
| 2.4 NVIDIA Air | 0, 6 |
| 2.5–2.6 Monitoring and telemetry | 4, 7 |
| 2.7–2.8 DOCA, BlueField, SuperNIC | 10 (concepts), book Chapter 8 |
| 3.1–3.4 InfiniBand SM, PKeys, routing, monitoring | 8 |
| 4.1–4.2 Network Operator | 10 |
| 5.1–5.2 cl-resource-query, WJH | 7 |
| 5.3 Low-latency verification | 9 |
| 5.4–5.5 UFM health, IB tools | 8, 13 |
| 6.1 NVUE templates | 11 |
| 6.2 Ansible | 12 |
| All | 13 |
