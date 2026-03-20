---
name: GitHub Student Pack Entegrasyonu
description: GitHub Student Developer Pack araclari, HZF repo entegrasyonlari, aktif servisler ve claim durumu
type: project
---

GitHub Student Pack entegrasyonu 2026-03-20'de bu bilgisayara migrate edildi.

**Why:** Diger bilgisayarda OpenClaw/Hezarfen tarafindan yapilandirilan 15+ arac, bu Samsung bilgisayara da kuruldu.

**How to apply:** HZF repo (hzf-v6-supertango) ana entegrasyon noktasi. quality_gate.yml tum CI/CD pipeline'i yonetiyor. Secret'lar GitHub repo settings'te, env var'lar Doppler'da.

## Aktif Servisler (config dosyalari mevcut)
- Doppler CLI v3.75.3 (login bekliyor)
- New Relic (newrelic.ini)
- Imgbot (.imgbotconfig, weekly aggressive)
- Codecov (.codecov.yml, quality_gate.yml)
- CodeScene Project #77690
- DeepScan Team #29212
- ConfigCat (configcat.json)
- Sentry (quality_gate.yml, claim bekliyor)
- Blackfire + LocalStack (docker-compose.local.yml)
- Appwrite fra.cloud (popsql_connections.json)
- Scrapy/Zyte Project #926627
- Termius Pro (termius_config.stub)
- JetBrains (.idea/misc.xml)
- PopSQL (popsql_connections.json)

## GitHub Repo Secrets (14 adet, 2026-03-21)
APPWRITE_API_SECRET, APPWRITE_PROJECT_ID, BLACKFIRE_ENV_ID, CODECOV_TOKEN, CODESCENE_PROJECT_ID, CONFIGCAT_SDK_KEY, DD_API_KEY, DEEPSCAN_TEAM_ID, HEROKU_API_KEY, NEW_RELIC_ACCOUNT_ID, NEW_RELIC_LICENSE_KEY, NOTION_API_KEY, PAGECLIP_API_KEY, SENTRY_AUTH_TOKEN

## Secret Durumu (2026-03-21)
- Sentry: AKTIF (auth token eklendi)
- Datadog: AKTIF (API key eklendi)
- Heroku: BEKLEMEDE (ogrenci onay bekliyor)
- MongoDB Atlas: HATA (GITHUBSTUDENT50-PX05WT kodu var, kimlik saglayici hatasi)
- DigitalOcean: HATA (odeme yontemi reddedildi, $200 kredi alinmadi)
- Doppler: CLI kuruldu, login bekliyor

## Mobil Uygulama Gelistirme Araclari (Student Pack)
LambdaTest (1 yil, mobil test), BrowserStack (1 yil, 2000+ cihaz), Azure ($100 kredi), NativeScript (acik kaynak), FrontendMasters (6 ay kurs), Flutter (acik kaynak), Codespaces Pro, Stripe ($1000 waived), Appwrite (Pro tier)

## 50 Mobil Uygulama Projesi (2026 Hedefi)
Niche SaaS mobil uygulamalar gelistirilecek, ek gelir icin. Detaylar: project_mobile_apps_2026.md
