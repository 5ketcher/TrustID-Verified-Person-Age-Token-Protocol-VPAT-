### VPAT-Global-Profile (v1.0)
**Status:** Open Interoperability Profile  
**Author:** Vojtěch Sejkora  
**Date:** 2025-12-10  

---

# 1. Purpose
This profile defines a minimal global interoperability framework for VPAT deployments
in regions without unified identity regulation.  
It prioritizes flexibility, broad applicability, and technical neutrality.

This profile is intended for:
- multinational platforms  
- global online services  
- decentralized ecosystems  
- markets without strong identity infrastructure  

---

# 2. Allowed Identity Providers

Any IdP MAY issue VPAT tokens if it meets these minimum requirements:

- performs identity verification appropriate for its jurisdiction  
- maintains secure key management (HSM or equivalent recommended)  
- provides a publicly accessible JWKS endpoint  
- publishes transparent issuer metadata  
- complies with local laws related to identity, privacy, and consumer protection  

Permitted IdP types include:
- governments  
- telecom operators  
- regulated KYC/AML providers  
- financial institutions  
- private identity providers  
- decentralized identity systems (DID-based)  

---

# 3. Required Assurance Levels (IAL)

`assurance_level` MAY be one of:

- `"low"`  
- `"substantial"`  
- `"high"`  

Relying Parties MUST evaluate LoA based on their own risk requirements.

---

# 4. Required Claims

Tokens MUST include:

- `real_person = true`  
- `issuer_country`  
- `issuer_type`  
- `policy_profile = "vpat-global-1.0"`  

Other claims MAY be included depending on IdP capabilities.

---

# 5. Cryptographic Requirements

- ES256 or RS256 MUST be supported  
- JWKS endpoint MUST use HTTPS  
- Key rotation every 365 days is RECOMMENDED  
- Keys MUST be generated using a CSPRNG  

---

# 6. Revocation Requirements

IdPs MUST support:

- token revocation  
- compromised key revocation  
- status verification via API  

---

# 7. Relying Party Requirements

RPs MUST:

- evaluate issuer metadata  
- apply their own trust policy  
- consider regulatory obligations for each region served  
- reject tokens failing structural or cryptographic validation  

---

# 8. Version
```
policy_profile = "vpat-global-1.0"
```

---

# End of VPAT-Global-Profile
