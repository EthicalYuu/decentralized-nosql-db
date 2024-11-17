Decentralized Cluster-Based NoSQL Database System
=================================================

> ⚠️ **Important:** This README provides a high-level overview of the project. For comprehensive details, including architecture, design decisions, and implementation, please refer to the [Project Documentation (PDF)](link-to-your-pdf-file).

Overview
--------

This project implements a decentralized, cluster-based NoSQL database system using Java. It simulates the interaction between users and nodes within a distributed database architecture, emphasizing principles of clean code, SOLID design, and DevOps practices. The system is designed for high availability, scalability, and efficient data management without the constraints of traditional relational databases.

Table of Contents
-----------------

-   [Overview](#overview)
-   [Technologies Used](#technologies-used)
-   [Features](#features)
-   [Command Reference](#command-reference)
-   [Architecture](#architecture)
-   [Implementation Highlights](#implementation-highlights)
-   [Documentation](#documentation)
-   [Future Work](#future-work)

Technologies Used
-----------------

-   **Java**: Primary programming language for development.
-   **Spring Framework**: Used for building RESTful services and managing components.
-   **Maven**: Dependency management and project management tool.
-   **Git**: Version control system for tracking changes in the codebase.

Features
--------

-   **Decentralized Node Operation**: Nodes function independently, communicating through REST APIs to ensure seamless data management.
-   **Data Consistency**: Implements multithreading and synchronization mechanisms to ensure consistent data across distributed nodes.
-   **Scalability**: The system supports dynamic scaling by adding more nodes to the cluster.
-   **Security**: User authentication and authorization via secure methods to ensure safe data access.
-   **CLI Integration**: A command-line interface allows users to interact directly with the database through simple commands.

Command Reference
-----------------
After installation, you can use the Command-Line Interface (CLI) to interact with the database system. Below are a few key commands:
| **Command** | **Description** |
| --- | --- |
| `start cluster` | Starts and initializes the cluster. |
| `login <username> <password>` | Logs into an assigned node using a username and password. |
| `write document <document>` | Creates a new document. |
| `read document <id>` | Reads a document by its ID. |
| `read document <id> property <property-name>` | Reads a specific property of a document by ID. |
| `update property <id> <property>` | Updates a property of a document. |
| `delete document <id>` | Deletes a document by ID. |
| `create collection <collection-name>` | Creates a new collection. |
| `delete collection <collection-name>` | Deletes a collection. |
| `use collection <collection-name>` | Selects a collection for subsequent operations. |
| `list collection` | Lists all collections in the current database. |
| `create database <db-name>` | Creates a new database. |
| `delete database <db-name>` | Deletes a database. |
| `use database <db-name>` | Selects a database for subsequent operations. |
| `list database` | Lists all databases in the system. |

Architecture
------------

The system is based on a cluster of Spring-based nodes that communicate through REST APIs. The architecture includes:

### Bootstrap Node

-   Responsible for initializing the cluster and assigning users to specific nodes.

### Cluster Nodes

-   Handle user requests independently, ensuring load balancing and fault tolerance.

![4](https://github.com/user-attachments/assets/72995299-2cf0-46fc-976a-361d76b0ca50)

![19](https://github.com/user-attachments/assets/ce07a91b-094e-411f-bb64-7ea05deac962)


Implementation Highlights
-------------------------

### Bootstrapping and Node Interaction

-   A **bootstrapping node** initializes the cluster and assigns users to nodes in a load-balanced manner.
-   After bootstrapping, users interact exclusively with their assigned nodes for all subsequent operations, ensuring efficient request handling.
  
![7](https://github.com/user-attachments/assets/0336ecab-bd64-4868-887c-387dff483169)

### Core Operations

-   **Database and Collection Management**: Supports creation, deletion, and selection of databases and collections.
-   **Document Management**: Facilitates creation, deletion, and property indexing for JSON-based documents.
-   **JSON Schema and Indexing**: Documents adhere to a unique JSON schema replicated across all nodes. Indexes are created on specific JSON properties for efficient data retrieval.

### Data Consistency and Write Management

-   Ensures **data consistency** using an optimistic locking mechanism for write operations, avoiding race conditions during concurrent writes.

![17](https://github.com/user-attachments/assets/9db55548-8216-4636-84bd-0980c0acf2d2)

-   Implements **document-to-node affinity** for writes, ensuring load-balanced and efficient write operations.

![18](https://github.com/user-attachments/assets/69f7ec4b-e94c-489d-8a6d-4f7b845f209b)

### Inter-Node Communication

-   Nodes communicate via **REST APIs** over a Docker network, ensuring seamless integration and decentralized operation.
-   Write operations trigger **broadcasts** to propagate changes across nodes, maintaining consistency while supporting distributed reads.

### Key Design Considerations

#### Data Structures

-   Efficient indexing is achieved through custom implementations tailored for JSON document properties.

#### Multithreading

-   The system uses multithreading to handle concurrent user operations, ensuring smooth performance and preventing data conflicts.

#### Load Balancing

-   The bootstrapping node distributes document writes across the cluster using a load-balanced affinity mechanism.

![21](https://github.com/user-attachments/assets/abdec5bb-6919-49f5-b932-49e5ce84cef3)

#### Communication Protocols

-   RESTful endpoints are used for all inter-node communication, ensuring a standardized and scalable approach.

#### Security

-   Robust **authentication** and **role-based access control** mechanisms protect user data and ensure secure system interactions.

#### DevOps Practices

-   The project is fully containerized using **Docker**, facilitating easy deployment and management.

Documentation
-------------

For detailed documentation on the system's architecture, design, and implementation, please refer to the Project Documentation (PDF).

Future Work
-----------

Future improvements could include:

-   Advanced query processing for JSON documents.
-   More granular data consistency controls.
-   Enhanced security protocols for inter-node communication.
