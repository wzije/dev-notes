# Database Naming Convention

## Pentingnya Penamaan (Naming Convention)
1. Nama akan digunakan dalam jangka waktu yang lama
   
   Tidak dipungkiri bahwa struktur data bisa jadi akan bertahan lebih lama ketimbang aplikasi. Bisa saja aplikasi akan dibuat ulang tanpa mengubah skema datanya.
2. Nama merupakan sebuah kontrak
   
   Objek database atau nama variable data dalam aplikasi direferensikan oleh nama dari database sehingga nama database merupakan kontrak untuk suatu objek. Dengan anggapan itu, maka bisa saja mengubah nama suatu kolom / tabel dalam database maka akan merusak aplikasi itu sendiri.
3. Peralihan antar developer
   
   Konsistensi sebuah nama dalam database akan mempermudah / menyingkat waktu seorang developer untuk membaca / mempelajarinya. Bayangkan saja apabila ada developer baru yang bergabung dalam tim maka dia membutuhkan waktu untuk mempelajari skema data yang sudah dibuat.

## Penamaan (Naming Convention)
1. Hindari penggunaan tanda kutip `"` atau spasi 
   
   Penggunaan tanda kutip atau tanda baca dalam sebuah nama akan sangat menyulitkan jika kita ingin mengubah (rename) nama tersebut.
   
   Contoh: `"FirstName"` atau `"First Name"`
2. Gunakan huruf kecil semua `lowercase`
   
   Identifier harus ditulis dengan huruf kecil semua (lowercase) termasuk table, kolom, view, dll. Dalam beberapa kasus lowercase akan lebih nyaman dibaca.

   Contoh: `fist_name` bukan `First_Name`
3. Jangan gunakan tipe data sebagai nama, atau kata yang sudah dipakai oleh framework / bahasa pemrograman tertentu.
   
   Pastinya akan terjadi konflik jika kita menggunakan nama yang sudah didefinisikan sebagai nama dari sebuah platform itu sendiri. Ganti nama yang sudah ada dengan sinonim yang lain. jika dipaksakan, maka bisa jadi masalah yang serius dikemudian hari.

   Contoh: `type`,`text`, `timestamp`, `model`, `int`

4. Gunakan snake case (underscore sebagai pemisah antar kata) 
   Pemisah dengan _underscores_ akan lebih mudah dibaca ketimbang menggunakan camel case (huruf besar di depan)
   
   Contoh: `word_count`, `team_member_id` bukan `wordcount` atau `wordCount`
5. Gunakan kata lengkap bukan singkatan, kecuali singkatan yang sudah umum yang tidak ambigu.
   
   Nama objek harus merupakan kata utuh / lengkap. Secara umum, hindari singkatan, terutama jika merupakan jenis yang menghilangkan huruf vokal. Sebagian besar database SQL mendukung setidaknya nama 30 karakter yang seharusnya lebih dari cukup untuk beberapa kata utuh PostgreSQL mendukung hingga 63 karakter untuk pengidentifikasi.

    Contoh: `middle_name` bukan `mid_nm`


## Key Field
1. Primary Key
   
   Kolom tunggal (single column) field primary harus diberi nama `id`, singkat, simple, tidak ambigu. Dengan begitu ketika kita ingin melakukan query join maka kita sudah tahu nama field yang akan dijoinkan. kemudian nama kolom yang lain dipisah degan garis bawah (underscores).

   ```sql
    CREATE TABLE person (
        id            bigint PRIMARY KEY,
        full_name     text NOT NULL,
        birth_date    date NOT NULL
    );
   ```
2. Foreign Key
   
   Nama field foreign key harus kombinasi dari nama kolom dengan kolom referensinya.

   ```sql
   CREATE TABLE team_member (
        team_id     bigint NOT NULL REFERENCES team(id),
        person_id   bigint NOT NULL REFERENCES person(id),
        CONSTRAINT  team_member_pkey PRIMARY KEY (team_id, person_id)
    );
   ```

## Sumber
https://github.com/RootSoft/Database-Naming-Convention
   

   