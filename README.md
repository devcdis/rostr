# Rostr: A Decentralized FOSS Gig Marketplace Powered by Nostr

The global community requires an open source alternative to the gig economy. Here lies a permanent link to this public good; Rostr.

This repository hosts a FOSS instantiation of a gig working application built on the [Nostr networking protocol](https://nostr.com/). It is aimed to free service providers, and customers from the shackles of opaque algorithms of present-day gig economy. Users can post messages of services required via relays to a public roster. Those subscribed to the roster can then read those relays. This can be done both to list services or avail listed services.

Any gig service can be listed and sought after through relays on Rostr. An example relay has been hosted on https://cdis.iitk.ac.in/rostr/

We invite developers to create forks of this project with better trust mechanisms, language support, UI improvements etc. It is our hope to motivate a FOSS-driven competitor within the gig-economy.

### Technical Overview

Rostr is composed of three main components:

1. **Customer Mobile App**: This application enables customers to browse and connect with gig workers in their local area.
   
2. **Merchant Mobile App**: Designed for gig workers, this app allows them to discover and register with relays, making their services available to potential customers.

3. **Relay Backend**: Built as an extension of the [Nostream](https://github.com/cameri/nostream) relay implementation, the backend manages communication between clients and relays. It also includes a dashboard for relay managers to oversee and manage active gig workers in real-time.

---

### Relay Lists and Network Setup

Rostr's network architecture includes a decentralized relay system, allowing for robust service discovery and avoiding a single point of failure. Each relay maintains a list of other relays, ensuring system redundancy and a growing network.

- **Master Server**: A master server is responsible for introducing new relays to the network. It provides the initial list of relays to the new relay, allowing it to request inclusion from existing relays. Once a relay is inducted into the network, it operates independently, and the master server is no longer involved in its functioning. This ensures that the network remains fully decentralized and can continue to operate without reliance on any central entity.

- **Relay Lists**: Relays, customers, and merchants all maintain relay lists. The lists are dynamically updated as they interact with the network:
  - *Customers*: Automatically fetch and update relay lists upon connecting with a relay.
  - *Merchants*: Choose relays to advertise services based on various metrics like cost and reach.
  - *Relays*: Periodically update their own lists by interacting with the master server and other relays.

---

### Mobile App Features

- **Merchant App**: 
  - Fetch relay lists from the master server.
  - View relays based on location, advertising costs, operating radius, and reach.
  - Choose relays to advertise services and send service details via WebSocket.
  - Modify, add, or remove connected relays and service offerings.

- **Customer App**: 
  - Fetch relay lists from the master server.
  - View merchants from specific or nearby relays, categorized by services offered.
  - Fetch and update relay lists when connecting to a relay.

---

### Relay Management System

- **Relay Admin App**:
  - Fetch and manage relay lists.
  - Handle merchant applications for service listings.
