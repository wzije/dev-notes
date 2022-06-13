# Laravel Conventions
## Daftar isi
- Naming Controllers
- Naming database tables in Laravel
- Pivot tables
- Table columns names
- Primary Key
- Foreign Keys
- Variables
- Naming Conventions for models
- Naming Models in Laravel
- Model properties
- Model Methods
- Relationships
- hasOne or belongsTo relationship (one to many)
- hasMany, belongsToMany, hasManyThrough (one to many)
- Polymorphic relationships
- Controllers
- Method naming conventions in controllers
- Traits
- Blade view files

## Naming Controllers
Controller harus berbentuk kata tunggal, tidak ada spasi diantara kata, dan diakihir dengan kata `Controller`. Juga harus kata harus _Capitalize_  (seperti: BlogController, not blogcontroller).

CONTOH  : BlogController, AuthController, UserController.

JANGAN  : UsersController (karena mengandung kata jamak), Users (karena tidak ada Controller suffix).

## Naming database tables di Laravel
Nama tabel database harus `lower case` dengan penghubung garis bawah antar kata (snake_case), dan harus berbentuk kata jamak.

CONTOH: posts, project_tasks, uploaded_images.

JANGAN!!: all_posts, Posts, post, blogPosts

## Pivot tables
Tabel pivot harus `lower case` dan setiap model dalam urutas alfabet, serta dihubungkan dengan garis bawah antar katanya (snake_case).

CONTOH: post_user, task_user etc.

JANGAN!!: users_posts, UsersPosts.

## Nama kolom tabel
Nama kolom tabel harus `lower case` dan dihubungkan dengan garis bawah antar katanya. kamu tidak perlu juga mereferensi nama tabelnya.

CONTOH: post_body, id, created_at.

JANGAN!!: blog_post_created_at, forum_thread_title, threadTitle.

## Primary Key
Umumnya adalah bernama `id`

## Foreign Keys
Foreign keys harus nama model singular dengan `_id` yang disematkan. Asumsikan bahwa PK dalam urutan tabel adalah kolom `id`.

CONTOH: comment_id, user_id.

## Variables
Variabel biasa harus berbentuk camelCase dengan huruf kata pertama kecil.

CONTOH: $users = ..., $bannedUsers = ....

JANGAN!!: $all_banned_users = ..., $Users=....

Jika wariabel berisi sebuah array atau collection pada banyak item, maka variabel harus berbentuk jamak. selain itu harus berbentuk tunggal.

CONTOH: $users = User::all(); (jika untuk mendapatkan data banyak berbentuk array / collection), tapi $user = User::first() (untuk mendapatkan data tunggal )

## Naming Conventions untuk models
1. Naming Models dalam Laravel
   Sebuah model harusnya kata tunggal, tidak ada spasi antar kata, dan berupa capitalized.

    CONTOH: `User` (`\App\User` or `\App\Models\User`, etc), `ForumThread`, `Comment`.

    JANGAN!!: Users, ForumPosts, blogpost, blog_post, Blog_posts.

    Secara umum, model-mu haruslah dapat secara otomatis menentukan dari tabel database apa yang harus digunakan dari metode berikut:

    ```php 
    public function getTable()
    {
        if (! isset($this->table)) {
            return str_replace(
                '\\', '', Str::snake(Str::plural(class_basename($this)))
            );
        }
        return $this->table;
    }
    ```

    Namun, tentu kamu hanya cukup mungatur `$this->table` dalam model-mu. Lihat bagian table naming conventions.

    Direkomendasikan untuk membuat model dan migration dalam waktu yang bersamaan menggunakan perintah artisan berikut, untuk dapat secara otomatis mengenerate file model dan migration. 
    ```bash
    php artisan make:model -m ForumPost 
    ```

2. Model properties
    Properti model harus `lower case` dan berbentuk `snake_case`. mereka juga harus memiliki nama yang sama dengan nama kolom.

    CONTOH: $this->updated_at, $this->title.

    JANGAN!!: $this->UpdatedAt, $this->blogTitle.

3. Model Methods
    Fungsi dalam model harus berbentuk camelCase yang diawali dengan hurus kecil pada kata pertama.

    CONTOH: public function get(), public function getAll().

    JANGAN!!: public function GetPosts(), public function get_posts().

4. Relationships
   1. hasOne or belongsTo relationship (one to many)

      Kata harus berbentuk tunggal dan mengikuti naming convention pada fungsi model pada umumnya. camelCase yang diawali dengan hurus kecil pada kata pertama

      CONTOH: public function postAuthor(), public function phone().

   2. hasMany, belongsToMany, hasManyThrough (one to many)
      harus berbentuk sama dengan convention oneToMany, tapi kata harus berbentuk jamak.

      CONTOH: public function comments(), public function roles().

5. Polymorphic relationships
    Ini bisa jadi sedikit canggung untuk mendapatkan nama yang sesuai.

    Idealnya, kamu ingin sebuah fungsi seperti ini:

    ```php
    public function category()
    {
        return $this->morphMany('App\Category', 'categoryable');
    }
    ```

    Dana laravel akan secara default berasumsi bahwa terdapat sebuah categoryable_id dan categoriable_type.

    Tapi kamu dapat menggunakan pilihan parameter lain untuk morphMany ( public function morphMany($related, $name, $type = null, $id = null, $localKey = null)) untuk mengubah default.

## Controllers
### Method naming conventions in controllers
Bagian ini harus mengikuti aturan yang sama dengan fungsi dari model. Seperti. camelCase (karakter kata pertama lowerCase ).

sebagai tambahan, untuk normal operasi CRUD harus menggunakan salah satu dari nama fungsi berikut.

```bash
VERB	URI	TYPICAL METHOD NAME	ROUTE NAME
GET	    /photos	index()	photos.index
GET	    /photos/create	create()	photos.create
POST	/photos	store()	photos.store
GET	    /photos/{photo}	show()	photos.show
GET	    /photos/{photo}/edit	edit()	photos.edit
PUT/PATCH	/photos/{photo}	update()	photos.update
DELETE	/photos/{photo}	destroy()	photos.destroy
```

### Traits
Traits harus berwujud kata keterangan.

CONTOH: Notifiable, Dispatchable, etc.

### Blade view files
File Blade harus lower case dan snake case.

CONTOH: all.blade.php, all_posts.blade.php, etc

## Sumber
https://webdevetc.com/blog/laravel-naming-conventions/#section_naming-controllers