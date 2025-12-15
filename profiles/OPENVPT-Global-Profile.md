### OpenVPT-Global-Profile (v1.0)
**Status:** Open Interoperability Profile  
**Author:** Vojtěch Sejkora  
**Date:** 2025-12-10  

---

# 1. Purpose

This profile defines a minimal global interoperability framework for
**OpenVPT (Open Verified Person Token)** deployments in regions without
a unified or regulated digital identity framework.

It prioritizes flexibility, broad applicability, and technical neutrality.

This profile is intended for:
- multinational platforms  
- global online services  
- decentralized ecosystems  
- markets without strong identity infrastructure  

---

# 2. Allowed Identity Providers

Any Identity Provider (IdP) MAY issue **VPT tokens** under this profile
if it meets the following minimum requirements:

- performs identity verification appropriate for its jurisdiction  
- maintains secure key management (HSM or equivalent recommended)  
- provides a publicly accessible JWKS endpoint  
- publishes transparent issuer metadata  
- complies with applicable local laws related to identity, privacy,
  and consumer protection  

Permitted IdP categories include:
- government identity providers  
- telecom operators  
- regulated KYC/AML providers  
- financial institutions  
- private identity providers  
- decentralized identity systems (e.g. DID-based)  

---

# 3. Required Assurance Levels (LoA)

The `assurance_level` claim MAY be one of:

- `"low"`  
- `"substantial"`  
- `"high"`  

Relying Parties MUST evaluate the assurance level according to their
own risk model, regulatory obligations, and use case requirements.

---

# 4. Required Claims

VPT tokens issued under this profile MUST include:

- `real_person = true`  
- `issuer_country`  
- `issuer_type`  
- `policy_profile = "openvpt-global-1.0"`  

Additional claims MAY be included depending on Identity Provider
capabilities and local requirements.

---

# 5. Cryptographic Requirements

Identity Providers issuing tokens under this profile MUST ensure that:

- **ES256** or **RS256** signing algorithms are supported  
- the JWKS endpoint is accessible exclusively over **HTTPS**  
- signing keys are generated using a **cryptographically secure random
  number generator (CSPRNG)**  

Key rotation at least every **365 days** is RECOMMENDED.

---

# 6. Revocation Requirements

Identity Providers MUST support:

- token revocation  
- compromised key revocation  
- token or account status verification via API  

---

# 7. Relying Party Requirements

Relying Parties (RPs) accepting this profile MUST:

- evaluate issuer metadata and declared assurance level  
- apply their own Trust Policy when accepting tokens  
- consider regulatory obligations for each served jurisdiction  
- reject tokens that fail structural, cryptographic, or signature
  validation  

---

# 8. Versioning

This profile is uniquely identified by:

policy_profile = "openvpt-global-1.0"  

---

# End of OpenVPT-Global-Profile
