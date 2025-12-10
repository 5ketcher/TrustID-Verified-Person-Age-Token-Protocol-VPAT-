### VPAT-US-Profile (v1.0)
**Status:** Regional Profile — United States  
**Author:** Vojtěch Sejkora  
**Date:** 2025-12-10  

---

# 1. Purpose
This profile defines rules for VPAT deployments in the United States,
reflecting the decentralized structure of U.S. identity verification.  
It aligns explicitly with:

- **NIST SP 800-63A (Identity Assurance)**  
- **NIST SP 800-63B (Authentication Assurance)**  
- **NIST SP 800-63C (Federation Assurance)**  

---

# 2. Allowed Identity Providers

IdPs MUST be one of:

- U.S. state-issued identity systems (DMV, state ID)  
- NIST-compliant identity providers  
- U.S.-regulated KYC/AML providers  
- Banks and financial institutions  
- Mobile carriers with validated subscriber identity  
- Government contractors certified under NIST 800-63  

IdPs MUST disclose identity verification methods and comply with applicable federal and state regulations.

---

# 3. Required Assurance Levels (IAL)

`assurance_level` MUST follow **NIST SP 800-63A IAL**:

Allowed:
- **"ial2"**  
- **"ial3"**

Tokens with **"ial1"** MUST be rejected for real-person verification.

---

# 4. Authentication Assurance Requirements (AAL)

The authentication event used during verification MUST comply with **NIST SP 800-63B**:

- For IAL2 identity: **AAL2** is RECOMMENDED  
- For IAL3 identity: **AAL3** is REQUIRED  

Acceptable AAL2 methods include MFA with possession + knowledge or possession + biometrics.

---

# 5. Federation Assurance Requirements (FAL)

VPAT token issuance aligns with:

- **NIST SP 800-63C FAL1**: signed assertions (minimum requirement)

Higher levels (FAL2, FAL3) MAY be used by deployments requiring encryption or hardware-backed key material.

---

# 6. Required Claims

Tokens MUST include:

- `real_person = true`  
- `issuer_country = "US"`  
- `policy_profile = "vpat-us-1.0"`  
- `assurance_level` with a valid IAL value  

Age verification MUST follow U.S. compliance rules (COPPA, state laws, California regulations, etc.).

---

# 7. Cryptographic Requirements

- ES256 or ES384 RECOMMENDED  
- RS256 (≥2048-bit) MAY be used  
- Key rotation required every **180 days**  
- JWKS endpoint MUST use HTTPS  

---

# 8. Revocation Requirements

IdPs MUST follow **NIST revocation best practices**, including:

- token revocation  
- credential compromise response  
- fraud reporting channels  
- continuous monitoring  

---

# 9. Relying Party Requirements

RPs MUST:

- enforce U.S.-specific age rules  
- validate issuer metadata  
- validate IAL/AAL/FAL where required  
- follow applicable state and federal privacy laws  
- reject tokens not matching `policy_profile = "vpat-us-1.0"`  

---

# 10. Version
```
policy_profile = "vpat-us-1.0"
```

---

# End of VPAT-US-Profile
