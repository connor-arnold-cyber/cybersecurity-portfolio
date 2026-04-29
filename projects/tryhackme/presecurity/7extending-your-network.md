# Networking: Port Forwarding, Firewalls, VPNs, Routers, and Switches

---

## Port Forwarding

### What It Is
- Port forwarding allows external devices (internet) to access services inside a private network
- It maps a **public IP + port → private IP + port**

---

### The Problem It Solves

- Devices inside a network use **private IPs** (ex: 192.168.x.x)
- These are **not accessible from the internet**
- Without port forwarding:
  - Only devices on the same network (intranet) can access services

---

### What It Does

- Exposes a specific internal service to the internet
- Allows traffic coming to a public IP to be redirected to a specific device inside the network

---

### How It Works (Step-by-Step)

Example:
- Internal server:
  - IP: 192.168.1.10
  - Port: 80 (web server)

- Router:
  - Public IP: 82.62.51.70

#### Flow:

1. External user connects to:
   ```
   82.62.51.70:80
   ```

2. Router receives the request

3. Router checks port forwarding rules

4. Router forwards traffic to:
   ```
   192.168.1.10:80
   ```

5. Internal server responds

6. Router sends response back to external user

---

### Key Concept

- Port forwarding = **traffic redirection**
- It does NOT decide if traffic is allowed
- It only decides **where traffic goes**

---

### Port Forwarding vs Firewall

- Port Forwarding:
  - Routes traffic to a device

- Firewall:
  - Decides if traffic is allowed or blocked

---

### Where It Is Configured

- Configured on the **router**

---

## Firewall

### What It Is

- A device that controls what traffic can:
  - Enter a network
  - Leave a network

---

### What It Does

- Filters traffic based on rules

---

### How It Works

Firewalls inspect packets based on:

- Source (where it came from)
- Destination (where it's going)
- Port (which service)
- Protocol (TCP or UDP)

---

### Packet Inspection

- Firewalls analyze packets before allowing or blocking them

---

### Types of Firewalls

#### Stateful Firewall

- Looks at **entire connection**
- Tracks session behavior

##### What It Does
- Understands context of communication
- Can allow or block based on connection behavior

##### Tradeoffs
- More accurate
- Uses more system resources

---

#### Stateless Firewall

- Looks at **individual packets only**

##### What It Does
- Uses fixed rules
- No memory of previous packets

##### Tradeoffs
- Fast and efficient
- Less intelligent
- Only as good as its rules

---

### Key Differences

| Feature | Stateful | Stateless |
|--------|--------|----------|
| Tracks connections | Yes | No |
| Resource usage | High | Low |
| Accuracy | High | Lower |

---

### OSI Layers

- Firewalls operate at:
  - Layer 3 (Network)
  - Layer 4 (Transport)

---

## VPN (Virtual Private Network)

### What It Is

- A secure tunnel between devices over the internet
- Creates a **private network over a public network**

---

### What It Does

- Encrypts data
- Allows secure communication between networks

---

### How It Works

- Data is encrypted before leaving device
- Sent through a secure tunnel
- Decrypted at destination

---

### Key Concepts

- Devices inside VPN behave like they are on the same network
- Even if physically far apart

---

### Benefits

#### 1. Connect Remote Networks
- Example:
  - Office A ↔ Office B

---

#### 2. Privacy

- Encrypts traffic
- Prevents others from viewing data
- Useful on public WiFi

---

#### 3. Anonymity

- Hides activity from:
  - ISPs
  - Intermediaries

---

### Important Limitation

- Privacy depends on VPN provider
- If VPN logs data → no real anonymity

---

### VPN Technologies

#### PPP (Point-to-Point Protocol)

- Provides:
  - Authentication
  - Encryption

- Limitation:
  - Cannot route traffic by itself

---

#### PPTP

- Allows PPP data to travel across networks

##### Pros
- Easy to set up

##### Cons
- Weak encryption

---

#### IPSec

- Encrypts data using IP framework

##### Pros
- Strong encryption

##### Cons
- Complex setup

---

## Router

### What It Is

- A device that connects networks

---

### What It Does

- Moves data between networks

---

### How It Works

- Uses **routing**
- Determines best path for data

---

### Routing Decisions Based On

- Shortest path
- Reliability
- Speed of connection

---

### OSI Layer

- Operates at Layer 3 (Network)

---

### Key Features

- Connects different networks
- Can configure:
  - Port forwarding
  - Firewalls

---

## Switch

### What It Is

- A device that connects multiple devices within a network

---

### What It Does

- Sends data to the correct device

---

### Layer 2 Switch

#### How It Works
- Uses MAC addresses
- Forwards frames

#### Key Role
- Device-to-device communication within same network

---

### Layer 3 Switch

#### How It Works
- Uses:
  - MAC addresses (like L2)
  - IP addresses (like router)

#### Key Role
- Can route traffic between networks

---

### VLAN (Virtual LAN)

#### What It Is
- Splits a network into smaller virtual networks

#### What It Does
- Separates groups of devices

#### Why It Matters
- Improves security
- Controls communication between groups

---

### Example

- Sales VLAN
- Accounting VLAN

Both:
- Can access internet

But:
- Cannot communicate with each other

---

## Key Takeaways

- Port forwarding = directs traffic to internal device
- Firewall = decides allow/deny
- VPN = secure encrypted tunnel
- Router = connects networks and routes traffic
- Switch = connects devices inside network
- VLAN = splits network logically for control and security
