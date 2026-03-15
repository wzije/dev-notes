# Git Workflow Guide

Dokumen ini menjelaskan standar **Git Workflow** yang digunakan pada project ini.
Tujuan workflow ini adalah untuk:

- menjaga struktur pengembangan tetap rapi
- mempermudah kolaborasi tim
- meminimalkan konflik kode
- memastikan kode yang masuk ke production sudah melalui proses review dan testing

Workflow ini menggunakan pendekatan **branch-based development** dengan Pull Request sebagai mekanisme integrasi kode.

---

# Branch Strategy

Project ini menggunakan beberapa jenis branch dengan fungsi yang berbeda.

## Branch Utama

```
main
develop
```

Penjelasan:

| Branch  | Deskripsi                                 |
| ------- | ----------------------------------------- |
| main    | Branch production yang berisi kode stabil |
| develop | Branch utama untuk proses development     |

Branch `main` hanya menerima perubahan dari **release atau hotfix**.

Branch `develop` digunakan sebagai tempat integrasi fitur sebelum masuk ke production.

---

# Branch Types

Selama development, beberapa jenis branch tambahan digunakan.

```
feature/*
fix/*
refactor/*
hotfix/*
```

| Branch      | Digunakan untuk                                        |
| ----------- | ------------------------------------------------------ |
| feature/\*  | Pengembangan fitur baru                                |
| fix/\*      | Perbaikan bug pada tahap development                   |
| refactor/\* | Perubahan struktur kode tanpa mengubah perilaku sistem |
| hotfix/\*   | Perbaikan bug yang terjadi di production               |

---

# Branch Naming Convention

Gunakan nama branch yang jelas dan konsisten.

Format:

```
type/deskripsi-singkat
```

Contoh:

```
feature/login-api
feature/product-search
fix/cart-calculation
refactor/user-service
hotfix/login-error
```

Gunakan:

- huruf kecil
- tanda `-` untuk pemisah kata
- deskripsi singkat dan jelas

---

# Development Workflow

Berikut langkah standar ketika mengembangkan fitur baru.

---

## 1 Update Branch Develop

Sebelum membuat branch baru, pastikan branch `develop` sudah terbaru.

```bash
git checkout develop
git pull origin develop
```

---

## 2 Buat Feature Branch

Buat branch baru dari `develop`.

```bash
git checkout -b feature/nama-fitur
```

Contoh:

```bash
git checkout -b feature/login-api
```

---

## 3 Implementasi Fitur

Tambahkan kode sesuai kebutuhan fitur.

Pastikan:

- kode mengikuti coding standard
- struktur project tetap konsisten
- tidak merusak fitur lain
- fitur dapat dijalankan dengan baik

---

## 4 Commit Perubahan

Gunakan **Commit Convention** yang telah ditentukan.

Contoh:

```
feat(auth): add login endpoint
```

Contoh commit lain:

```
feat(product): add product search feature
fix(cart): correct total price calculation
refactor(user): move logic to service layer
```

Lakukan commit secara **kecil dan terfokus** agar mudah direview.

---

## 5 Push Branch ke Remote

Push branch ke repository remote.

```bash
git push origin feature/login-api
```

---

# Pull Request Workflow

Setelah fitur selesai dikembangkan, langkah berikutnya adalah membuat **Pull Request**.

Pull Request digunakan untuk:

- menggabungkan kode
- melakukan code review
- memastikan kualitas kode

---

## 1 Membuat Pull Request

Buka repository di GitHub kemudian pilih **New Pull Request**.

Pengaturan branch:

```
base branch: develop
compare branch: feature/login-api
```

---

## 2 Menulis Deskripsi Pull Request

Deskripsi Pull Request harus jelas.

Contoh:

```
Menambahkan endpoint login menggunakan JWT authentication.

Fitur:
- login menggunakan email
- validasi password
- menghasilkan token JWT

Fixes #12
```

Jika memungkinkan sertakan:

- screenshot (untuk fitur UI)
- langkah pengujian
- referensi issue

---

# Code Review Process

Sebelum merge, Pull Request akan melalui proses **code review**.

Reviewer akan memeriksa:

- kualitas kode
- konsistensi coding style
- potensi bug
- efisiensi kode
- keamanan

Jika ada perbaikan, reviewer akan memberikan komentar pada Pull Request.

---

# Revisi Pull Request

Jika reviewer meminta perubahan:

1. Perbaiki kode
2. Commit perubahan
3. Push kembali ke branch yang sama

Contoh:

```bash
git add .
git commit -m "fix(auth): correct login validation"
git push
```

Pull Request akan **update otomatis**.

---

# Merge Pull Request

Setelah Pull Request disetujui, maintainer akan melakukan merge ke branch `develop`.

Metode merge yang dapat digunakan:

| Merge Type   | Deskripsi                             |
| ------------ | ------------------------------------- |
| Merge Commit | mempertahankan seluruh riwayat commit |
| Squash Merge | menggabungkan commit menjadi satu     |
| Rebase Merge | menjaga riwayat commit tetap linear   |

Biasanya project menggunakan **Squash Merge** agar riwayat commit lebih bersih.

---

# Release Workflow

Release dilakukan ketika fitur pada branch `develop` sudah stabil.

Diagram alur release:

```
feature branch
      ↓
develop (testing)
      ↓
main (production)
```

Langkah-langkah:

1. Semua feature branch di-merge ke `develop`
2. Dilakukan testing pada branch `develop`
3. Jika stabil, merge `develop` ke `main`

Contoh:

```bash
git checkout main
git merge develop
git push origin main
```

---

# Hotfix Workflow

Jika ditemukan bug pada production, gunakan **hotfix branch**.

---

## 1 Buat Branch Hotfix

Branch dibuat dari `main`.

```bash
git checkout main
git pull origin main
git checkout -b hotfix/nama-bug
```

Contoh:

```bash
git checkout -b hotfix/login-error
```

---

## 2 Perbaiki Bug

Lakukan perbaikan pada bug yang ditemukan.

---

## 3 Commit dan Push

```
fix(auth): resolve login error in production
```

Push branch:

```bash
git push origin hotfix/login-error
```

---

## 4 Merge Hotfix

Hotfix harus di-merge ke dua branch:

- `main`
- `develop`

Agar perbaikan ikut masuk ke development.

---

# Best Practices

Berikut beberapa praktik terbaik dalam menggunakan Git.

### Gunakan Commit Kecil

Commit perubahan secara bertahap agar mudah dilacak.

### Gunakan Pesan Commit yang Jelas

Contoh baik:

```
feat(product): add product search feature
```

Contoh buruk:

```
update
fix bug
change code
```

### Hindari Commit Langsung ke Main

Semua perubahan harus melalui:

```
feature branch → Pull Request → develop
```

### Update Branch Secara Berkala

Agar menghindari konflik:

```bash
git pull origin develop
```

---

# Ringkasan Workflow

```
feature/*  → develop → main
fix/*      → develop
refactor/* → develop
hotfix/*   → main + develop
```

---

# Visual Workflow

```
             feature/login
                   │
                   │
feature/product ---│
                   │
                develop
                   │
                   │
                 main
```

---

# Kesimpulan

Workflow ini dirancang untuk:

- menjaga kualitas kode
- mempermudah kolaborasi tim
- memastikan proses development lebih terstruktur
- meminimalkan bug di production

Dengan mengikuti workflow ini, proses pengembangan software dapat berjalan lebih stabil dan profesional.
