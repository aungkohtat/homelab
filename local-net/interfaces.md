auto lo
iface lo inet loopback

# Interface 1 - VLAN 10 on enp5s0
iface enp5s0 inet manual

auto vmbr10
iface vmbr10 inet static
    address 172.16.10.10/24
    bridge_ports enp5s0
    bridge_stp off
    bridge_fd 0

# Interface 2 - VLAN 20 on enp4s0
iface enp4s0 inet manual

auto vmbr20
iface vmbr20 inet static
    address 172.16.20.10/24
    bridge_ports enp4s0
    bridge_stp off
    bridge_fd 0

# Interface 3 - VLAN 30 on enp7s0
iface enp7s0 inet manual

auto vmbr30
iface vmbr30 inet static
    address 172.16.30.10/24
    bridge_ports enp7s0
    bridge_stp off
    bridge_fd 0

# Uplink interface on enp5s0 (if needed)
auto vmbr0
iface vmbr0 inet static
    address 192.168.1.100/24
    gateway 192.168.1.1
    bridge_ports none
    bridge_stp off
    bridge_fd 0