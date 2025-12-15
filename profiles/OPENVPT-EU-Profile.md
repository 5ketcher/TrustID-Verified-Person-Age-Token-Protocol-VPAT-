### OpenVPT-EU-Profile (v1.0)
**Status:** Proposed Profile for EU-compatible deployments  
**Author:** Vojtěch Sejkora  
**Date:** 2025-12-10  

---

# 1. Purpose

This profile defines the rules, assurance levels, and allowed Identity Providers (IdPs)
for deployments of the **OpenVPT (Open Verified Person Token)** standard within the
European Union.

This profile aligns with:
- eIDAS 2.0  
- EU Digital Identity Wallet (EUDI)  
- regulated KYC/AML identity providers  
- EU cybersecurity and privacy directives  
- EU digital trust framework governance  

---

# 2. Allowed Identity Providers

An Identity Provider (IdP) MUST fall into one of the following regulated categories:

- EU Member State **eIDAS-notified** Identity Provider  
- **Qualified** EU Digital Identity Wallet Provider  
- Licensed **KYC/AML provider** operating under EU regulation  
- EU-based **financial institution** (bank)  
- EU **telecom operator** complying with SIM registration requirements  

IdPs SHOULD be qualified or notified under the eIDAS trust framework where applicable.  
Unregulated or non-EU IdPs MUST NOT issue **VPT tokens** under this profile.

---

# 3. Required Assurance Levels (LoA)

Tokens issued under this profile MUST contain one of the following:

- `assurance_level = "substantial"`  
- `assurance_level = "high"`

Tokens with `assurance_level = "low"` MUST be rejected by Relying Parties.

The `assurance_level` MUST follow the **eIDAS 2.0 Level of Assurance model**.

The authentication event used to verify identity MUST meet the requirements of the
**EUDI Wallet High-Level Architecture**, including strong authentication consistent
with EU standards.

---

# 4. Required Token Claims

VPT tokens issued under this profile MUST include:

- `real_person = true`  
- `age_bracket` OR an age-bound claim (`age_over_*`)  
- `issuer_country` = ISO-3166 code of an EU Member State  
- `policy_profile = "openvpt-eu-1.0"`  
- `issuer_type` = regulated provider category  

The `issuer_type` MUST reflect the IdP class, for example:
`"government"`, `"wallet_provider"`, `"bank"`, `"kyc_provider"`, `"telecom"`.

---

# 5. Cryptographic Requirements

The Identity Provider MUST:

- sign tokens using **ES256**, **ES384**, or **RS256** (≥2048-bit keys)  
- rotate signing keys at least every **180 days**  
- publish a JWKS endpoint accessible **exclusively over HTTPS**  
- generate signing keys using a **cryptographically secure random number generator (CSPRNG)**  
- protect private keys using **HSM** or equivalent secure key storage  

If the IdP is an **EU Digital Identity Wallet Provider**, cryptographic material
MUST comply with the **EUDI Wallet technical architecture**, including qualified
electronic seal or signature requirements where applicable.

---

# 6. Revocation Requirements

The Identity Provider MUST:

- support token revocation lookup via API  
- maintain a list of revoked accounts and devices  
- immediately revoke tokens upon identity compromise  
- ensure revocation endpoints meet EU availability and reliability expectations  

---

# 7. Relying Party Requirements

A Relying Party (RP) accepting this profile MUST:

- reject tokens without `policy_profile = "openvpt-eu-1.0"`  
- reject tokens issued by non-EU Identity Providers  
- validate assurance level and issuer metadata  
- enforce minimum age verification according to EU and Member State law  
- verify cryptographic signatures using the IdP JWKS  
- reject tokens issued by IdPs suspended or revoked under EU trust frameworks  

---

# 8. Versioning

This profile is uniquely identified by:  
policy_profile = "openvpt-eu-1.0"

---

# End of OpenVPT-EU-Profile


