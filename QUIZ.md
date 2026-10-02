<div align="center">

<h1>
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=30&pause=1000&color=0B5ED7&center=true&vCenter=true&width=650&lines=Networking+Concepts+Quiz;IPs+%7C+Subnets+%7C+DNS+%7C+TCP%2FUDP;Think+first.+Toggle+to+reveal." alt="Networking Concepts Quiz" />
</h1>

<p><b>One concept quiz. No coding required. Click a question to reveal the answer.</b></p>

</div>

---

### 🌐 Concept Quiz — Networking

*Addressing, subnetting, DNS, transport protocols, ports, and everyday diagnostics.*

<details>
<summary><b>1.</b> What is an IP address? Difference between IPv4 and IPv6?</summary>

A numeric label for a network interface. IPv4 is 32-bit (`192.168.1.1`); IPv6 is 128-bit (`2001:db8::1`) — bigger address space, no NAT needed in principle.
</details>

<details>
<summary><b>2.</b> What is a subnet mask? What does <code>/24</code> mean in CIDR?</summary>

A mask that separates the network portion from the host portion of an IP. `/24` means the first 24 bits are the network — 256 addresses, 254 usable hosts.
</details>

<details>
<summary><b>3.</b> Given <code>192.168.1.10/24</code>, what is the network address? The broadcast address? The usable host range?</summary>

Network: `192.168.1.0`. Broadcast: `192.168.1.255`. Usable hosts: `192.168.1.1` – `192.168.1.254`.
</details>

<details>
<summary><b>4.</b> What is the difference between a <b>private</b> and <b>public</b> IP? Give one range for each.</summary>

Private IPs are non-routable on the internet (`10.0.0.0/8`, `172.16.0.0/12`, `192.168.0.0/16`). Public IPs are globally routable, assigned by ISPs.
</details>

<details>
<summary><b>5.</b> What does <code>127.0.0.1</code> mean? How does it differ from <code>0.0.0.0</code>?</summary>

`127.0.0.1` is **loopback** — "this machine only." `0.0.0.0` as a **bind address** means "all interfaces"; as a **route** it means "default."
</details>

<details>
<summary><b>6.</b> What is DNS? What does a resolver do?</summary>

DNS maps names to IPs. A resolver queries the DNS hierarchy (root → TLD → authoritative) and caches answers to answer client lookups quickly.
</details>

<details>
<summary><b>7.</b> What does <code>/etc/hosts</code> do, and how does it relate to DNS?</summary>

A local static name→IP map. It's checked **before** DNS, so entries there override DNS for that machine — handy for testing.
</details>

<details>
<summary><b>8.</b> What's the difference between TCP and UDP?</summary>

TCP is connection-oriented, ordered, reliable (handshake, retransmits). UDP is connectionless, unordered, unreliable — faster, used for DNS, VoIP, streaming.
</details>

<details>
<summary><b>9.</b> What is a port? Name three well-known ports and their services.</summary>

A number identifying a service on a host. Examples: `22` SSH, `80` HTTP, `443` HTTPS. Well-known ports are `0`–`1023`.
</details>

<details>
<summary><b>10.</b> What's the difference between <b>listening</b> on <code>127.0.0.1:80</code> and <code>0.0.0.0:80</code>?</summary>

`127.0.0.1` accepts only **local** connections. `0.0.0.0` accepts connections on **every** interface — reachable from the network (subject to firewall).
</details>

<details>
<summary><b>11.</b> What does <code>ping</code> actually test? What does it <i>not</i> test?</summary>

Tests ICMP reachability and round-trip time to a host. It does **not** test TCP/UDP ports or whether a specific service is up — a host can respond to ping but have port 80 closed.
</details>

<details>
<summary><b>12.</b> What does <code>curl http://example.com</code> do at the network level? Name three layers it touches.</summary>

Resolves DNS (application), opens a TCP connection to port 80 (transport), sends an HTTP GET and reads the response. Touches application, transport, and network layers.
</details>

<details>
<summary><b>13.</b> What does <code>ss -tuln</code> show?</summary>

Listening sockets: `-t` TCP, `-u` UDP, `-l` listening, `-n` numeric (no DNS/service lookup). A quick inventory of what's listening on this host.
</details>

<details>
<summary><b>14.</b> If two machines are on <code>192.168.1.0/24</code>, can they reach each other directly? What about <code>192.168.2.5</code>?</summary>

Same subnet → yes, direct via ARP. `192.168.2.5` is on a **different** subnet → traffic must go through a router/gateway to reach it.
</details>

<details>
<summary><b>15.</b> What is NAT, and why does it matter when you're running services?</summary>

Network Address Translation rewrites private IPs to a public one on the way out. For inbound services you need **port forwarding** on the router — otherwise the service is unreachable from the internet.
</details>

<br>

---

### 🔬 Diagnostic Task

*Use real commands to answer the questions below, then compare with the answers you toggled.*

```bash
# 1. What is my IP and subnet?
ip addr show

# 2. What's my default gateway?
ip route show

# 3. Can I reach the internet? (ICMP)
ping -c 3 1.1.1.1

# 4. Does DNS resolve?
dig example.com +short

# 5. What's listening locally?
ss -tuln

# 6. What does the full HTTP exchange look like?
curl -v http://example.com
```

---

<div align="center">

*Come back, click a few, see what stuck.*

</div>
