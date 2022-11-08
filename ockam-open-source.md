---
description: Use Ockam Open Source for hacking and personal projects.
---

# Ockam Open Source

<figure><img src=".gitbook/assets/Screen Shot 2022-10-28 at 10.37.03 AM.png" alt=""><figcaption><p>Please click the diagram to see a bigger version.</p></figcaption></figure>

Ockam Open Source tools and programming libraries enable applications to:

* Safely Generate, Store, Rotate and Revoke **Cryptographic Keys.**
* Generate unique cryptographically provable **Identities** and manage private keys in safe **Vaults.**
* Enable **Vault Add-Ons** for various TEEs, TPMs, HSMs, Secure Enclaves, and Cloud KMSs.
* Create **Credential Authorities** to issue lightweight, fine-grained attribute-based credentials**.**
* Securely Issue, Store, Present, and Verify cryptographically verifiable **Credentials**.
* Define and enforce Attribute Based Access Control (ABAC) **Policies**.
* Deliver messages reliably over any Transport topology using - Application Layer **Routing**.
* Create end-to-end encrypted, mutually authenticated, and authorized **Secure Channels** over multi-hop, multi-protocol **Transport** topologies.
* Enable **Transport Add-Ons** for various protocols TCP, UDP, WebSockets, BLE, LoRaWAN etc.
* Securely traverse NATs and protocol gateways using **** end-to-end encrypted **Relays.**&#x20;
* Tunnel any application protocol through mutually authenticated and encrypted **Portals.**
* Operate in **any environment** - cloud virtual machines or constrained embedded devices.
* Integrate deeply using our **rust** **library** or run as an application **sidecar** process or container.
* Licensed under the Apache 2.0 open source license.&#x20;
* Community Support.

### Get Started

#### Homebrew

If you use Homebrew, you can install Ockam using `brew`.

```bash
brew install build-trust/ockam/ockam
```

#### Precompiled Binaries

Otherwise, you can download our latest architecture specific pre-compiled binary by running:

```shell
curl --proto '=https' --tlsv1.2 -sSf https://raw.githubusercontent.com/build-trust/ockam/develop/install.sh | sh
```

After the binary downloads, please move it to a location in your shell's `$PATH`, like `/usr/local/bin`.