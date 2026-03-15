# Commit Convention Guide

Panduan ini menjelaskan standar penulisan **commit message** agar konsisten, mudah dibaca, dan memudahkan kolaborasi dalam pengembangan perangkat lunak.

Format ini mengikuti praktik umum yang banyak digunakan dalam proyek profesional.

---

## 1. Struktur Commit Message

Format dasar commit message:

```bash

<type>(<scope>): <description>

[optional body]

[optional footer]

```

Contoh commit lengkap:

```bash
feat(auth): add JWT login

Implement JWT authentication for API login
and protect routes using auth middleware.

Closes #21
```

---

## 2. Komponen Commit Message

| Komponen    | Wajib    | Deskripsi                            |
| ----------- | -------- | ------------------------------------ |
| type        | Ya       | Jenis perubahan dalam commit         |
| scope       | Opsional | Bagian sistem yang terdampak         |
| description | Ya       | Ringkasan singkat perubahan          |
| body        | Opsional | Penjelasan lebih detail              |
| footer      | Opsional | Referensi issue atau breaking change |

---

## 3. Aturan Penulisan Commit

Gunakan aturan berikut:

- Gunakan **huruf kecil (lowercase)**
- Gunakan **present tense**
- Deskripsi maksimal **50–72 karakter**
- Gunakan kalimat **jelas dan spesifik**
- Hindari commit message yang terlalu umum

Contoh yang benar:

```bash
feat(user): add profile update feature
```

Contoh yang tidak disarankan:

```bash
update
fix bug
changes
```

---

## 4. Type Commit

`type` menunjukkan kategori perubahan yang dilakukan pada kode.

Format dasar:

```bash
<type>: <description>
```

atau

```bash
<type>(scope): <description>
```

---

## 5. Scope

`scope` menunjukkan bagian sistem yang berubah.

Contoh scope umum:

```bash
auth
user
product
cart
payment
api
database
ui
config
```

Contoh penggunaan:

```bash
feat(auth): add google login
fix(cart): incorrect total calculation
```

---

## 6. Description

`description` adalah ringkasan singkat dari perubahan.

Aturan:

- gunakan huruf kecil
- gunakan present tense
- jelas dan langsung ke perubahan

Contoh:

```bash
feat(product): add product search feature
fix(auth): handle expired token
```

---

## 7. Body (Opsional)

Digunakan untuk menjelaskan detail perubahan.

Biasanya menjelaskan:

- apa yang berubah
- alasan perubahan
- dampak perubahan

Contoh:

```bash
feat(payment): add midtrans payment gateway

Integrate Midtrans Snap API to process payment transactions and store transaction status in the orders table.
```

---

## 8. Footer (Opsional)

Digunakan untuk referensi issue atau perubahan besar.

Contoh:

```bash
Closes #45
```

atau

```bash
BREAKING CHANGE: authentication now requires API key
```

Contoh lengkap:

```bash
feat(auth): implement jwt authentication
Add JWT token generation for login endpoint.
Closes #45
```

---

## 9. Jenis Commit (Types) dan Contohnya

## feat

Menambahkan **fitur baru**.

```bash
feat: add product search
feat(auth): implement login with JWT
feat(post): create post CRUD API
```

---

### fix

Memperbaiki **bug atau kesalahan program**.

```bash
fix: resolve login error
fix(cart): incorrect total price calculation
fix(upload): prevent image upload failure
```

---

### docs

Perubahan **dokumentasi saja**.

```bash
docs: update installation guide
docs(api): add endpoint documentation
docs(readme): improve project description
```

---

### style

Perubahan **format kode tanpa mengubah logika program**.

Contoh perubahan:

- indentation
- spacing
- formatting

```bash
style: fix code formatting
style(controller): improve code indentation
style: remove unused whitespace
```

---

### refactor

Perubahan **struktur kode tanpa menambah fitur atau memperbaiki bug**.

```bash
refactor: simplify validation logic
refactor(user): move business logic to service layer
refactor(api): separate controller and service
```

---

### perf

Perubahan untuk **meningkatkan performa aplikasi**.

```bash
perf: optimize database query
perf(post): reduce query count for post listing
perf(api): improve response time for product endpoint
```

---

### test

Menambahkan atau memperbaiki **unit test / integration test**.

```bash
test: add login API test
test(auth): add authentication unit tests
test(product): add product service tests
```

---

### chore

Perubahan kecil yang **tidak mempengaruhi logika aplikasi**, biasanya terkait maintenance.

```bash
chore: update composer dependencies
chore: update laravel to version 11
chore(config): update environment configuration
```

---

### build

Perubahan terkait **build system atau dependency build**.

```bash
build: update docker configuration
build: add vite build configuration
build(ci): update build pipeline
```

---

### ci

Perubahan pada **pipeline CI/CD**.

```bash
ci: add github actions workflow
ci: update deployment pipeline
ci: add automatic testing workflow
```

### Summary

| Type     | Deskripsi                                | Kapan Digunakan                  | Contoh Commit                                 |
| -------- | ---------------------------------------- | -------------------------------- | --------------------------------------------- |
| feat     | Menambahkan fitur baru                   | Saat menambah functionality baru | `feat(auth): implement login with JWT`        |
| fix      | Memperbaiki bug                          | Saat memperbaiki error atau bug  | `fix(cart): incorrect total calculation`      |
| docs     | Perubahan dokumentasi                    | Update README, docs API, panduan | `docs(readme): update installation guide`     |
| style    | Perubahan format kode tanpa ubah logika  | Formatting, spacing, linting     | `style(controller): fix code indentation`     |
| refactor | Perubahan struktur kode tanpa ubah fitur | Improve readability / structure  | `refactor(user): move logic to service layer` |
| perf     | Peningkatan performa                     | Optimasi query, caching, speed   | `perf(api): optimize product query`           |
| test     | Menambah atau memperbaiki test           | Unit test atau integration test  | `test(auth): add login unit test`             |
| chore    | Maintenance atau perubahan kecil         | Update dependency, config        | `chore: update composer dependencies`         |
| build    | Perubahan sistem build                   | Docker, Vite, bundler            | `build: update docker configuration`          |
| ci       | Perubahan pipeline CI/CD                 | Github Actions, Gitlab CI        | `ci: add github actions workflow`             |

---

## 10. Contoh Commit pada Project Laravel

Contoh commit realistis pada proyek Laravel:

```bash
feat(auth): implement login API
feat(post): create post CRUD
fix(user): resolve avatar upload error
refactor(post): move business logic to service layer
perf(api): optimize post listing query
test(auth): add login feature test
docs: update API documentation
chore: update composer dependencies
```

---

## 11. Commit yang Harus Dihindari

Hindari commit message yang terlalu umum seperti:

```bash
update
fix bug
changes
wip
```

Gunakan commit yang lebih jelas:

```bash
fix(auth): handle expired token
```

---

## 12. Contoh Workflow Commit

Contoh workflow saat membuat fitur login:

```bash
feat(auth): create login endpoint
feat(auth): add JWT authentication
fix(auth): handle invalid credentials
test(auth): add login API test
```

Workflow ini membuat histori commit menjadi:

- jelas
- mudah dilacak
- mudah direview oleh tim
