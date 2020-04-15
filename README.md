# SAN DID Method Specification

Version: 0.1

Note: This specification will be updated and the version number will be bumped.

The system aims to provide secure authentication and various health services based on the SAN blockchain and DID & Verifiable Credential Specifications published by the W3C.

[Decentralized Identifiers (DIDs) v1.0](https://w3c.github.io/did-core/#interoperability-registries)

## 1. SAN DID

The namestring that shall identify this DID method is: san

```
did:san:<method-specific-id>

did:san:abcdefgh1234
```

method-specific-id = 12 characters long and contains the characters a-z and 1–5

Basic DID Document:
```
{
  "@context": "https://w3id.org/did/v1",
  "publicKey": [
    {
      "id": "#keys-1",
      "type": "EcdsaSecp256k1Signature2019",
      "publicKeyBase58": "H3C2AVvLMv6gmMNam3uVAjZpfkcJCwDwnZn6z3wXmqPV"
    },
    {
      "id": "#keys-2",
      "type": "EcdsaSecp256k1Signature2019",
      "publicKeyBase58": "H3C2AVvLMv6gmMNam3uVAjZpfkcJCwDwnZn6z3wXmqPV"
    }
  ],
  "authentication": ["#key-1"],
  "recovery": ["#key-2"],
  "created":< Created Date of DID Document>,
  "updated":< Created Date of DID Document>
}
```

## 2. Method Operation

The following section defines the operations supported to manage DIDs.


### 2.1 Create

A DID can be created by performing an HTTP POST.

Request:

```
{
    "did": "did:san:abcdefgh1234",
    "document": {
        "@context": "https://w3id.org/did/v1",
        "id": "did:san:abcdefgh1234",
        "version": 1,
        "created": "2020-04-14T00:00:00.961Z",
        "updated": "2020-04-14T00:00:00.961Z",
        "publicKey": [
            {
                "id": "did:san:abcdefgh1234#key-1",
                "type": "EcdsaSecp256k1Signature2019",
                "publicKeyBase58": "H3C2AVvLMv6gmMNam3uVAjZpfkcJCwDwnZn6z3wXmqPV"
            },
            {
                "id": "did:san:abcdefgh1234#key-2",
                "type": "EcdsaSecp256k1Signature2019",
                "publicKeyBase58": "H3C2AVvLMv6gmMNam3uVAjZpfkcJCwDwnZn6z3wXmqPV"
            }
        ],
        "authentication": [
            "did:san:abcdefgh1234#key-1"
        ],
        "recovery": [
            "did:san:abcdefgh1234#key-2"
        ],
        "proof": {
            "type": "EcdsaSecp256k1Signature2019",
            "creator": "did:san:abcdefgh1234#key-1",
            "signatureValue": "3045022100ff51c2629c9eb5d75d9786506ad45e82a87bf91b991a4b37f6d81ce70984220302201f4aa4f609a7ff96de190db68a25603fc849f1098d3f506098dc79af826b4a67"
        }
    },
    "operation": "create",
    "timestamp": 1586936155
}
```

### 2.2 Read

A DID Document can be read by performing an HTTP GET.

Request:

```
curl https://did.baasze.com/v1/did/resolve/did:san:abcdefgh1234
```

Result:

```
{
  "code": 0,
  "message": "ok",
  "content": {
    "didDocument": {
        "@context": "https://w3id.org/did/v1",
        "id": "did:san:abcdefgh1234",
        "version": 1,
        "created": "2020-04-14T00:00:00.961Z",
        "updated": "2020-04-14T00:00:00.961Z",
        "publicKey": [
            {
                "id": "did:san:abcdefgh1234#key-1",
                "type": "EcdsaSecp256k1Signature2019",
                "publicKeyBase58": "H3C2AVvLMv6gmMNam3uVAjZpfkcJCwDwnZn6z3wXmqPV"
            },
            {
                "id": "did:san:abcdefgh1234#key-2",
                "type": "EcdsaSecp256k1Signature2019",
                "publicKeyBase58": "H3C2AVvLMv6gmMNam3uVAjZpfkcJCwDwnZn6z3wXmqPV"
            }
        ],
        "authentication": [
            "did:san:abcdefgh1234#key-1"
        ],
        "recovery": [
            "did:san:abcdefgh1234#key-2"
        ],
        "proof": {
            "type": "EcdsaSecp256k1Signature2019",
            "creator": "did:san:abcdefgh1234#key-1",
            "signatureValue": "3045022100ff51c2629c9eb5d75d9786506ad45e82a87bf91b991a4b37f6d81ce70984220302201f4aa4f609a7ff96de190db68a25603fc849f1098d3f506098dc79af826b4a67"
        }
    }
  }
}
```

### 2.3 Update

A DID document can be updated by performing an HTTP POST.

Request:

```
{
    "did": "did:san:abcdefgh1234",
    "document": {
        "@context": "https://w3id.org/did/v1",
        "id": "did:san:abcdefgh1234",
        "version": 1,
        "created": "2020-04-14T00:00:00.961Z",
        "updated": "2020-04-14T00:00:00.961Z",
        "publicKey": [
            {
                "id": "did:san:abcdefgh1234#key-1",
                "type": "EcdsaSecp256k1Signature2019",
                "publicKeyBase58": "H3C2AVvLMv6gmMNam3uVAjZpfkcJCwDwnZn6z3wXmqPV"
            },
            {
                "id": "did:san:abcdefgh1234#key-2",
                "type": "EcdsaSecp256k1Signature2019",
                "publicKeyBase58": "H3C2AVvLMv6gmMNam3uVAjZpfkcJCwDwnZn6z3wXmqPV"
            }
        ],
        "authentication": [
            "did:san:abcdefgh1234#key-1"
        ],
        "recovery": [
            "did:san:abcdefgh1234#key-2"
        ],
        "proof": {
            "type": "EcdsaSecp256k1Signature2019",
            "creator": "did:san:abcdefgh1234#key-1",
            "signatureValue": "3045022100ff51c2629c9eb5d75d9786506ad45e82a87bf91b991a4b37f6d81ce70984220302201f4aa4f609a7ff96de190db68a25603fc849f1098d3f506098dc79af826b4a67"
        }
    },
    "operation": "update",
    "timestamp": 1586936155,
    "signature": "212w6nedqdm2wdp2dpdkasxkapp12kw12w12w"
}
```

### 2.4 Revoke
A DID document can be revoked by performing an HTTP POST.

```
{
    "did": "did:san:abcdefgh1234",
    "operation": "revoke",
    "timestamp": 1586936155,
    "signature": "212w6nedqdm2wdp2dpdkasxkapp12kw12w12w"
}
```

## Security considerations

* SAN DID method uses the Byzantine Fault Tolerance-DPoS protocol to reach consensus.
* A DID owner can use recovery key to reset authentication key, but no one can access the verifiable credentials which were issued and encrypted by origin public key.
* SAN DID Document uses ECDSA secp256k1 to prevent malicious tampering.

## Privacy considerations

* The SAN DID method is architected to ensure reduced correlation risk.
* The public key will be used to encrypt data, only those with the private key can decrypt and access the data.
* The private key only exists on the user's device and will not be known to any third party.