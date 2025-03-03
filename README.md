# Fidesinnova DiD Structure
## 1. DID Method Specification
- A unique DID method must be defined for FidesInnova. The DID will follow the general format:
```
did:fidesinnova:<method-specific-identifier>
```
## 2. DID Components
Component	Description
did	Standard DID prefix
fidesinnova	The DID method name (FidesInnova-specific)
<method-specific-identifier>	A unique identifier for an entity (device, user, organization)
## 3. Method-Specific Identifier
- The method-specific identifier can be designed as follows:
- For IoT Devices:
```
did:fidesinnova:device:<device-ID>
```
- <device-ID> → A cryptographic hash (SHA-256, BLAKE2) of the device’s public key
- Example:
```  
did:fidesinnova:device:8b1a9953c4611296a827abf8c47804d7
```
- For Users:
```
did:fidesinnova:user:<user-hash>
```
- <user-hash> → A DID generated from the user’s verifiable credential (e.g., Ethereum public key)
- Example:
```
did:fidesinnova:user:0x12aBcD34Ef5678...
```
- For Organizations (e.g., Partners, Data Consumers):
```
did:fidesinnova:org:<org-ID>
```
- \<org-ID\> → A unique identifier assigned to organizations using zk-IoT for data access
- Example:
```  
did:fidesinnova:org:trustsense
```
## 4. DID Document Structure
- Each DID is associated with a DID Document, containing the following fields:
```
{
  "@context": "https://www.w3.org/ns/did/v1",
  "id": "did:fidesinnova:device:8b1a9953c4611296a827abf8c47804d7",
  "authentication": [{
    "id": "did:fidesinnova:device:8b1a9953c4611296a827abf8c47804d7#key1",
    "type": "Ed25519VerificationKey2020",
    "controller": "did:fidesinnova:device:8b1a9953c4611296a827abf8c47804d7",
    "publicKeyBase58": "GfHh8c7..."
  }],
  "service": [{
    "id": "did:fidesinnova:device:8b1a9953c4611296a827abf8c47804d7#data",
    "type": "LinkedDataProofs",
    "serviceEndpoint": "https://api.fidesinnova.com/device/8b1a9953c4611296a827abf8c47804d7"
  }]
}
```
## 5. DID Resolution & Storage
- Storage Options:
   - Blockchain (Ethereum, Polygon, or FidesInnova’s private PoA network)
   - IPFS or Arweave for Decentralized Storage
   - FidesInnova zk-IoT Node for Verifiable Storage
 - Resolution Process:
   - A user requests the DID document by resolving did:fidesinnova:device:<device-ID>.
   - The system looks up the document in the decentralized storage layer.
   - The resolved DID document is returned with authentication details and service endpoints.
## 6. Trust & Verification Using zk-IoT
- Zero-Knowledge Proofs (ZKPs) ensure devices are authentic without revealing private data.
- Service Contracts allow secure and monetized IoT data sharing with third parties.

  
    
