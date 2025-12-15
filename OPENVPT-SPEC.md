# OpenVPT: Verified Person & Age Token Protocol (VPT)
**Draft Version:** 1.1  
**Status:** Public Working Draft  
**Date:** 2025-12-10  

**Primary Author:**  
**Vojtěch Sejkora**  
Czech Republic  

---

## Copyright & License
Copyright © 2025 **Vojtěch Sejkora**

This specification is released under the **Apache License 2.0**.

This means:
- Anyone may read, use, implement, and distribute this specification.  
- Attribution to the original author is required.  
- Implementations may be commercial or non-commercial.  

Full license text: https://www.apache.org/licenses/LICENSE-2.0

---

# Abstract

**OpenVPT** (Open Verified Person Token) defines the **Verified Person & Age Token (VPT)** protocol — an open, minimal-disclosure mechanism for verifying human authenticity and age category on online platforms.

The protocol enables Identity Providers (IdPs) to issue compact, privacy-preserving JWT tokens containing boolean or bracketed claims such as:
- `verified_person = true`  
- `age_over_18 = true`  
- `trust_level = 3`  
- `device_certified = true`  

No personal data (name, date of birth, national identifier, address) is ever shared with Relying Parties.

VPT tokens help platforms reduce:
- fake accounts  
- botnets  
- synthetic identities  
- underage access  
- deepfake misuse  

The OpenVPT protocol is designed to align with eIDAS 2.0, the EU Digital Identity Wallet, and compatible global identity frameworks.

---

# 1. Introduction

This document defines the **OpenVPT Verified Person & Age Token Protocol (VPT)**, an interoperable mechanism allowing online platforms (Relying Parties) to validate:

- that a user is a real, verified human,  
- the user's verified age bracket,  
- the trust or assurance level certified by an Identity Provider,  
- optional device authenticity signals.

OpenVPT uses JWT, JOSE, and JWKS for cryptographic security and interoperability.

The protocol is intended for use by:
- social networks  
- gaming platforms  
- content platforms  
- anonymity-sensitive communities  
- AI-moderated or large-scale digital networks  

---

# 2. Terminology

| Term | Definition |

