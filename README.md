# WeddCode Gallery

Galeri foto web statis untuk foto-foto Google Drive, di-host di GitHub Pages.

## Cara kerja

1. Satu halaman (`index.html`) yang query **Google Drive API v3** saat dibuka.
2. Foto diambil **langsung dari folder Drive** (harus dibagikan publik: "Siapa saja dengan link").
3. Setiap folder punya link galeri sendiri:
   `https://<user>.github.io/<repo>/?id=<ID_FOLDER_DRIVE>&title=<Nama Acara>`
4. Foto baru otomatis muncul tanpa perlu deploy ulang.

## Deployment

```bash
gh auth login
gh repo create weddcode-gallery --public --source . --push
gh api repos/<USER>/weddcode-gallery/pages -f "source[branch]=main" -f "source[path]=/"
```

## API Key

Key ada di bagian `API_KEY` dalam `index.html`. Best practice:
batasi key di Google Cloud Console hanya untuk referrer
`https://<user>.github.io/*` supaya tidak dipakai orang lain.

## Menjadi publik

Folder Drive harus di-share: klik kanan folder -> Bagikan -> Umum ->
"Siapa saja dengan link" -> Penonton. Baru link galeri bisa menampilkan fotonya.
