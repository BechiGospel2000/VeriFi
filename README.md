# VeriFi Smart Contract  

## Overview  
VeriFi is a **Decentralized Identity Verification Smart Contract** built on the Stacks blockchain using Clarity. It enables users to securely register, verify, and manage their identities on-chain while ensuring privacy and security. Only the contract owner can verify user identities, preventing unauthorized access.  

## Features  
- **Identity Registration**: Users can register their identity with a name and email.  
- **Decentralized Verification**: The contract owner can verify users to confirm their authenticity.  
- **Identity Management**: Users can retrieve or delete their identity information.  
- **Immutable Security**: All identity data is stored on the blockchain, ensuring transparency and protection against fraud.  

## Functions  

### 1. **Register Identity**  
Allows users to register their identity.  
```clarity
(define-public (register-identity (name (string-utf8 100)) (email (string-utf8 100))) ...)
```  
- **Params**:  
  - `name` (string, max 100 chars) – User's name  
  - `email` (string, max 100 chars) – User's email  
- **Returns**: `(ok true)` on success or an error if already registered.  

### 2. **Verify Identity (Admin Only)**  
Only the contract owner can verify a user's identity.  
```clarity
(define-public (verify-identity (user principal)) ...)
```  
- **Params**:  
  - `user` (principal) – The user to verify  
- **Returns**: `(ok true)` on success or an error if unauthorized.  

### 3. **Get Identity Information**  
Fetches a user's identity details.  
```clarity
(define-read-only (get-identity (user principal)) ...)
```  
- **Params**:  
  - `user` (principal) – The user whose identity is requested  
- **Returns**: The user's identity details or an error if not found.  

### 4. **Delete Identity**  
Users can delete their registered identity.  
```clarity
(define-public (delete-identity) ...)
```  
- **Returns**: `(ok true)` on successful deletion or an error if no identity exists.  

## Error Codes  
- **`ERR_UNAUTHORIZED (1001)`** – Action restricted to contract owner.  
- **`ERR_ALREADY_VERIFIED (1002)`** – User is already registered.  
- **`ERR_NOT_FOUND (1003)`** – User identity not found.  

## Deployment  
To deploy VeriFi, update the contract with the owner's principal address and deploy it on the Stacks blockchain using Clarity tools.  

## License  
This project is open-source and available under the **MIT License**. 