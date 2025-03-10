# Data Lattice

## Overview

Convex maintains data as part of the operation of the CVM (on-chain). It is possible to build decentralised solutions using these capabilities alone which we call a "pure dApp". This approach is sufficient for many use cases, however more sophisticated decentralised applications are likely to require additional data sources (off-chain). We call such applications "hybrid dApps".

While off-chain data can be provided in many different ways, including via tradition Web 2.0 server infrastructure, there is a compelling case for a more powerful decentralised storage solution to support hybrid dApps on Convex

## Rationale

Here are some of the key reasons data storage and processing extrinsic to Convex is useful for decentralised applications:

1. Scalability: Blockchains inherently have limits on computational capacity and data throughput. Storing and analysing large data sets is inefficient on-chain. Off-chain resources can horizontally scale to demand.

2. Privacy: Sensitive data like healthcare records or personal information requires restricted access. Public blockchains provide transparency but not confidentiality. Off-chain systems support encryption and fine-grained access control.

3. Speed & Responsiveness: DLTs feature lengthy settlement finality and limited transactions per second. This hinders uses needing real-time data flow like messaging or IoT monitoring. Off-chain networks have fewer limits reacting to data changes. 

4. Cost Efficiency: Persisting every small update on global chains becomes expensive long term. Offloading data which does not require use of the global on-chain state curtails unnecessary fees and bloat. Subnets handle localized logic.

5. Regulatory Compliance: Chains are transnational making compliance difficult. Off-chain systems can enforce jurisdiction specific rules around permissible data types, storage locations, access restrictions and lifecycles.

6. Rich Data Formats: Chains restrict data schemas to basic key-value pairs and byte strings. Document databases, media assets, and complex analytic jobs operate off-chain.

In summary, a hybrid decentralized model using blockchains for consensus/settlement alongside purpose-built off-chain coordination handles data-intensive tasks aligned to use case needs more effectively. This unlocks wider adoption.

## Capabilities

The Data Lattice provides the following capabilities:

- **Content Addressability**: all data is addressed and indexed by a cryptographic hash. The near impossibility of hash collisions ensures that having the correct hash always allows location of the correct data.

- **Verifiability**: all data can be verified in its entirety from the cryptographic hash. Because the data takes the form of a Merkle Tree, this verifiability extends to multiple levels

- **Structural Sharing**: all common subtrees (i.e. sharing the same content and cryptographic hash) are automatically shared and de-duplicated. This property arises naturally from content addressability and the Merkle Tree structure, which in turn allows for efficient operations such as cloning and storing modified copies of any data.

- **Rich Data Types**: The Lattice supports a wide variety of data structures, including all data types available on the CVM such as maps, lists, vectors, numbers, strings and arbitrary blobs of byte data. In particular, the data lattice types support a superset of JSON, so JSON objects can be naturally represented with ease.

- **CRDT support**: The data lattice forms a natural CRDT, where arbitrary sets of data can be merged to create a union of all data. This process is aided by automatic de-duplication to reduce storage and transmission costs.

- **Garbage Collection**: Stores can be garbage collected to reduce resource requirements at any time, simply by specifying which data is required to be maintained ("pinning"). This facilitates better operational management and allows flexible control by data lattice providers regarding what data they are interested in preserving or hosting.

- **Access Control**: data lattice hosts may optionally impose whatever access controls they require for governance, security or privacy purposes.

## Reference Implementation

The Data Lattice reference implementation contains two key components:

### Etch

Etch is the storage subsystem utilised by Convex, which is specialised for efficient storage of content addressable Merkle Trees. 

### REST API

The Data Lattice rest API provides key data lattice capabilities:

- Insert data
- Retrieve data
- Pin / unpin data
- Access controls
- Replication

## Specification

TODO: Elaborate
