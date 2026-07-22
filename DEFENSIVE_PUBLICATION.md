# Defensive Publication: Starlight LITE (TFBIA) — Hardware-Rooted Face Biometric Soulbound Token Issuance System

**Publication Date:** July 22, 2026  
**Author:** Shoel Lowy (and contributors)  
**This is a defensive publication to establish prior art.**

## Abstract

Starlight LITE is a compact, hardware-rooted terminal and protocol for authoritative issuance of non-transferable Soulbound Tokens (SBTs) that cryptographically bind verified live facial biometrics to a user-controlled blockchain identity. The system performs on-device liveness detection, template protection via BioHash cancelable transforms and fuzzy commitment schemes, post-quantum cryptographic commitments and signatures, and issues an SBT containing a hash commitment to the protected biometric template. It enables privacy-preserving, revocable, and verifiable one-person-one-credential proofs for national security, government research, and high-assurance identity applications.

## Problem Statement

Existing biometric identity systems for government and high-security contexts suffer from irreversible template compromise, transferable or centrally controlled credentials, weak integration with decentralized identity layers, and insufficient post-quantum security. There is a need for a deployable edge device and protocol that combines strong presentation attack detection, revocable template protection, post-quantum cryptography, and binding to non-transferable on-chain credentials in a single coherent system.

## Background

Traditional biometric eID and access control systems rely on centralized storage of raw or lightly protected templates. Commercial solutions often lack seamless blockchain integration or revocable template protection. Research on fuzzy vaults and cancelable biometrics exists but is rarely combined with post-quantum signatures, succinct ZK options, and authoritative SBT issuance in a production-grade terminal suitable for national-security environments.

## Novel Aspects

Starlight LITE unifies in a single deployable system:

- Multi-modal face capture with ISO 30107-compliant liveness and morph detection on a compact terminal.
- BioHash cancelable biometric transform feeding into a BCH-based fuzzy commitment scheme for template protection.
- On-device generation of SHA-3 hash commitments to the protected template inside a Trusted Execution Environment.
- Authority-signed issuance of ERC-5192 / EIP-4973 Soulbound Tokens that bind the commitment to a user wallet or DID.
- Support for revocation via on-chain registry and optional succinct ZK proofs for verification.
- Post-quantum signature suite (Dilithium/Falcon) and hardware attestation chain.

The system is specifically engineered as a production terminal rather than a purely theoretical construction, with explicit support for air-gapped or high-assurance deployment patterns.

## Technical Description (Enabling Disclosure)

### Hardware Platform
Compact vertical wedge terminal with RGB + NIR/ToF depth cameras, NPU-equipped processor (e.g., Rockchip RV1126B-class or equivalent), Trusted Execution Environment (AMD SEV-SNP or equivalent), dedicated secure element/HSM, PoE connectivity, tamper sensors, and encrypted storage.

### Biometric Processing Sequence (Enrollment)
1. Multi-frame capture with liveness and presentation attack detection.
2. Quality scoring and feature extraction (ArcFace/CosFace embeddings).
3. BioHash cancelable transform (random projection + thresholding).
4. Fuzzy commitment generation using BCH codes inside the TEE.
5. SHA-3 hash commitment to the protected template.
6. 1:N deduplication against existing protected templates (policy-driven).
7. Authority attestation (Dilithium signature) and SBT minting.

### Verification Sequence
Fresh capture + liveness → BioHash + fuzzy commitment reconstruction in TEE → attested match or succinct ZK proof against on-chain commitment → on-chain SBT and revocation registry check.

### Cryptographic & Identity Layer
- Hash-based commitments (SHA-3) for post-quantum compatibility.
- Post-quantum signatures (CRYSTALS-Dilithium preferred).
- Soulbound Tokens (ERC-5192 minimal soulbound or EIP-4973 account-bound semantics).
- Binding to user-controlled wallet or Decentralized Identifier (DID).
- On-chain revocation registry.

### Software Architecture
Security-critical components in Rust; biometric orchestration and model inference in Python with NPU acceleration; chain-agnostic integration for SBT contracts and revocation registry.

The above description, together with the referenced tech stack, constitutes an enabling disclosure sufficient for a person skilled in the art of secure biometric systems and blockchain identity to understand and implement the core concepts.

## High-Level Claims (Defensive Form)

1. A method and system for authoritative issuance of non-transferable on-chain credentials cryptographically bound to protected facial biometric templates using on-device TEE processing, BioHash cancelable transforms, and fuzzy commitment schemes.

2. A terminal device performing the method of claim 1, comprising multi-modal face capture with liveness detection, hardware-rooted template protection, and direct credential issuance with post-quantum signatures.

3. Use of hash-based cryptographic commitments combined with authority-signed non-transferable tokens for revocable, verifiable bio-cryptographic identity proofs without exposing raw biometric data.

4. Integration of on-device fuzzy commitment with on-chain revocation registry and optional succinct ZK proofs.

5. A complete hardware-software stack enabling the above in a compact, tamper-evident, air-gap compatible form factor suitable for national security and government research deployments.

## Publication and Archiving Instructions

This document is published as a defensive disclosure to establish prior art. Recommended actions:
1. Create a public GitHub repository.
2. Commit this file with a clear dated commit message.
3. Immediately archive the repository URL and raw file URL using the Internet Archive Wayback Machine “Save Page Now” feature.

This publication is made available under CC0 1.0 (Public Domain Dedication).

---

**End of Defensive Publication**

*This document is intended solely as a defensive publication to prevent others from obtaining patent rights over the described subject matter. It does not constitute an offer to license or any other legal commitment.*