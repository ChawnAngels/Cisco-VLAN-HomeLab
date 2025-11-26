# Cisco-VLAN-HomeLab
VLAN trunking lab using 2 Cisco switches (VLAN 10/20/30, STP, access + trunk ports)
## Topology

- **Switch 1:**  
- **Switch 2:**   

- **Trunk link**
  - `Gi1/0/4` (Chawn-Lab1) ↔ `Fa0/4` (Switch)
  - Encapsulation: 802.1Q
  - Allowed VLANs: 10, 20, 30
  - Native VLAN: 1

- **VLANs**

  | VLAN | Name  |
  |------|-------|
  | 10   | RED   |
  | 20   | BLUE  |
  | 30   | GREEN |

- **Access ports (for end devices)**  
  Switch 1(Chawn-Lab1):
  - `Gi1/0/1` → VLAN 10 (RED)  
  - `Gi1/0/2` → VLAN 20 (BLUE)  
  - `Gi1/0/3` → VLAN 30 (GREEN)

  Switch 2(Switch):
  - `Fa0/1` → VLAN 10 (RED)  
  - `Fa0/2` → VLAN 20 (BLUE)  
  - `Fa0/3` → VLAN 30 (GREEN)

At the moment I only have one laptop, so I test by moving it between access ports on each switch. The switches are fully configured for multiple hosts once I add more devices.

---

## Key Configuration

### VLANs

```bash
vlan 10
 name RED
vlan 20
 name BLUE
vlan 30
 name GREEN
```
### Trunk ports

**Switch 1**

```bash
! Configure trunk on Switch 1 (2960-X)
interface Gi1/0/4
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30
```

**Switch 2**

```bash
! Configure trunk on Switch 2 (2960)
interface Fa0/4
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30
```

These commands configure the trunk link between Switch 1 and Switch 2 to carry VLANs 10, 20, and 30 using 802.1Q.
