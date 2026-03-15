# Development Guidelines

Dokumen ini berisi pedoman pengembangan kode pada project ini.
Tujuan dari pedoman ini adalah untuk:

- menjaga konsistensi kode
- meningkatkan kualitas kode
- memudahkan kolaborasi antar developer
- mempermudah maintenance jangka panjang

Semua kontributor diharapkan mengikuti pedoman ini saat menulis kode.

---

# Coding Principles

Beberapa prinsip dasar yang harus diikuti:

- **Readability** → kode harus mudah dibaca
- **Consistency** → gunakan pola yang sama di seluruh project
- **Simplicity** → hindari kompleksitas yang tidak perlu
- **Maintainability** → kode harus mudah diperbaiki dan dikembangkan

---

# Code Style

Gunakan standar berikut saat menulis kode.

### Gunakan Nama Variabel yang Jelas

Contoh baik:

```id="ntr4pr"
totalPrice
userEmail
orderItems
```

Contoh buruk:

```id="3h10rf"
tp
data1
x
```

---

### Gunakan Fungsi yang Kecil dan Fokus

Setiap fungsi harus memiliki satu tanggung jawab.

Contoh baik:

```id="7w1e7p"
function calculateTotalPrice(items) {
    // logic
}
```

Contoh buruk:

```id="af40t4"
function processOrderAndSendEmailAndUpdateStock() {
}
```

---

# Project Structure

Struktur folder harus konsisten agar mudah dipahami.

Contoh struktur umum:

```id="mwxu40"
project
│
├── app
│   ├── Controllers
│   ├── Services
│   ├── Models
│   └── Repositories
│
├── database
│   ├── migrations
│   └── seeders
│
├── routes
│
├── resources
│   ├── views
│   └── assets
│
└── tests
```

Penjelasan:

| Folder       | Fungsi                |
| ------------ | --------------------- |
| Controllers  | menangani request     |
| Services     | berisi business logic |
| Models       | representasi data     |
| Repositories | akses database        |

---

# Controller Guidelines

Controller harus **ringan dan sederhana**.

Controller hanya bertugas untuk:

- menerima request
- memanggil service
- mengembalikan response

Contoh:

```id="3fntd0"
public function login(Request $request)
{
    return $this->authService->login($request);
}
```

Hindari menulis business logic langsung di controller.

---

# Service Layer

Gunakan **Service Layer** untuk menyimpan business logic.

Contoh:

```id="m1x64r"
class AuthService {

    public function login($request)
    {
        // login logic
    }

}
```

Keuntungan:

- kode lebih terstruktur
- mudah diuji
- mudah digunakan kembali

---

# Error Handling

Gunakan penanganan error yang jelas.

Contoh:

```id="9u0q5n"
try {
    // process
} catch (Exception $e) {
    return response()->json([
        'error' => $e->getMessage()
    ]);
}
```

Hindari menampilkan error mentah ke user.

---

# Database Guidelines

Gunakan standar berikut saat bekerja dengan database.

### Gunakan Migration

Semua perubahan database harus menggunakan migration.

Contoh:

```bash id="ktzeov"
php artisan make:migration create_products_table
```

---

### Gunakan Naming Convention

Tabel:

```
users
products
orders
```

Kolom:

```
user_id
created_at
updated_at
```

---

# Commit Guidelines

Gunakan **commit convention** yang telah ditentukan.

Contoh:

```
feat(auth): add login endpoint
fix(cart): correct price calculation
refactor(user): move logic to service
```

Hindari commit seperti:

```
update
fix
change code
```

---

# Testing

Jika memungkinkan, setiap fitur harus memiliki test.

Jenis testing:

| Test             | Tujuan                           |
| ---------------- | -------------------------------- |
| Unit Test        | menguji fungsi tertentu          |
| Integration Test | menguji integrasi antar komponen |
| Feature Test     | menguji fitur secara keseluruhan |

---

# Code Review

Semua kode harus melalui proses **code review** sebelum digabungkan.

Reviewer biasanya memeriksa:

- kualitas kode
- potensi bug
- performa
- keamanan

---

# Best Practices

Gunakan praktik terbaik berikut:

### Jangan Commit File Sensitif

Contoh:

```
.env
config secrets
API keys
```

Gunakan `.gitignore`.

---

### Gunakan Branch untuk Setiap Fitur

```
feature/login-api
feature/product-search
```

---

### Pull Request Kecil Lebih Baik

Pull Request kecil lebih mudah direview dibandingkan perubahan besar.

---

# Documentation

Setiap fitur penting harus memiliki dokumentasi.

Dokumentasi dapat berupa:

- README
- API documentation
- komentar kode

---

# Kesimpulan

Dengan mengikuti pedoman ini, pengembangan project akan:

- lebih konsisten
- lebih mudah dipahami
- lebih mudah dikembangkan
- lebih mudah dipelihara
