# ☁️ NineCloud

**NineCloud** adalah repositori publik yang digunakan sebagai tempat penyimpanan file yang diunggah melalui aplikasi web:  
🔗 [ninecloudvrs.vercel.app](https://ninecloudvrs.vercel.app)

> ⚠️ Semua file yang diunggah bersifat **publik**, jadi hindari mengunggah data sensitif atau pribadi.

---

## 🚀 Tentang
NineCloud berfungsi sebagai **media penyimpanan sederhana berbasis GitHub API**, yang memungkinkan aplikasi untuk mengunggah file langsung ke repositori ini menggunakan endpoint:

```
PUT /repos/{owner}/{repo}/contents/{path}
```

Autentikasi dilakukan menggunakan **Fine-grained Personal Access Token (PAT)** dengan izin berikut:
- `Contents: Read and write`
- `Metadata: Read-only`

---

## 🧰 Teknologi
- [GitHub REST API](https://docs.github.com/en/rest)
- [Vercel](https://vercel.com/)
- [Node.js](https://nodejs.org/) atau `fetch()` browser
- Token autentikasi GitHub

---

## 📁 Struktur Folder (contoh)
```
/uploads
  ├── images/
  ├── json/
  └── misc/
```

---

## 🧑‍💻 Contoh Upload File (Node.js)
```js
import fs from "fs";
import fetch from "node-fetch";

const owner = "nine";
const repo = "ninecloud";
const path = "uploads/hello.txt";
const token = process.env.GITHUB_TOKEN;
const content = fs.readFileSync("./hello.txt", "base64");

await fetch(`https://api.github.com/repos/${owner}/${repo}/contents/${path}`, {
  method: "PUT",
  headers: {
    "Authorization": `token ${token}`,
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    message: "Upload file lewat API",
    content: content,
  }),
});
```

---

## 📜 Lisensi

Proyek ini dilisensikan di bawah **[MIT License](LICENSE)**  
Silakan digunakan, dimodifikasi, dan dibagikan dengan bebas, selama mencantumkan kredit yang sesuai.

---

### ❤️ Dibuat dengan semangat eksplorasi oleh [NineCloud Team](https://ninecloudvrs.vercel.app)
