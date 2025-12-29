## Sunderland-ZIP is a protocol for decentralized digital identity management

![logo](./img/logo.jpg)

It allows individuals to generate, store, and verify claims about themselves—such as age, citizenship, and academic achievements—without relying on centralized registries or third parties.

Verification is implemented through zero-knowledge proofs (ZKPs): the verifying party can verify the correctness of the claim without accessing the source data or requiring the disclosure of personal information. Proof schemes are tied to cryptographically derived identifiers (e.g., DID) controlled by the owner.

The project is at a very early stage of development. 
The current goal is to implement a minimal but complete proof-of-concept, including: 
    issuance of autonomous verifiable credentials,
    generation and verification of ZK-proofs (e.g., age ≥ 18),
    complete user control over keys and data without external dependencies.

How and where the project will develop is still unknown. It is also unclear whether it will comply with any government standards. The repository exists to test the technical feasibility of the idea.

I am doing this because the idea interests me and it would be great to implement it. So far, the “success” is a working POC that allows, for example, to confirm “I am ≥18” without revealing my date of birth. If something more grows out of this, great. If not, at least the diagrams will remain correct and reusable.

Constructive comments, suggestions for threat modeling, and help with testing are especially important at this stage.

## Examples / Additional modules

[**Sunderland-ZIP-Migrant-module**](examples/rzip-migrant-zk/README.md) - System for verifying the migration status of foreign citizens in Russia using the Zero-Knowledge Identity Protocol. 

## Installation

For this, you need Rust 1.70+ [(link)](https://rustup.rs/)

```
# Clone the repository
git clone https://github.com/Tokyo-09/Sunderland-Zero-Knowledge_Identity_Protocol.git
cd Sunderland-Zero-Knowledge_Identity_Protocol

# Build the project
cargo build --release
```
All done!

## Usage

```
.\szip-cli.exe --help
Usage: szip-cli.exe <COMMAND>

Commands:
  create-did  Create a DID
  prove-age   Generate ZK age proof
  verify      Verify a proof file
  help        Print this message or the help of the given subcommand(s)

Options:
  -h, --help     Print help
  -V, --version  Print version
```

```
$ .\szip-cli.exe create-did --method rzip --id test
✅ DID created: did:rzip:test

$ .\szip-cli.exe prove-age --age 19 --subject-did did:rzip:test
✅ Proof created: age_proof_19.json
📊 Commitment: 2eabba5d
🔒 Proves: age ≥ 18
⏱️  Proof size: 5773 bytes
🕒 Generation: 255.8349ms
🕒 Verification: 42.1504ms

$ .\szip-cli.exe verify --file .\age_proof_19.json
🔍 Verifying proof from .\age_proof_19.json...
✅ Proof is VALID
🎉 Subject is ≥ 18 years old
👤 DID: did:rzip:test
📅 Issued: 2025-12-25T15:55:38.401391700+00:00
🕒 Verification time: 51.5627ms
```

## Demo

![Demo0](./img/showcase0.jpg)

![Demo1](./img/showcase1.jpg)
