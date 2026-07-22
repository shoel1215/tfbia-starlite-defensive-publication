# Star LITE (TFBIA) — High-Level Architecture

## Overview
Star LITE is a compact edge terminal that performs the full sensitive biometric-to-credential pipeline on-device in a Trusted Execution Environment while binding the result to a non-transferable on-chain credential.

## Core Layers

### 1. Physical / Hardware Layer
- Multi-modal vision module (RGB + NIR/ToF depth cameras with IR illumination)
- Main SoC with NPU (e.g., Rockchip RV1126B-class or equivalent)
- Trusted Execution Environment (TEE — AMD SEV-SNP or ARM TrustZone)
- Dedicated secure element / HSM for root of trust and post-quantum operations
- Tamper sensors, PoE connectivity, encrypted storage

### 2. Biometric Pipeline (TEE-Isolated)
- Capture → Liveness Detection & PAD (ISO 30107)
- Feature Extraction (ArcFace/CosFace embeddings)
- Cancelable Transform (BioHash)
- Fuzzy Commitment (BCH codes)
- Quality scoring and deduplication check

### 3. Cryptographic Binding (TEE)
- SHA-3 hash commitment to protected template
- Post-quantum authority signature (Dilithium/Falcon)
- Optional succinct ZK proof generation

### 4. Credential & On-Chain Layer
- Soulbound Token (SBT) issuance (ERC-5192/EIP-4973 semantics)
- Binding of cryptographic commitment to user wallet/DID
- On-chain revocation registry
- Optional W3C Verifiable Credential payload

## Data Flow (Enrollment)
Capture → TEE (liveness + BioHash + fuzzy commitment + hash commitment) → Authority attestation → SBT mint → Secure storage of protected template

## Data Flow (Verification)
Capture → TEE (match or ZK proof) → On-chain SBT + revocation check → Attested result

## Security Boundaries
- All biometric and cryptographic operations inside TEE
- Raw images discarded immediately
- Minimal data on-chain (commitments only)
- Hardware attestation and tamper response

This architecture enables high-assurance, privacy-preserving biometric identity credentials in a deployable terminal form factor.