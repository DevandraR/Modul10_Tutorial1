# 1.2. Understanding how it works

```
PS D:\UI\SEM 4\Pemrograman Lanjut\Rust\timer_future> cargo run
   Compiling timer_future v0.1.0 (D:\UI\SEM 4\Pemrograman Lanjut\Rust\timer_future)
    Finished dev [unoptimized + debuginfo] target(s) in 0.53s
     Running `target\debug\timer_future.exe`
Devan's Computer : hey hey
Devan's Computer : howdy!
Devan's Computer : done!
PS D:\UI\SEM 4\Pemrograman Lanjut\Rust\timer_future>
```
Kenapa "hey hey" dicetak sebelum "howdy!" ? karena ada spawn dan executor, lalu spawn itu pemalah, jadi tidak ada dieksekusi tanpa adanya request eksplisit, pada kode ini terdapat executor yang membuat request tersebut.

# 1.3. Multiple Spawn and removing drop

1. Multiple Spawn
```
PS D:\UI\SEM 4\Pemrograman Lanjut\Rust\timer_future> cargo run
   Compiling timer_future v0.1.0 (D:\UI\SEM 4\Pemrograman Lanjut\Rust\timer_future)
    Finished dev [unoptimized + debuginfo] target(s) in 0.49s
     Running `target\debug\timer_future.exe`
Devan's Computer : hey hey
Devan's Computer : howdy!
Devan's Computer : howdy2!
Devan's Computer : howdy3!
Devan's Computer : done!
Devan's Computer : done3!
Devan's Computer : done2!
PS D:\UI\SEM 4\Pemrograman Lanjut\Rust\timer_future>
```
pasangan antara howdy dan done tidak sama, urutan pencetakannya tidak sama karena semuanya dijalankan secara concurrent atau bersamaan, jadi urutan pencetakannya tidak pengaruh karena seharusnya bersamaan.

2. Removing Drop
```
PS D:\UI\SEM 4\Pemrograman Lanjut\Rust\timer_future> cargo run
   Compiling timer_future v0.1.0 (D:\UI\SEM 4\Pemrograman Lanjut\Rust\timer_future)
    Finished dev [unoptimized + debuginfo] target(s) in 0.53s
     Running `target\debug\timer_future.exe`
Devan's Computer : hey hey
Devan's Computer : howdy!
Devan's Computer : howdy2!
Devan's Computer : howdy3!
Devan's Computer : done2!
Devan's Computer : done!
Devan's Computer : done3!

```
Spawner sifatnya seperti antrian atau queue dari perintah, jika kita spawn maka akan ditempatkan pada queue tersebut, lalu saat dijalankan oleh executor akan diambil semua, namun jika kita tidak drop maka queue akan berjalan terus.