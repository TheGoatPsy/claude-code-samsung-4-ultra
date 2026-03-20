---
name: GitHub Student Pack - Full Integration Map
description: 15 aracin Claude Code entegrasyonu, CLI kurulumlar, config dosyalari, Python SDK'lar, CI/CD pipeline
type: project
---

GitHub Student Developer Pack entegrasyonu 2026-03-20'de Samsung 4 Ultra bilgisayara kuruldu.

**Why:** Diger bilgisayardaki OpenClaw/Hezarfen konfigurasyonlari bu cihaza migrate edildi + yeni araclar eklendi.

**How to apply:** HZF repo (hzf-v6-supertango) merkezi entegrasyon noktasi. `python/hzf_integrations.py` tum servisleri tek noktadan baslatir. `scripts/verify_integrations.py` durumu kontrol eder.

## Kurulan CLI Araclar (Samsung 4 Ultra)
- Doppler CLI v3.75.3 (winget, login bekliyor)
- Sentry CLI v3.3.3 (npm global)
- GitHub CLI v2.88.1 (winget, codespace scope eklendi)
- DigitalOcean CLI / doctl (winget)
- Heroku CLI (winget)
- Git v2.53.0
- Node.js v24.14.0
- Python 3.14.3

## Kurulan Python SDK'lar
- sentry-sdk 2.55.0
- newrelic 12.0.0
- datadog 0.52.1
- configcat-client 10.0.0
- requests 2.32.5

## HZF Repo'ya Eklenen Dosyalar (2026-03-20)
- `.codecov.yml` - PR coverage raporlari
- `.env.example` - 20+ env var belgesi
- `configcat.json` - 5 feature flag tanimi
- `python/hzf_integrations.py` - Merkezi entegrasyon hub (Sentry, NR, DD, ConfigCat, Notion, Appwrite, MongoDB)
- `scripts/verify_integrations.py` - Dogrulama scripti
- `Procfile` - Heroku deploy
- `app.json` - Heroku app manifest
- `.do/app.yaml` - DigitalOcean App Platform spec
- `.devcontainer/devcontainer.json` - Guncellendi (docker-in-docker, node, SDK'lar eklendi)
- `.github/workflows/quality_gate.yml` - ConfigCat + Sentry release eklendi

## GitHub Repo Secrets (11 adet)
APPWRITE_API_SECRET, APPWRITE_PROJECT_ID, BLACKFIRE_ENV_ID, CODECOV_TOKEN, CODESCENE_PROJECT_ID, CONFIGCAT_SDK_KEY, DEEPSCAN_TEAM_ID, NEW_RELIC_ACCOUNT_ID, NEW_RELIC_LICENSE_KEY, NOTION_API_KEY, PAGECLIP_API_KEY

## 15 Arac Entegrasyon Haritasi
1. Sentry - Python SDK + CI release tracking + CLI
2. New Relic - Python agent + newrelic.ini + APM
3. Datadog - Python SDK + metrik/event API
4. ConfigCat - Python SDK + configcat.json fallback
5. Codecov - .codecov.yml + GitHub Actions
6. CodeScene - GitHub App + Project #77690
7. DeepScan - Team #29212 + quality_gate.yml
8. Imgbot - .imgbotconfig (weekly, aggressive)
9. Doppler - CLI + secret injection
10. Notion - REST API + NOTION_API_KEY
11. Appwrite - REST API + fra.cloud.appwrite.io
12. MongoDB Atlas - pymongo client (claim bekliyor)
13. GitHub Codespaces - devcontainer.json (full stack)
14. Heroku - Procfile + app.json + CLI
15. DigitalOcean - .do/app.yaml + doctl CLI

## Claim Bekleyenler
Sentry DSN, Datadog API key, MongoDB URI, DigitalOcean token, Heroku API key
Doppler login (PowerShell'den)
