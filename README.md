# TT Downloader

Download video TikTok tanpa watermark + rip MP3 — pure HTML/CSS/JS, zero backend, zero dependency.

**Live demo → [tiktok-downloader-delta-three.vercel.app](https://tiktok-downloader-delta-three.vercel.app)**

[![Stars](https://img.shields.io/github/stars/RynnStecu/tt-downloader?style=flat-square&color=8b0000&labelColor=0d0d12&logo=github)](https://github.com/RynnStecu/tt-downloader/stargazers)
[![Forks](https://img.shields.io/github/forks/RynnStecu/tt-downloader?style=flat-square&color=6b0000&labelColor=0d0d12&logo=github)](https://github.com/RynnStecu/tt-downloader/forks)
[![License](https://img.shields.io/badge/license-MIT-8b0000?style=flat-square&labelColor=0d0d12)](LICENSE)

---

## Fitur

- Download video TikTok tanpa watermark
- Rip audio / MP3 dari video TikTok
- Multi-API fallback otomatis (tikwm → tikmate)
- Paste dari clipboard sekali klik
- Full WebKit CSS prefix — Safari & iOS ready
- Pure static file — bisa deploy di mana aja
- Tersedia versi obfuscated (`index.min.html`)

---

## File

```
tt-downloader/
├── index.html        # versi bersih
├── index.min.html    # versi obfuscated
└── README.md
```

---

## Deploy

### GitHub Pages

```bash
git clone https://github.com/RynnStecu/tt-downloader.git
cd tt-downloader
git add .
git commit -m "deploy"
git push origin main
```

Lalu: **Repo → Settings → Pages → Source: main / (root) → Save**

Live di `https://namakamu.github.io/tt-downloader/`

---

### Vercel *(dipakai di repo ini)*

```bash
npm install -g vercel
cd tt-downloader
vercel --prod
```

Ikuti prompt → pilih akun → nama project → directory `./` → deploy.

Custom domain bisa di-set di: **Vercel Dashboard → Project → Settings → Domains**

---

### Netlify

Cara paling cepat — drag & drop folder project ke [app.netlify.com](https://app.netlify.com).

Atau lewat CLI:

```bash
npm install -g netlify-cli
netlify deploy --prod --dir .
```

---

### Cloudflare Pages

```bash
npm install -g wrangler
wrangler login
wrangler pages deploy . --project-name tt-downloader
```

Atau via dashboard: **Workers & Pages → Create → Pages → Connect Git → pilih repo → Deploy**

---

### VPS + Nginx + Cloudflare Tunnel

```bash
# Copy ke webroot
sudo cp index.html /var/www/html/index.html
sudo systemctl restart nginx

# Install cloudflared
curl -L https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64 \
  -o /usr/local/bin/cloudflared
chmod +x /usr/local/bin/cloudflared

# Setup & jalankan tunnel
cloudflared tunnel login
cloudflared tunnel create tt-downloader
cloudflared tunnel --url http://localhost:80 run tt-downloader
```

---

### Termux (Android)

```bash
pkg update && pkg install python -y
cd /sdcard/tt-downloader
python -m http.server 8080
# buka http://localhost:8080 di browser
```

---

## Kustomisasi

```html
<!-- Ganti avatar -->
<img src="LINK_FOTO" alt="Avatar" class="avatar">

<!-- Ganti handle -->
<div class="hero-handle">@username</div>

<!-- Ganti link channel WA -->
<a href="LINK_CHANNEL_WA" ...>
```

Ganti warna accent di CSS:

```css
:root {
  --accent: #8b0000; /* dark red — ganti sesuai selera */
}
```

---

## API yang Dipakai

| API | Endpoint | Keterangan |
|-----|----------|------------|
| tikwm | `tikwm.com/api` | Primary, no watermark |
| tikmate | `api.tikmate.app` | Fallback |

Keduanya gratis, no API key required.

---

## Komunitas

[![Channel WA](https://img.shields.io/badge/Channel%20WhatsApp-@RynnStecu-25d366?style=flat-square&logo=whatsapp&logoColor=white&labelColor=0d0d12)](https://whatsapp.com/channel/0029Vb7gcbuLdQelWzrTzD3D)

---

## License

MIT — bebas pakai, modif, dan sebarluaskan. Jangan hapus credit `@RynnStecu`.

---

> Kalau repo ini berguna, kasih ⭐ ya — gratis tapi berarti banyak!
