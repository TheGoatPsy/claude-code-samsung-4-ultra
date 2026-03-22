---
name: DigitalOcean Droplet Bilgileri
description: DO droplet baglanti bilgileri, SSH config, nyc1 bolge, henuz SSH key yuklenmedi
type: reference
---

## Droplet Bilgileri
- **Public IPv4**: 147.182.164.38
- **Private IPv4**: 10.116.0.2 (VPC: default-nyc1, range: 10.116.0.0/20)
- **Gateway**: 147.182.160.1
- **Subnet**: 255.255.240.0
- **IPv6**: Kapalı (Droplet kapatılınca etkinlestirilebilir)
- **Bolge**: nyc1
- **DO email**: hezarfen.onour@gmail.com

## SSH Yapılandırması
- SSH config: ~/.ssh/config (Host: do-hezarfen)
- SSH key: ~/.ssh/id_ed25519 (ed25519, onuribram@outlook.com)
- Public key: ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIByqWyNLNgTgLq5kpKso2//FrOViIg8Ij81X/VT0nDdp
- **DURUMU**: SSH key henuz droplet'a yuklenemedi (Windows TTY sorunu, sshpass calismadi)

## Baglanti
```bash
ssh do-hezarfen  # key yuklendikten sonra
```

## Bekleyen Islem
DO web console'dan SSH key'i authorized_keys'e eklemek gerekiyor:
```bash
echo 'ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIByqWyNLNgTgLq5kpKso2//FrOViIg8Ij81X/VT0nDdp onuribram@outlook.com' >> ~/.ssh/authorized_keys
```
