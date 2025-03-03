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
