# Branch Naming Convention

Dokumen ini menjelaskan standar penamaan branch pada repository ini.
Tujuannya adalah untuk menjaga konsistensi, memudahkan kolaborasi tim, dan membuat riwayat pengembangan lebih mudah dipahami.

---

# Format Branch

Format penamaan branch yang digunakan adalah:

```
type/deskripsi-singkat
```

Contoh:

```
feature/login-api
fix/cart-calculation
refactor/user-service
hotfix/payment-error
```

---

# Branch Types

Beberapa tipe branch yang digunakan pada project ini:

| Type     | Digunakan untuk                              | Contoh                  |
| -------- | -------------------------------------------- | ----------------------- |
| feature  | Pengembangan fitur baru                      | feature/user-login      |
| fix      | Perbaikan bug pada tahap development         | fix/cart-total          |
| refactor | Perbaikan struktur kode tanpa mengubah fitur | refactor/auth-service   |
| hotfix   | Perbaikan bug di production                  | hotfix/login-error      |
| docs     | Perubahan dokumentasi                        | docs/update-readme      |
| chore    | Maintenance atau perubahan kecil             | chore/update-dependency |

---

# Rules

Saat membuat branch, ikuti aturan berikut:

- gunakan **huruf kecil**
- gunakan **tanda strip (-)** untuk memisahkan kata
- gunakan **deskripsi yang jelas**
- hindari nama branch yang terlalu panjang

Contoh baik:

```
feature/product-search
fix/login-validation
refactor/order-service
```

Contoh buruk:

```
feature/newfeature
fixbug
update
branch1
```

---

# Branch Naming Examples

Berikut beberapa contoh penamaan branch yang umum digunakan.

### Feature Development

```
feature/user-registration
feature/payment-integration
feature/product-search
```

### Bug Fix

```
fix/cart-total-calculation
fix/login-validation-error
```

### Refactor

```
refactor/auth-service
refactor/database-query
```

### Hotfix

```
hotfix/login-error
hotfix/payment-timeout
```

---

# Best Practices

Beberapa praktik terbaik saat membuat branch:

- buat branch **untuk satu tugas spesifik**
- gunakan nama branch yang **mudah dipahami**
- hapus branch setelah merge

Contoh workflow:

```
develop
   │
   └── feature/login-api
           │
           └── merge → develop
```
