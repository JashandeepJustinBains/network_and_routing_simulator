### **Core Network Components**
#### **1. Router Component (`<Router />`)**
- **Props**:
  - `imageSrc`: URL or local path to router image.
  - `size`: Dimensions for rendering.
  - `ports`: List of available ports (RJ-45, Fiber, etc.).
  - `routingTable`: Array of routes.
  - `configStatus`: Tracks whether the router has correct/incorrect configurations.
- **Features**:
  - Displays routing table dynamically.
  - Shows active/inactive interfaces.
  - Visualizes routing protocols (OSPF, BGP, RIP).

#### **2. Switch Component (`<Switch />`)**
- **Props**:
  - `ports`: RJ-45, Fiber (SFP, QSFP), numbered interfaces.
  - `switchingTable`: Mapping MAC addresses to ports.
  - `spanningTreeStatus`: Shows STP state (root bridge, blocked ports).
  - `configStatus`: Shows proper/improper switch configuration.
- **Features**:
  - VLAN assignments.
  - Shows packet flow paths dynamically.
  - Indicates misconfigurations (loop issues, mismatched trunk/native VLANs).

### **Network Infrastructure Components**
#### **3. Host Component (`<Host />`)**
- **Props**:
  - `hostname`
  - `ipAddress`
  - `macAddress`
  - `status`: Up/Down/Error state
- **Features**:
  - Displays ping/traceroute responses.
  - Allows network simulation based on connectivity.

#### **4. Cable Component (`<Cable />`)**
- **Props**:
  - `type`: Ethernet, Fiber, Coaxial.
  - `length`
  - `status`: Connected, Faulty, Intermittent.
- **Features**:
  - Simulates cable disconnections and failures.
  - Allows automatic fault injection for troubleshooting.

#### **5. Packet Flow Component (`<Packet />`)**
- **Props**:
  - `srcIP`
  - `destIP`
  - `protocol`: TCP, UDP, ICMP.
  - `status`: Delivered, Dropped, Error.
- **Features**:
  - Shows real-time packet movement.
  - Indicates congestion and packet loss.

### **Simulation & Algorithm Components**
#### **6. Configuration Generator (`<ConfigGenerator />`)**
- **Props**:
  - `deviceType`: Router, Switch, Host.
  - `difficultyLevel`: Easy, Moderate, Complex.
- **Features**:
  - Creates randomized configurations (both correct and incorrect).
  - Generates troubleshooting challenges based on misconfigurations.

#### **7. Network Visualization (`<NetworkGraph />`)**
- **Props**:
  - `topologyData`: Nodes and edges of the network.
  - `highlightErrors`: Marks misconfigured devices.
- **Features**:
  - Draws dynamic network graphs.
  - Displays active routes, blocked paths, and link failures.



A pseudo-CLI for your network emulator is a brilliant idea! It will give users an authentic command-line troubleshooting experience while keeping them focused on networking-specific functions.

### **Key Functions to Include in the CLI**
Your CLI should allow users to simulate real-world troubleshooting commands. Here are some essential ones:
1. **Basic Network Info & Diagnostics**
   - `ifconfig` / `ip addr show` – Show network interface details.
   - `ping <destination>` – Test connectivity to an IP or hostname.
   - `traceroute <destination>` – Show the path packets take to a target.
   - `netstat -rn` – Show routing tables.

2. **Switch & VLAN Configuration**
   - `show vlan brief` – Display VLANs and port assignments.
   - `show mac-address-table` – View MAC address mappings.
   - `show spanning-tree` – Check STP status (root bridge, blocked ports).
   - `interface eth0` / `switchport mode access` – Configure ports.

3. **Routing Protocols & Configuration**
   - `show ip route` – Display active routes.
   - `show ip ospf neighbor` – Check OSPF adjacency.
   - `show bgp summary` – Show active BGP neighbors and prefixes.

4. **Security & Firewall Testing**
   - `show access-lists` – View configured ACLs.
   - `test packet firewall <src> <dest>` – Simulate firewall traffic.
   - `show arp` – Check ARP table for potential security issues.

5. **Automatic Failure Injection**
   - `simulate cable failure <interface>` – Break a random link.
   - `simulate routing misconfiguration` – Inject incorrect routing entries.
   - `simulate traffic congestion` – Artificially add latency/jitter.

- **Load Balancer (`<LoadBalancer />`)** – Tracks server health and routing failures.
- **DHCP Server (`<DHCPServer />`)** – Assigns IPs dynamically with lease expiration issues.
- **DNS Server (`<DNSServer />`)** – Resolves domains while introducing incorrect or unreachable records.
- **VPN Tunnel (`<VPN />`)** – Visualizes encrypted traffic flow while showing tunneling errors.
- **Firewall Packet Inspection (`<FirewallInspector />`)** – Allows users to check why packets are being blocked.

### **How to Display the CLI**
You could have a **fixed panel on the right or left** of the screen, where users enter commands. Here's how you can structure it:
1. **Split View Layout**
   - Left: Main network visualization (routers, switches, hosts).
   - Right: CLI panel (input/output terminal).
   - Dynamic resizing for usability.

2. **Command History & Autocomplete**
   - Show previous commands for reference.
   - Autocomplete suggestions based on common CLI syntax.

3. **Real-time Feedback**
   - Parse errors & invalid commands.
   - Color-coded output (green for successful commands, red for errors).
   - Interactive responses (e.g., "Routing misconfiguration detected! Neighbor unreachable.")
