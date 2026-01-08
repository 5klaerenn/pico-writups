# Rust fixme3

## Description

Have you heard of Rust? 
Fix the syntax errors in this Rust file to print the flag!
Download the Rust code here. 

## Write-up

flag: 

Comme pour le précédent challenge, on commence par faire un build pour
voir l'erreur qui se produit :

```bash
 cargo build
   Compiling crossbeam-utils v0.8.20
   Compiling rayon-core v1.12.1
   Compiling either v1.13.0
   Compiling crossbeam-epoch v0.9.18
   Compiling crossbeam-deque v0.8.5
   Compiling rayon v1.10.0
   Compiling xor_cryptor v1.2.3
   Compiling rust_proj v0.1.0 (/home/sklae/Documents/00_projets_perso/picoCTF/GeneralSkills/easy/RustFixme/fixme3)
error[E0133]: call to unsafe function `std::slice::from_raw_parts` is unsafe and requires unsafe function or block
  --> src/main.rs:31:31
   |
31 |         let decrypted_slice = std::slice::from_raw_parts(decrypted_ptr, decrypted_len);
   |                               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ call to unsafe function
   |
   = note: consult the function's documentation for information on how to avoid undefined behavior

For more information about this error, try `rustc --explain E0133`.
error: could not compile `rust_proj` (bin "rust_proj") due to 1 previous error
```

On doit faire des `unsafe operations`. Un lien vers la doc est fourni
dans le code source. 

Pour le moment, je vais me limiter à mettre la ligne dans un bloc unsafe pour pouvoir continuer. 

```rust
        // Unsafe operation: calling an unsafe function that dereferences a raw pointer
        unsafe{
            let decrypted_slice = std::slice::from_raw_parts(decrypted_ptr, decrypted_len);
            borrowed_string.push_str(&String::from_utf8_lossy(decrypted_slice));
        }
```

On essaye de build : 

```bash
 cargo build
   Compiling rust_proj v0.1.0 (/home/sklae/Documents/00_projets_perso/picoCTF/GeneralSkills/easy/RustFixme/fixme3)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.36s
```

Bonne nouvelle ! 
Et maintenant, le run

```bash
 cargo run
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.03s
     Running `target/debug/rust_proj`
Using memory unsafe languages is a: PARTY FOUL! Here is your flag: picoCTF{n0w_y0uv3_f1x3d_1h3m_411}
```

Sans les connaissances en C, je ne sais pas si j'aurais compris la moindre des
choses qu'on a fait ici. Mais Rust attendra à un moment de plus d'espace
mental. 


