---
name: Claude Code Mobil Gelistirme Platformu (Tam Envanter)
description: Claude Code'un mobil uygulama gelistirme platformu olarak yapilandirmasi. MCP sunuculari, plugins, commands, skills, rules, hooks, batch scripts, agent teams, settings detaylari.
type: project
---

Claude Code, 50 niche SaaS mobil uygulama portfoyü icin tam gelistirme platformuna donusturuldu (2026-03-22).

**Why:** AquaLog v3 sonrasi daha buyuk uygulamalar icin altyapi gerekti. Tek seferlik kurulumla her yeni projede sifirdan yapilandirma gereksiz.

**How to apply:** Tum yapilandirma ~/.claude/ altinda. Yeni proje baslatmak icin `/mobile-init uygulama-adi` yeterli. Toplu islemler icin batch scriptleri kullan. Paralel gelistirme icin `/team-dev` kullan.

## MCP Sunuculari (8 adet, global scope ~/.claude.json)

| Sunucu | Paket | Durum | Islem |
|--------|-------|-------|-------|
| Context7 | @upstash/context7-mcp@latest | Calisiyor | Guncel kutuphane dokumanlarini ceker |
| RN-Expo | @divagnz/mcp-react-native-expo | Calisiyor | 933 React Native araci |
| Tavily | tavily-mcp@latest | Calisiyor | Ucretsiz web arama (API key env'de) |
| Figma | figma-mcp | Calisiyor | Tasarimdan koda (API key env'de) |
| Sentry | @sentry/mcp-server --access-token | Yeniden baslatmada calısacak | Hata takibi |
| Playwright | @playwright/mcp | Yeniden baslatmada calısacak | Tarayici otomasyonu |
| Expo | mcp.expo.dev/mcp (HTTP) | Auth gerekli | Ilk kullanımda tarayicida giris |
| Memory | @modelcontextprotocol/server-memory | Calisiyor | Knowledge graph (onceden vardi) |

Ayrica: supermemory (HTTP, auth gerekli), obsidian (Vault bagli), claude.ai connectors (Clinical Trials, Canva, Google Calendar, Indeed, Scholar Gateway, Gamma, PubMed, Bigdata.com).

## Marketplace ve Plugins (3 marketplace, 9 plugin)

**Marketplace'ler:**
- expo-plugins (expo/skills)
- anthropic-agent-skills (anthropics/skills)
- callstack-agent-skills (callstackincubator/agent-skills)

**Kurulu Pluginler:**
- expo, expo-app-design, expo-deployment, upgrading-expo (Expo)
- react-native-best-practices, github-actions, upgrading-react-native (Callstack)
- document-skills, claude-api (Anthropic)

## Custom Slash Commands (10 adet, ~/.claude/commands/)

| Komut | Dosya | Islem |
|-------|-------|-------|
| /mobile-init | mobile-init.md | Yeni Expo projesi + Hezarfen template |
| /build-android | build-android.md | EAS build + submit Android |
| /build-ios | build-ios.md | EAS build + submit iOS |
| /app-checklist | app-checklist.md | Pre-deployment 10 madde dogrulama |
| /test-suite | test-suite.md | tsc + eslint + jest |
| /release-notes | release-notes.md | Git log'dan EN/TR release notes |
| /team-dev | team-dev.md | Agent team: architect + ui-builder + i18n-tester |
| /team-review | team-review.md | Agent team: security + performance + quality |
| /batch-run | batch-run.md | Tum uygulamalarda toplu islem |
| /register-app | register-app.md | claude-projects'e yeni uygulama ekle |

## Custom Skills (3 adet, ~/.claude/skills/)

- **mobile-build**: EAS build + submit + release notes (Bash(eas:*), Bash(npx:*))
- **rn-feature**: Feature modulu scaffold (screens, hooks, types, tests)
- **store-listing**: Play Console / App Store metadata 8 dilde

## Conditional Rules (3 adet, ~/.claude/rules/)

- **testing.md**: Jest + RNTL standartlari (*.test.ts, *.test.tsx)
- **monetization.md**: API key koruma, isPremium check, RevenueCat (monetization/**, Paywall*, AdBanner*)
- **batch-scripts.md**: max-budget-usd zorunlu, MAX_PARALLEL=3, app.json kontrolu

## Batch Scripts (3 adet, ~/.claude/scripts/, chmod +x)

- **batch-update-sdk.sh**: Tum uygulamalarda Expo SDK guncelleme (paralel, max 3)
- **batch-aso-metadata.sh**: Tum uygulamalar icin ASO metadata uretimi (8 dil, seri)
- **batch-lint-fix.sh**: Toplu lint + type check duzeltme (paralel, max 4)

Kullanim: `~/.claude/scripts/batch-update-sdk.sh ~/apps 3`

## Hooks (2 adet, settings.local.json)

- **PostToolUse (Write|Edit)**: Prettier auto-format (jq ile dosya yolu cikarimi)
- **TeammateIdle**: Agent team'de bosta kalan teammate'e bildirim

## Agent Teams (Deneysel)

- `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1` (settings.local.json env)
- Worktree config: node_modules ve .expo symlink
- Gereksinim: Claude Code v2.1.32+, git repo, Opus model (lead)
- Kullanim: `/team-dev` veya `/team-review`

## Permissions (22 adet, settings.local.json)

Otomatik izin verilen komutlar: systeminfo, wmic, powershell system queries, nvidia-smi, eas, npx expo, npx eas, npm install, npm run, git (status/log/diff/add), gh, claude mcp, npx playwright, npx tsc, claude -p.

## claude-projects (ccode)

- Global kurulu: npm install -g claude-projects
- Config: ~/.claude-projects.yaml
- Ilk proje: aqualog (~/apps/aqualog-v3)
- Kullanim: `ccode aqualog "store listing guncelle"` veya `ccode aqualog "SDK guncelle" --background`

## Headless Mode Kullanimi

```bash
claude -p --output-format json --max-budget-usd 5 --allowedTools "Read,Write,Edit,Bash(npx:*)" "prompt"
```
Onemli flagler: -p (headless), --output-format (text/json/stream-json), --max-budget-usd, --allowedTools, --session-id, --resume, --continue

## Kritik Dosya Haritasi

```
~/.claude/
  settings.local.json    # env, worktree, permissions, hooks
  .claude.json           # MCP sunuculari (global mcpServers key)
  commands/              # 10 slash command
  skills/                # 3 custom skill (mobile-build, rn-feature, store-listing)
  rules/                 # 3 conditional rule (testing, monetization, batch-scripts)
  scripts/               # 3 batch script (chmod +x)
  plugins/marketplaces/  # 3 marketplace cache
~/.claude-projects.yaml  # claude-projects config
```
