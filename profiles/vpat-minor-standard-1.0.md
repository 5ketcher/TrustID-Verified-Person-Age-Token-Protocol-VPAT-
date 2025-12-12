
# VPAT Minor Standard 1.0
Privacy-Preserving Age Verification for Minors

Status: Experimental Policy Profile  
Version: 1.0  
Date: 2025-12-10  
Part of: TrustID VPAT Protocol  
Author: Vojtěch Sejkora  

---

## 1. Purpose
The VPAT Minor Standard defines a constrained, privacy-first profile of the TrustID VPAT protocol for minor subjects.
It enables age-based access control without creating persistent child identities.

---

## 2. Scope
Applies to subjects under the age of majority where only age category verification is required.
This standard does not define child digital identity.

---

## 3. Roles

### 3.1 Subject (Minor)
- No persistent account
- Uses a pseudonymous handle
- No recovery mechanism

### 3.2 Legal Guardian
- Authorizes age attestation
- Authenticates only with an external authority
- Not identifiable to Issuer or RP

### 3.3 Age Attestation Authority (AAA)
- Regulated bank, national eID, or EUDI Wallet
- Returns only age bracket, assurance, validity
- Never issues VPAT tokens

### 3.4 VPAT Issuer (IdP)
- Issues VPAT tokens
- Stores no personal data
- Relies solely on age attestations

### 3.5 Relying Party (RP)
- Consumes VPAT tokens
- Cannot correlate users
- Receives no guardian or bank data

---

## 4. Core Principles
- Age-only verification
- No persistent identity
- No cross-platform correlation
- No recovery
- Minimal retention

---

## 5. Pseudonym Model

### 5.1 Internal Handle
- Generated randomly
- Stored locally on device
- Loss equals loss of continuity

### 5.2 Pairwise Identifiers
- Token `sub` MUST be pairwise per RP
- No global identifiers allowed

---

## 6. Verification Flow
1. Subject initiates verification via RP
2. Redirect to Issuer
3. Pseudonym created
4. Guardian authenticates with AAA
5. AAA evaluates age
6. AAA returns age bracket + validity
7. Issuer records attestation
8. Issuer issues VPAT token

---

## 7. Token Requirements

### Mandatory Claims
- iss, sub, iat, exp, jti, policy_profile

### Allowed Claims
- age_bracket
- age_13_plus / age_15_plus
- assurance_level
- issuer_type
- issuer_country

### Prohibited Claims
- real_person = true
- verified_person = true
- biometrics
- identity hashes
- device identifiers

---

## 8. Example Token

```json
{
  "iss": "https://issuer.example",
  "sub": "pairwise-sub-fb",
  "aud": "facebook.com",
  "iat": 1735689600,
  "exp": 1735689900,
  "jti": "a9f3c1e2",
  "policy_profile": "vpat-minors-1.0",
  "age_bracket": "13+",
  "assurance_level": "high",
  "issuer_type": "bank",
  "issuer_country": "CZ"
}
```

---

## 9. Validity & Renewal
- Attestations SHOULD be short-lived (e.g. 6 months)
- Tokens MUST be short-lived (minutes)
- Renewal requires new guardian authorization

---

## 10. Device & Continuity
- Continuity based on handle possession
- No device registry
- Explicit transfer MAY be supported
- Loss requires re-verification

---

## 11. Data Retention
- Minimal storage only
- No guardian data
- No platform mappings
- Delete pseudonym after expiry + grace period

---

## 12. Security Considerations
Privacy and non-linkability take precedence over convenience.

---

## 13. Relationship to Adult Profiles
Adult profiles may support accounts and recovery.
Minor profiles MUST NOT.

---

## 14. Future Evolution
Designed as a transitional model.
May integrate regulated age credentials in the future.

---

## 15. Final Statement
The VPAT Minor Standard does not identify children.
It defines only what systems may responsibly know about them.
