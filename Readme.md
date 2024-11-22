## Belajar Rust Dasar

### Install RUST dengan menggunakan tools RUSTUP

link: <https://www.rust-lang.org/tools/install>

### Membuat project Rust dengan Cargo

Cargo adalah package manager bawaan dari RUST, sama seperti node dan npm dari Javascript

```bash
cargo new NAME_PROJECT
```

### Print Hello World

```Rust
print!("Hello world") // Tidak terdapat enter jadi akan 1 line,
println!("Hello, world!") // auto terdapat enter
```

### Menjalankan project dengan CARGO

RUST itu tidak menjalankan code kita, dia akan mengcompile menjadi binnary, lalu menjalankan file binnary tersebut
yang ada didalam file target.

Mode debug

```bash
cargo run
cargo build
```

Relase Mode

```bash
cargo build --release
```

### Unit test

RUST tidak bisa terdapat lebih dari 1 function dia hanya menjalankan 1 main aja yaitu function
dalam membuat unit test nya bisa menggunakan attribute #[test]

```Rust
#[test]
fn test_hello() {
    println!("Hello i am Rizat");
}
```

Run all test

```bash
cargo test
```

Run per function

```bash
cargo test nama_test_fuction -- --exact --nocapture
```

### Variable

Varibale RUST itu static <br>
Variable pada RUST ketika sudah diisi datanya itu tidak dapat diubah, disebut immutable <br />
RUST juga memperbolehkan variable yang bisa dirubah lagi, disebut mutable dengan let mut <br />

```Rust
// Variable immutable
let name = "Rizat Sakmir";
let job = "Software Engineer";
println!("Hello saya {}, seorang {}", name, job); // menggunakan subtitusi

// Variable mutable
let mut working_in = "Dartmedia";
println!("Working in years 2022 {}", working_in);

working_in = "Adira Finance";
println!("Working in years 2023 {working_in}");
```

#### Variable Character

Variable character mendeskripsikanya dengan menggunakan kutip 1 dan hanya satu karakter saja

```Rust
let char_1 = 'r';
println!("Ini adalah variable character {char_1}");
```

#### Variable Tuple

Variable tuple tidak dapat ditambahkan atau dikurangi, dan tidak dapat merubah type isinya.

```Rust
let mut data_tuple = ('a', "Rizat Sakmir", 24);
println!("Ini data tuple pertama {}", data_tuple.0);

data_tuple.0 = 'b';
println!("Ini data tuple setelah dirubah {}, {}, {}", data_tuple.0, data_tuple, data_tuple.2);

// Destructuring
let (a, _, c) = data_tuple;
println!("Membongkar isi dari tuple {a}, {c}");
```

#### Variable Array

Variable array nilainya hanya boleh 1 type, saja dan sudah ditentukan berapa banyak nilainya <br />
tidak seperti bahasa pemograman lain yang dynamis

```Rust
let mut data_array = ["Nasi", "Ayam suwir", "Daun Pisang"];
println!("Data semua array {:?}", data_array);

let [array_1, _, array_3] = data_array;
println!("Data Array 1 {array_1}");
println!("Data Array 2 {}", data_array[1]);
println!("Data Array 3 {array_3}");

data_array[0] = "Ketan";
println!("Data array pertama setelah dirubah itu {}", data_array[0]);

let length_array = data_array.len();
    println!("Jumlah data array {length_array}");
```

### Perkondisian

```Rust
let umur_a = 20;
let umur_b = 24;
let oke = "";

if umur_a < umur_b {
    println!("Ya, umur a lebih kecil dari umur b")
} else {
    println!("Tidak, umur a lebih besar dari umur b");
}

if oke.is_empty() {
    println!("variable oke tidak ada isinya")
}
```

### Function

```Rust
fn plus(number_1: i32, number_2: i32) -> i32 {
    let result = number_1 + number_2;
    return result;
}

#[test]
fn test_function() {
    let x = plus(10, 5);

    println!("The value of x is: {x}");

    let y = {
        let x = 10;
        x + 100
    };
    println!("Result y {y}");
}
```
