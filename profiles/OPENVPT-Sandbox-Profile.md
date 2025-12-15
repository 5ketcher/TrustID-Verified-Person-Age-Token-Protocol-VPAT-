### OpenVPT-Sandbox-Profile (v1.0)
**Status:** Testing & Development Profile  
**Author:** Vojtěch Sejkora  
**Date:** 2025-12-10  

---

# 1. Purpose

This profile defines a fully permissive **OpenVPT (Open Verified Person Token)** configuration
intended exclusively for non-production use, including:

- development environments  
- QA testing  
- integration pilot projects  
- hackathons  
- emulation of Identity Provider (IdP) behavior without real identities  

This profile MUST NOT be used in production environments.

---

# 2. Allowed Identity Providers

Any Identity Provider (IdP) MAY be used under this profile, including:

- mock or testing IdPs  
- local development servers  
- simulated identity systems  
- ephemeral IdPs created during testing  

No regulatory or compliance requirements apply.

---

# 3. Required Assurance Levels (LoA)

There are no required assurance levels under this profile.

Test or mock values are permitted, such as:

- `"test-low"`  
- `"test-medium"`  
- `"mock"`  

---

# 4. Required Claims

VPT tokens issued under this profile MUST include only:

- `policy_profile = "openvpt-sandbox-1.0"`  

All other claims MAY be omitted, mocked, randomized, or simplified as needed
for testing and development purposes.

---

# 5. Cryptographic Requirements

Under this profile:

- signing MAY use test or self-generated keys  
- JWKS MAY be static, local, or non-HTTPS  
- Identity Providers MAY use ephemeral or non-persistent keys  
- no key rotation requirements apply  

---

# 6. Revocation Requirements

Token revocation support is OPTIONAL.

Identity Providers MAY simulate revocation behavior for testing purposes.

---

# 7. Relying Party Requirements

Relying Parties (RPs) MUST treat tokens issued under this profile as
**invalid for production use**.

Use is restricted to controlled development or testing environments only.

---

# 8. Versioning

This profile is uniquely identified by:

```
policy_profile = "openvpt-sandbox-1.0"
```

---

# End of OpenVPT-Sandbox-Profile
