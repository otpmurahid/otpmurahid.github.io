# 🔐 OTPMurah.id — Developer Hub

> **SMS OTP Termurah Indonesia** · Platform sewa nomor virtual untuk verifikasi WhatsApp, Telegram, Shopee, Gojek, Tinder & 478+ aplikasi lainnya. Mulai dari **Rp 150**.

[![Website](https://img.shields.io/badge/🌐_Website-otpmurah.id-2a9d5b?style=for-the-badge)](https://otpmurah.id)
[![API Docs](https://img.shields.io/badge/📖_API_Docs-Read-1d8348?style=for-the-badge)](https://otpmurah.id/api-docs)
[![Quick Start](https://img.shields.io/badge/⚡_Quick_Start-5_menit-2563eb?style=for-the-badge)](https://otpmurah.id/api-quickstart)
[![Blog](https://img.shields.io/badge/📰_Blog-Tutorial-f59e0b?style=for-the-badge)](https://otpmurah.id/blog/)

---

## 👋 Tentang OTPMurah.id

[**OTPMurah.id**](https://otpmurah.id) adalah penyedia layanan SMS OTP & nomor virtual #1 Indonesia dengan harga termurah dan proses tercepat. Cocok untuk:

- 🛒 **Verifikasi akun e-commerce** (Shopee, Tokopedia, Lazada)
- 💬 **Aktivasi WhatsApp, Telegram, Signal** tanpa kartu SIM fisik
- 🚗 **Pendaftaran ojek online** (Gojek, Grab, Maxim)
- ❤️ **Sosial media & dating** (Instagram, Facebook, Tinder, Bumble)
- 🏢 **Bisnis & developer** (auto-registration, testing, CRM)

🔗 **Kunjungi:** https://otpmurah.id

---

## 🚀 Quick Links

| Resource | Link |
|----------|------|
| 🌐 Website Utama | https://otpmurah.id |
| 📖 Dokumentasi API Lengkap | https://otpmurah.id/api-docs |
| ⚡ API Quick Start Guide (5 menit) | https://otpmurah.id/api-quickstart |
| 📰 Blog & Tutorial Indonesia | https://otpmurah.id/blog/ |
| 💰 Daftar Harga OTP Termurah | https://otpmurah.id/#harga |
| 🔐 Daftar Akun Gratis | https://otpmurah.id/register |
| 🤖 Telegram Bot Resmi | https://t.me/otpmurahid_bot |
| 👥 Group Komunitas | https://t.me/OTPMurahOfficial |

---

## ✨ Kenapa Pilih OTPMurah.id?

- ✅ **Harga Termurah** — mulai dari Rp 150 per OTP
- ✅ **76+ Negara Tersedia** — Indonesia, Malaysia, Singapore, USA, Russia, India, dll
- ✅ **478+ Aplikasi Didukung** — semua app populer & niche
- ✅ **OTP Masuk <30 Detik** — server real-time, latency rendah
- ✅ **Refund Otomatis** — kalo OTP gak masuk, saldo balik 100%
- ✅ **2 Server Pilihan** — Server Plus (paling hemat) & Server Express (respons cepat)
- ✅ **REST API Lengkap** — kompatibel SMS-Activate protocol
- ✅ **Garansi 100%** — uang kembali kalo gagal aktivasi
- ✅ **Pembayaran Lokal** — QRIS, Transfer Bank, E-Wallet (DANA, OVO, Gopay, ShopeePay)

📚 Pelajari lebih lanjut: [Cara Beli OTP Murah](https://otpmurah.id/blog/cara-beli-otp-murah) · [Verifikasi WhatsApp Tanpa SIM](https://otpmurah.id/blog/verifikasi-whatsapp-tanpa-sim) · [Perbandingan Harga OTP 2026](https://otpmurah.id/blog/perbandingan-harga-otp-2026)

---

## 💻 Code Examples

> **Tutorial integrasi step-by-step:** [otpmurah.id/api-quickstart](https://otpmurah.id/api-quickstart)
>
> **Dokumentasi endpoint lengkap:** [otpmurah.id/api-docs](https://otpmurah.id/api-docs)

### 🔑 Authentication

Semua request butuh API key (dapatkan gratis di [otpmurah.id/dashboard](https://otpmurah.id/register)):

```
X-API-Key: YOUR_API_KEY
```

### cURL — Cek Saldo

```bash
curl "https://otpmurah.id/api/?action=getBalance" \
  -H "X-API-Key: YOUR_API_KEY"
```

### cURL — Order Nomor WhatsApp Indonesia

```bash
curl -X POST "https://otpmurah.id/api/?action=getNumber" \
  -H "X-API-Key: YOUR_API_KEY" \
  -d "service=wa&country=6&server=s2"
```

### PHP

```php
<?php
$apiKey = 'YOUR_API_KEY';
$baseUrl = 'https://otpmurah.id/api/';

// Cek saldo
$ch = curl_init($baseUrl . '?action=getBalance');
curl_setopt_array($ch, [
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_HTTPHEADER => ['X-API-Key: ' . $apiKey],
]);
$response = json_decode(curl_exec($ch), true);
echo "Saldo: Rp " . $response['data']['balance'];

// Order nomor WhatsApp
$ch = curl_init($baseUrl . '?action=getNumber');
curl_setopt_array($ch, [
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_POST => true,
    CURLOPT_POSTFIELDS => http_build_query([
        'service' => 'wa',
        'country' => 6,
        'server' => 's2',
    ]),
    CURLOPT_HTTPHEADER => ['X-API-Key: ' . $apiKey],
]);
$order = json_decode(curl_exec($ch), true);
echo "Phone: " . $order['data']['phone'];
echo "Activation ID: " . $order['data']['activation_id'];
```

### Node.js

```javascript
const apiKey = 'YOUR_API_KEY';
const baseUrl = 'https://otpmurah.id/api/';

// Cek saldo
const balanceRes = await fetch(`${baseUrl}?action=getBalance`, {
    headers: { 'X-API-Key': apiKey }
});
const balance = await balanceRes.json();
console.log(`Saldo: Rp ${balance.data.balance}`);

// Order WhatsApp
const orderRes = await fetch(`${baseUrl}?action=getNumber`, {
    method: 'POST',
    headers: {
        'X-API-Key': apiKey,
        'Content-Type': 'application/x-www-form-urlencoded'
    },
    body: 'service=wa&country=6&server=s2'
});
const order = await orderRes.json();
console.log(`Phone: ${order.data.phone}`);
```

### Python

```python
import requests

API_KEY = 'YOUR_API_KEY'
BASE_URL = 'https://otpmurah.id/api/'
HEADERS = {'X-API-Key': API_KEY}

# Cek saldo
r = requests.get(BASE_URL, params={'action': 'getBalance'}, headers=HEADERS).json()
print(f"Saldo: Rp {r['data']['balance']}")

# Order WhatsApp
r = requests.post(BASE_URL,
    params={'action': 'getNumber'},
    data={'service': 'wa', 'country': 6, 'server': 's2'},
    headers=HEADERS
).json()
print(f"Phone: {r['data']['phone']}")
```

🎯 **Tutorial lengkap dengan polling OTP & error handling:** [otpmurah.id/api-quickstart](https://otpmurah.id/api-quickstart)

---

## 🌍 Server Selection

OTPMurah.id punya 2 server dengan harga & stok berbeda:

| Server | Code | Karakteristik |
|--------|------|---------------|
| **Server Plus** | `s2` | Pilihan utama · paling hemat (default) |
| **Server Express** | `s1` | Alternatif · respons cepat |

Detail lengkap: [otpmurah.id/api-docs#servers](https://otpmurah.id/api-docs)

---

## 🛠️ Service Codes Populer

| Service | Code | Service | Code |
|---------|------|---------|------|
| WhatsApp | `wa` | Instagram | `ig` |
| Telegram | `tg` | Facebook | `fb` |
| Shopee | `oi` | Tinder | `oo` |
| Gojek | `ka` | Google | `go` |
| Tokopedia | `tk` | TikTok | `lf` |

📋 **Daftar lengkap 478+ service codes:** [otpmurah.id/api-docs#services](https://otpmurah.id/api-docs)

---

## 🌐 76+ Negara Tersedia

Indonesia (6) · Malaysia (7) · Singapore (196) · United States (187) · Russia (0) · India (22) · Philippines (4) · Vietnam (10) · Thailand (52) · United Kingdom (16) · Germany (43) · France (78) · Brazil (73) · Mexico (54) · Canada (36) · Australia (175) · dan 60+ negara lainnya.

🗺️ **Cek harga & stok per negara:** [otpmurah.id/dashboard/order](https://otpmurah.id)

---

## 📚 Resources & Tutorials

- 📖 [API Documentation](https://otpmurah.id/api-docs) — Endpoint reference, parameter, response format
- ⚡ [API Quick Start Guide](https://otpmurah.id/api-quickstart) — Tutorial integrasi 5 menit
- 📝 [Blog OTPMurah](https://otpmurah.id/blog/) — Tips, tutorial, & news
- 🎓 [Cara Beli OTP Murah](https://otpmurah.id/blog/cara-beli-otp-murah) — Panduan pemula
- 📱 [Verifikasi WhatsApp Tanpa SIM](https://otpmurah.id/blog/verifikasi-whatsapp-tanpa-sim) — Step-by-step
- 💸 [Perbandingan Harga OTP 2026](https://otpmurah.id/blog/perbandingan-harga-otp-2026) — Review harga

---

## 🤖 Telegram Bot

Mau order langsung dari Telegram tanpa coding? Pake bot resmi kami:

👉 **[@otpmurahid_bot](https://t.me/otpmurahid_bot)**

Bot fitur lengkap: cek saldo, order OTP, top up QRIS, cek status, riwayat — semua dalam 1 chat.

---

## 💬 Support & Komunitas

- 🌐 **Website:** https://otpmurah.id
- 📖 **API Docs:** https://otpmurah.id/api-docs
- ⚡ **Quick Start:** https://otpmurah.id/api-quickstart
- 📰 **Blog:** https://otpmurah.id/blog/
- 🤖 **Bot Telegram:** https://t.me/otpmurahid_bot
- 👥 **Group Diskusi:** https://t.me/OTPMurahOfficial
- 💬 **Admin CS:** https://t.me/otpmurahid

---

## ⭐ Star & Follow

Kalo repo ini bermanfaat, jangan lupa **⭐ star** repo ini & **follow** [@otpmurahid](https://github.com/otpmurahid) untuk update terbaru.

🔗 **Coba gratis sekarang:** https://otpmurah.id/register

---

## 📄 License

MIT License — feel free to use, modify, and distribute.

Copyright © 2026 [OTPMurah.id](https://otpmurah.id) — DAPATKAN OTP DENGAN CEPAT DAN TERMURAH
