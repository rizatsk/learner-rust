# Belajar Rust Dasar  

## Install RUST dengan menggunakan tools RUSTUP

link: <https://www.rust-lang.org/tools/install>

## Membuat project Rust dengan Cargo

Cargo adalah package manager bawaan dari RUST, sama seperti node dan npm dari Javascript

```bash
cargo new NAME_PROJECT
```

## Print Hello World

```Rust
print!("Hello world") // Tidak terdapat enter jadi akan 1 line,
println!("Hello, world!") // auto terdapat enter
```

## Menjalankan project dengan CARGO

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

## Unit test

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

## Variable

Varibale RUST itu static  
Variable pada RUST ketika sudah diisi datanya itu tidak dapat diubah, disebut immutable  
RUST juga memperbolehkan variable yang bisa dirubah lagi, disebut mutable dengan let mut  

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

### Variable Character

Variable character mendeskripsikanya dengan menggunakan kutip 1 dan hanya satu karakter saja

```Rust
let char_1 = 'r';
println!("Ini adalah variable character {char_1}");
```

### Variable Tuple

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

### Variable Array

Variable array nilainya hanya boleh 1 type, saja dan sudah ditentukan berapa banyak nilainya  
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

### Variable Constant

Variable constant itu tidak memiliki **"Mutable"**, dia "**I2mutable**" dan sudah harus ada isinya sejak awal code  
dan harus juga diisikan type datanya di awal,  
biasanya dengan menggunakan huruf besar penamaan variablenya

```Rust
const MAXIMUM: i32 = 100;
const MINIMUM: i32 = 0;

println!("Maximum {MAXIMUM} dan minimum {MINIMUM}");
```

### Variable String

Variable yang disimpan didalam **"Heap"** dan dapat diubah isinya,  
berbeda dengan &str yang dimana datanya itu fix disimpan dialam stack, jadi ketika diimutable dia membuat data baru,  
kalau String dia benar benar mengubah isinya.

```Rust
let mut name = String::from("Rizat Sakmir");
name.push_str("seorang Software Engineer");
println!("{name}");

// Replace membuat nilai baru
let udin = name.replace("Rizat", "Udin");
println!("{udin}");
```

## Ownership

Yaitu dimana kepemilikan dari data

```Rust
/* Data yang di stack akan di copy */
let name = "Rizat Sakmir";
let name_copy = name;

println!("{name}");
println!("{name_copy}");

// Heap
let name_3 = String::from("Udin");
let name_3_copy = name_3;

/* println!("{name_3}"); ini akan error karena owner dari data name_3
sudah menjadi name_3_copy jadi tidak bisa digunakan lagi */
println!("{name_3_copy}");
```

## Clone

Data yang disimpan pada heap itu dapat diclone

```Rust
let name = String::from("Clone rizat");
let name_clone = name.clone();

println!("{name}");
println!("{name_clone}");
```

## Perkondisian

```Rust
let umur_a = 20;
let umur_b = 24;
let oke = "";

if umur_a < umur_b {
    println!("Ya, umur a lebih kecil dari umur b");
} else if umur_a >= umur_b {
    println!("Oke test aja kawan");
} else {
    println!("Tidak, umur a lebih besar dari umur b");
}

if oke.is_empty() {
    println!("variable oke tidak ada isinya")
}
```

## Perulangan Loop

Perulangan loop ketika ingin berhenti maka menggunakan **"Break"**
dan ingin menghentikan perulangan saat ini, melanjutkan ke perulangan selanjutnya gunakan **"Continue"**  
dan tidak melanjutkan kode dibawahnya

```Rust
let mut counter = 0;
loop {
    counter += 1;
    if counter > 10 {
        break;
    } else if counter % 2 == 0 {
        continue;
    }

    println!("Counter: {counter}");
}
```

### Loop Label

Biasanya membuat loop di dalam loop, ketika ingin menghentikan loop yang diatasnya
itu kita bisa menggunakan **"Label"**, cukup dipanggil saja **"break"** dengan nama labelnya

```Rust
let mut number = 1;
'outer: loop {
    let mut i = 1;
    loop {
        if number > 10 {
            break 'outer;
        }

        println!("{number} x {i} = {}", number * i);
        i += 1;
        if i > 10 {
            break;
        }
    }
    number += 1;
}
```

### While

Perulangan yang terdapat perkondisianya

```Rust
let mut counter = 0;
while counter <= 10 {
    if counter % 2 == 0 {
        println!("Counter: {counter}");
    }

    counter += 1;
}
```

### For Loop

Perulangan sampai habis dari data array

```Rust
let array = ['A', 'B', 'C', 'D', 'E'];

for value in array {
    println!("Value in array {value}");
}
```

## Range

Yaitu type data range **"exclusive"** antar start dan end, contoh disini  
yaitu dari 1 sampai 3, yang endnya tidak diambil  
**"Inclusive"** itu endnya tetap diambil

```Rust
let array = ['A', 'B', 'C', 'D', 'E'];
// Exlcusive
let range = 1..3;

println!("Ini range exclusive");
for value in range {
    println!("Value in array {}", array[value]);
}

// Inclusive
println!("Ini range inclusive");
let range_incusive = 1..=3;
for value in range_incusive {
    println!("Value in array {}", array[value]);
}
```

## Function

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

### Function Ownership

Yaitu dimana data yang disimpan pada **Stack** hanya menggunakan datanya saja  
tanpa mengambil kepemilikanya, dan untuk **Heap** dia akan memindahkan kepemelikan datanya.

```Rust
fn function_ownership() {
    let number = 10;
    print_number(number);
    println!("Ini function ownership number: {number}");

    let name = String::from("Rizat Sakmir");
    hi(name);
    println!("Hai function ownership name: {name}"); // ini akan error karena kepemilikan atanya sudah dipindahkan
}

fn print_number(number: i32) {
    println!("Number : {number}");
}

fn hi(name: String) {
    println!("Hi, {name}");
}
```

### Borrow

Yaitu untuk mengambil data dari variable yang disimpan di **Heap** tanpa mengambil  
kepemlikanya, cukup menggunakan **"&"**.  
Menggunakan borrowing default datanya tidak boleh diubah, karena datanya bersifat immutable

```Rust
fn function_ownership() {
    let name = String::from("Rizat Sakmir");
    hi(&name);
    println!("Hai function ownership name: {name}");
}

fn hi(name: &String) {
    println!("Hi, {name}");
}
```

#### Borrow Mutable

Untuk dapat mengubah data borrowing dapat menggunakan **"&mut"**  
