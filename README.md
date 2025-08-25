# Agile Call Framework

A next-generation blockchain-native document management and collaboration toolkit, built on Stacks, designed for high-trust, permission-aware document workflows.

## Overview

The Agile Call Framework provides a robust, decentralized solution for managing sensitive documents with unprecedented security, granular access control, and version tracking. By leveraging blockchain's immutability, we create a tamper-proof document collaboration environment.

### Key Features
- Blockchain-secured document metadata
- Fine-grained access permission management
- Version-controlled document tracking
- Decentralized storage integration
- Immutable ownership records
- Flexible collaboration models

### Use Cases
- Professional document collaboration
- Compliance and audit trails
- Secure knowledge management
- Distributed team workflows
- Legal and financial document tracking

## Architecture

The system is built around a core smart contract that manages document metadata, collections, and permissions. Here's how it works:

```mermaid
graph TD
    A[User] -->|Uploads Document| B[DocuNest Core Contract]
    B -->|Stores Metadata| C[Blockchain]
    B -->|Points to Content| D[Decentralized Storage]
    B -->|Manages| E[Collections]
    B -->|Controls| F[Permissions]
    B -->|Tracks| G[Versions]
```

### Core Components
- Document Registry
- Collection Management
- Permission System
- Version Control
- Access Control

## Contract Documentation

### docunest-core.clar

The main contract handling all document management functionality.

#### Permission Levels
- NONE (0): No access
- VIEW (1): Read-only access
- EDIT (2): Can modify documents
- ADMIN (3): Full control

#### Key Data Structures
- `collections`: Stores collection metadata
- `documents`: Stores document metadata
- `collection-documents`: Maps documents to collections
- `document-versions`: Tracks document version history
- `collection-permissions`: Stores collection access rights
- `document-permissions`: Stores document access rights

## Getting Started

### Prerequisites
- Clarinet
- Stacks wallet
- IPFS or Gaia storage setup

### Installation
1. Clone the repository
2. Install dependencies
3. Deploy using Clarinet

```bash
clarinet deploy
```

### Basic Usage

1. Create a collection:
```clarity
(contract-call? .docunest-core create-collection 
    "collection-123" 
    "Family Documents" 
    (some "Important family records"))
```

2. Add a document:
```clarity
(contract-call? .docunest-core add-document
    "doc-456"
    "Will.pdf"
    (some "Last Will and Testament")
    "pdf"
    "ipfs://Qm..."
    0x1234...
    u1000)
```

## Function Reference

### Collection Management
- `create-collection`: Create a new document collection
- `delete-collection`: Remove a collection
- `get-collection`: Retrieve collection details

### Document Management
- `add-document`: Add a new document to the system
- `update-document`: Create a new document version
- `delete-document`: Remove a document
- `get-document`: Retrieve document details
- `get-document-version`: Get specific version information

### Permission Management
- `grant-document-permission`: Set document access rights
- `grant-collection-permission`: Set collection access rights
- `can-view-document`: Check view permissions
- `can-edit-document`: Check edit permissions
- `can-admin-collection`: Check admin permissions

## Development

### Testing
Run the test suite using Clarinet:
```bash
clarinet test
```

### Local Development
1. Start Clarinet console:
```bash
clarinet console
```

2. Deploy contracts:
```clarity
(contract-call? .docunest-core ...)
```

## Security Considerations

### Key Security Features
- Immutable audit trail of all document changes
- Granular permission controls
- Owner-only administrative actions
- Version history tracking

### Best Practices
1. Always verify document hashes after upload
2. Use appropriate permission levels
3. Regularly audit access permissions
4. Keep private keys secure
5. Backup documents in secure locations

### Limitations
- Document content stored off-chain
- Gas costs for frequent updates
- Block size limits for batch operations
- Permission inheritance not implemented