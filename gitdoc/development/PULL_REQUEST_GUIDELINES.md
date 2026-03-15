# Pull Request Guidelines

Dokumen ini menjelaskan panduan membuat Pull Request agar proses review dan integrasi kode berjalan lebih efektif.

Pull Request (PR) digunakan untuk:

- menggabungkan perubahan kode
- melakukan code review
- memastikan kualitas kode sebelum masuk ke branch utama

---

# Sebelum Membuat Pull Request

Pastikan hal berikut sudah dilakukan:

- kode sudah berjalan dengan baik
- tidak ada error
- commit message mengikuti commit convention
- branch sudah terbaru dari `develop`

Update branch jika diperlukan:

```bash
git checkout develop
git pull origin develop
```

---

# Cara Membuat Pull Request

### 1 Push Branch

Push branch ke repository remote.

```bash
git push origin feature/nama-fitur
```

---

### 2 Buka Pull Request

Masuk ke repository GitHub dan klik **New Pull Request**.

Pengaturan branch:

```
base branch: develop
compare branch: feature/nama-fitur
```

---

# Menulis Deskripsi Pull Request

Deskripsi Pull Request harus jelas dan informatif.

Contoh:

```
Menambahkan fitur login menggunakan JWT authentication.

Fitur:
- login menggunakan email
- validasi password
- generate token JWT

Fixes #15
```

Jika perubahan berkaitan dengan UI, tambahkan screenshot.

---

# Pull Request Checklist

Sebelum mengirim Pull Request, pastikan:

- [ ] kode sudah diuji
- [ ] tidak ada error
- [ ] commit mengikuti commit convention
- [ ] branch terbaru dari develop
- [ ] dokumentasi diperbarui jika diperlukan

---

# Code Review Process

Setelah Pull Request dibuat, maintainer atau anggota tim lain akan melakukan review.

Hal yang biasanya diperiksa:

- kualitas kode
- konsistensi coding style
- potensi bug
- performa
- keamanan

Reviewer dapat memberikan komentar atau meminta revisi.

---

# Revisi Pull Request

Jika ada revisi dari reviewer:

1. Perbaiki kode
2. Commit perubahan
3. Push kembali ke branch

Contoh:

```bash
git add .
git commit -m "fix(auth): correct login validation"
git push
```

Pull Request akan **terupdate otomatis**.

---

# Merge Pull Request

Setelah disetujui, Pull Request akan di-merge ke branch `develop`.

Metode merge yang digunakan biasanya:

- **Squash Merge** → commit digabung menjadi satu
- **Merge Commit** → semua commit tetap terlihat

---

# Best Practices

Gunakan praktik berikut saat membuat Pull Request:

### Pull Request Kecil

Pull Request kecil lebih mudah direview dibandingkan perubahan besar.

### Deskripsi yang Jelas

Jelaskan perubahan yang dilakukan dan alasan perubahan.

### Satu Fitur per Pull Request

Jangan mencampur beberapa fitur dalam satu Pull Request.

---

# Contoh Alur Pull Request

```
feature/login-api
        │
        │
   Pull Request
        │
        ↓
     develop
```

Setelah fitur stabil di `develop`, kode akan masuk ke `main` saat proses release.
