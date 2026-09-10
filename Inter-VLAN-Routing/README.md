# Inter-VLAN Routing Lab

## 📌 Objective

Configure communication between different VLANs using a Cisco router and router-on-a-stick configuration.

## 🌐 Network Design

| VLAN | Department | Network         | Default Gateway |
| ---- | ---------- | --------------- | --------------- |
| 10   | SALES      | 192.168.10.0/24 | 192.168.10.1    |
| 20   | IT         | 192.168.20.0/24 | 192.168.20.1    |

## 🧩 Technologies

* Cisco Router
* Cisco Switch
* VLAN
* 802.1Q Trunking
* Router-on-a-Stick
* IPv4

## ⚙️ Router Configuration

```cisco
Router# configure terminal

Router(config)# interface gigabitEthernet 0/0
Router(config-if)# no shutdown
Router(config-if)# exit

Router(config)# interface gigabitEthernet 0/0.10
Router(config-subif)# encapsulation dot1Q 10
Router(config-subif)# ip address 192.168.10.1 255.255.255.0
Router(config-subif)# exit

Router(config)# interface gigabitEthernet 0/0.20
Router(config-subif)# encapsulation dot1Q 20
Router(config-subif)# ip address 192.168.20.1 255.255.255.0
Router(config-subif)# exit
```

## 🔀 Switch Trunk Configuration

```cisco
Switch# configure terminal

Switch(config)# interface gigabitEthernet 0/1
Switch(config-if)# switchport mode trunk
Switch(config-if)# exit
```

## 🔍 Verification Commands

```cisco
show vlan brief
show interfaces trunk
show ip interface brief
show ip route
```

## 🧪 Testing

Connectivity can be tested using:

```text
ping 192.168.10.1
ping 192.168.20.1
```

A successful ping between hosts in different VLANs confirms that Inter-VLAN Routing is functioning.

## ✅ Concepts Demonstrated

* VLAN segmentation
* Trunking
* 802.1Q encapsulation
* Router-on-a-stick
* Default gateways
* Inter-VLAN communication
* IPv4 addressing
* Network troubleshooting
