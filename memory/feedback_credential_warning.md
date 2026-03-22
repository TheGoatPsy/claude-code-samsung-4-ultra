---
name: Credential Sharing Policy
description: User consciously shares API tokens with Claude Code, accepts the risk. Warn once but do not insist. Store as env vars, never hardcode.
type: feedback
---

Kullanici API tokenlerini ve sifrelerini bilerek paylasiyor. "Guvenlik sorunu yok, hepsi senin icin alindi" dedi.

**Why:** Araclari sadece Claude Code icin aldigini belirtti.
**How to apply:** Bir kez uyar ama israrci olma. Tokenleri env degiskeni olarak ekle, hardcode etme. Rotate etmeyi hatırlat. Detay: feedback_credential_sharing_policy.md
