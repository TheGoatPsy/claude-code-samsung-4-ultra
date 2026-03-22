---
name: AquaLog v3 - Google Play Yükleme Durumu
description: AquaLog v3 Play Console internal testing aşamasında, hesap onayı bekleniyor (hafta sonu başvuru)
type: project
---

AquaLog v3.0.0 Google Play'e yüklendi ama hesap onayı bekleniyor.

**Build durumu:** AAB hazır, Play Console'a yüklendi (internal testing track)
- Build ID: b54bafb1-f836-49a6-85be-dba4c04177fa
- AAB: https://expo.dev/artifacts/eas/oospvsyPg1HzNFAEZKiNQJ.aab
- Boyut: 26.4 MB
- Version: 3.0.0, versionCode: 4

**Play Console durumu (2026-03-22):**
- Internal testing release oluşturuldu ama hesap onay hatası var
- "There are issues with your account which mean you can't publish changes"
- Hafta sonu başvuru yapıldığı için onay bekleniyor (tahmini Pazartesi-Salı)

**Tamamlanan entegrasyonlar:**
- AdMob (Yunanistan hesabı, pub-6564045764068405), gerçek ad unit ID'leri yerleştirildi
- RevenueCat SDK (test key: test_ytmmfexoVwyvDzsFlnAntxamjdW)
- Abonelik planları: aqualog_monthly ($2.99/ay), aqualog_yearly ($25.99/yıl), entitlement: premium
- Animasyonlu Aquascape splash screen (reanimated)
- app-ads.txt oluşturuldu

**EAS yapılandırması:**
- Expo hesabı: onourimpram (onurb693@gmail.com)
- Proje: @onourimpram/aqua-log (ID: 98a022d1-9f05-4baf-892b-a2e47e374efa)
- Google Service Account: eas-submit@automatic-rite-297118.iam.gserviceaccount.com
- Service account key: google-service-account.json (projede, gitignore'da)
- Google Play Android Developer API: etkinleştirildi
- İlk yükleme manuel yapıldı, sonraki güncellemeler eas submit ile otomatik olacak

**Sonraki adımlar:**
1. Hesap onayı gelince internal testing release'i yayınla
2. Play Console'da store listing, content rating, data safety formlarını doldur
3. 12 tester ile closed testing (14 gün)
4. Production'a başvur
5. Nisan sonu Apple Developer hesabı aç, iOS'a da yükle

**Why:** İlk mobil uygulama yayını, 50 uygulama hedefinin başlangıcı
**How to apply:** Hesap onayı geldiğinde internal testing'den devam et, store listing metinleri hazır
