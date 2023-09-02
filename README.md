# TUGAS PROYEK PEMROGRAMAN BERBASIS KERANGKA KERJA

- Nama: Fadhilla Ilham Robbani
- NPM: G1A020036
- Kelas: B1

## 1. Jelaskan Tentang Routes pada Laravel! 


Routes atau routing di Laravel adalah sebuah sistem yang mengatur bagaimana URL dihubungkan ke halaman tertentu. Sistem ini memungkinkan pengguna untuk berpindah halaman di dalam aplikasi Laravel dengan mudah.

Routing di Laravel dapat dibagi menjadi beberapa bagian, yang masing-masing memiliki fungsinya sendiri. File-file routing terletak di folder routes/, dan berisi empat file yaitu `api.php, channels.php, console.php, dan web.php.`

Untuk membuat kode routingnya kita bisa menulisnya di file web.php atau api.php. Untuk file web.php adalah untuk mendefinisikan route untuk web interface. Misalnya untuk mengakses ke halaman user seperti `http://www.example.com/user`. Sedangkan pada api.php routing lebih condong digunakan untuk mendefinisikan api routes sehingga untuk mengaksesnya akan ada prefix /api pada alamat web. Contohnya `http://www.example.com/api/user`. Pada soal ini contohnya yang biasanya digunakan adalah menuliskan routes di web.php

**a. Basic Routing**

Routing Laravel yang paling dasar yang berguna untuk menerima atau mengeksekusi perintah HTTP. Di laravel dapat menggunakan:
```php
Route::get($uri, $callback);

Route::post($uri, $callback);

Route::put($uri, $callback);

Route::patch($uri, $callback);

Route::delete($uri, $callback);

Route::options($uri, $callback);
```

Adapun contohnya sebagai berikut:
```php
use Illuminate\Support\Facades\Route;

Route::get('/greeting', function () {

return 'Hello World';

});
```
Penjelasan:

`get `=> adalah http method yang digunakan untuk menerima respon

`/greeting` =>alamat URI yang kita definisikan untuk kita akses di browser

`return “Hello World”` => nilai yang kita tampilkan dari callback function ke halaman web

**b. Routes Parameter**

Route parameter adalah variabel yang dapat digunakan dalam URL rute Laravel. Parameter dapat digunakan untuk membuat URL yang lebih fleksibel dan mudah diingat.

Untuk membuat route parameter, kita dapat menggunakan kurung kurawal di URL rute. Misalnya, untuk membuat route parameter bernama name, kita dapat menggunakan URL berikut:
```php
Route::get('/user/{name}', function ($name) {

// Do something with the name parameter

});
```
Saat pengguna mengunjungi URL ini, “name” akan diisi dengan nilai yang dimasukkan pengguna. Nilai ini kemudian dapat diakses dalam handler route, yaitu fungsi yang dijalankan saat rute dipanggil

**c. Optional Parameter**

Optional parameter adalah parameter yang dapat diisi atau tidak diisi saat memanggil rute Laravel. Optional parameter ditandai dengan tanda tanya di belakang nama parameter.

Untuk membuat optional parameter, kita dapat menggunakan tanda tanya di belakang nama parameter saat membuat rute. Misalnya, untuk membuat optional parameter bernama name, kita dapat menggunakan URL berikut:
```php
Route::get('/user/{name?}', function ($name = newuser) {

// Do something with the name parameter

});
```
Saat pengguna mengunjungi URL ini, “name” akan diisi dengan nilai yang dimasukkan pengguna, atau newuser jika tidak ada nilai yang dimasukkan. Nilai ini kemudian dapat diakses dalam handler route, yaitu fungsi yang dijalankan saat rute dipanggil.

**d. Named routes**

Named routes adalah rute yang diberi nama. Nama rute dapat digunakan untuk merujuk ke rute tersebut di tempat lain dalam aplikasi.

Untuk memberi nama rute, kita dapat menggunakan metode name() pada rute. Misalnya, untuk memberi nama rute /users/{id} dengan nama profile, kita dapat menggunakan kode berikut:
```php
Route::get('/users/{id}', function ($id) {

// Do something with the user

})->name('profile');
```
Nama rute dapat digunakan di tempat lain dalam aplikasi dengan menggunakan metode route(). Misalnya, untuk mengarahkan pengguna ke halaman profil pengguna tertentu, kita dapat menggunakan kode berikut:
```php
return redirect()->route('profile', ['id' => 1]);
```
Sebenarnya masih banyak lagi yang bisa dipelajari terkait routes. Lebih lengkapnya ada di dokumentasi laravel : https://laravel.com/docs/10.x/routing

## 2. Jelaskan Tentang Database pada Laravel!

Laravel memiliki dukungan yang kuat untuk database. Laravel menyediakan berbagai fitur yang memudahkan pengembang untuk berinteraksi dengan database, seperti:

**Model:** Model adalah kelas PHP yang mewakili tabel database. Model digunakan untuk mengakses dan memanipulasi data dalam database. Berikut adalah contohnya, misalnya model untuk tabel user:
```php
class User extends Model { 
	protected  $table = 'users'; 
	protected  $fillable = [ 'name', 'email', 'password', ]; 
}
```

**Migration:** Migration adalah file PHP yang digunakan untuk membuat, mengubah, dan menghapus tabel database. Migration digunakan untuk menjaga konsistensi database selama pengembangan aplikasi. Migration juga bisa dibilang sebagai version control untuk database di laravel. Yang artinya kita bisa melihat riwayat dari perubahan struktur database kita. Di laravel kita bisa membuat migration dengan perintah artisan `php artisan make:migration` yang diikuti nama migration yang ingin kita buat. Hasilnya akan disimpan di folder database/migration. Selengkapnya bisa dilihat di dokumentasi: https://laravel.com/docs/10.x/migrations

**Query Builder:** Query Builder adalah API yang menyediakan antarmuka yang lancar untuk membuat dan menjalankan kueri SQL. Dengan begitu, kita tidak perlu repot-repot menulis kode SQL secara manual dalam program. Hal ini tentunya meningkatkan efisiensi, kemudahan dalam penulisan kode SQL. Lengkapnya ada di dokumentasinya: https://laravel.com/docs/10.x/queries

**Eloquent:** Eloquent adalah ORM (Object-Relational Mapping) yang menyediakan cara yang elegan untuk mengakses dan memanipulasi data dalam database. Mirip seperti query builder, pada dasarnya eloquent memudahkan kita mengatur database dan menulis SQL di laravel. Dengan Eloquent, kita bisa berinteraksi dengan tabel di database secara sinkron dalam kode php. Dengan begitu kita bisa dengan mudah menulis relasi tabel, insert,update, delete, dan sebagainya terhadap data ataupun tabel di database.
Dokumentasi Eloquent: https://laravel.com/docs/10.x/eloquent
***
Jika yang dimaksud soal adalah folder database pada laravel, maka terdapat 3 subfolder di dalamnya yaitu factories, migration, dan seeder.

Factory adalah kelas PHP yang dapat digunakan untuk membuat data palsu untuk database. Factory sering digunakan untuk mengisi database dengan data uji saat menjalankan tes unit.

Seeder adalah kelas PHP yang digunakan untuk mengisi database dengan data yang sebenarnya. Seeder sering digunakan untuk mengisi database dengan data awal saat aplikasi pertama kali dijalankan. Kita bisa memasukkan data dari factories ke seeder agar dummy data bisa kita masukkan ke database.
Untuk dokumentasi bagaimana cara seeding di laravel ada pada link berikut: https://laravel.com/docs/10.x/seeding

Migration adalah file PHP yang digunakan untuk membuat, mengubah, dan menghapus tabel database. Migration digunakan untuk menjaga konsistensi database selama pengembangan aplikasi. Sudah dijelaskan di bagian sebelumnya

