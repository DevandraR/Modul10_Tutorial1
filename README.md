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

