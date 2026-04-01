**This is public repo with limited architectural and functional information of Project Postmaster.*


## Postmaster

**Postmaster** is a secure, fast, **decentralised & private**; peer to peer network and protocol 
designed for storing and sharing data in a distributed file system.

**In simple terms,** Postmaster follows a hybrid client-server architecture: 
- Clients (Peers):
  Nodes that store and share data with other peers in the network.
- Server (Control Plane):
  A centralized component responsible for maintaining metadata about peers and helping clients discover the most suitable peers to connect with.

#
### Architecture: 

**Postmaster** is designed using a control-plane and data-plane separation:
- **Data Plane (Peers)**
  - Runs on individual machines (clients)
  - Enables participation in the P2P network
  - Handles:
      - Data storage (in chunks) across different peers
      - Inter-region and cross-region replication for HA (configurable) 
      - Robust Replication Engine for fault tolerance (DR)
- **Control Plane (Server)**
  - Centralized metadata service
  - *Does not know which peer stored what chunk on which other peers*
  - Responsible for:
      - Peer registration
      - Maintaining peer state
      - Intelligent peer discovery

### Decentralized and Private (Core Differentiator):

Traditional decentralized systems (e.g., torrent-based networks) are:
- Fully decentralized
- But not private — data locations can often be discovered or inferred across the network

In contrast, **Postmaster** introduces controlled decentralization:
- Data is still distributed across peers
- But metadata visibility is restricted
- No peer can discover:
    - Where other peers store their data
    - Which peers hold specific data chunks
- Only the data owner has knowledge of their data placement.

While **Postmaster** is fundamentally a decentralized system, it intentionally uses a centralized control plane.
- This is a design trade-off to achieve:
  - Strong privacy guarantees
  - Efficient peer discovery
  - Better control over data placement


#
### Current Status:
I am currently evaluating architectural trade-offs for this project, focusing on performance, scalability, reliability, resiliency, availability and simplicity. 
I will soon begin development of the control plane (peer discovery service).

**On a side note:** I have previously worked on a similar project from an implementation perspective. This project is inspired/learned by that experience: https://github.com/hiabhishek1888/ninjafilesystem

### Found any missing/wrong piece or any doubt? Please open an issue to discuss.
Cheers 🙂
