# Rust Fixme 1

## Description

Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag!
Download the Rust code here.

## Writeup

flag: picoCTF{4r3_y0u_4_ru$t4c30n_n0w?}

Je ne connais pas Rust mais en regardant la doc, l'outil de
build utilisé est `cargo`

```bash
 cargo build
    Updating crates.io index
  Downloaded either v1.13.0
  Downloaded crossbeam-utils v0.8.20
  Downloaded crossbeam-epoch v0.9.18
  Downloaded xor_cryptor v1.2.3
  Downloaded rayon-core v1.12.1
  Downloaded crossbeam-deque v0.8.5
  Downloaded rayon v1.10.0
  Downloaded 7 crates (379.2KiB) in 0.24s
   Compiling crossbeam-utils v0.8.20
   Compiling rayon-core v1.12.1
   Compiling either v1.13.0
   Compiling crossbeam-epoch v0.9.18
   Compiling crossbeam-deque v0.8.5
   Compiling rayon v1.10.0
   Compiling xor_cryptor v1.2.3
   Compiling rust_proj v0.1.0 (/home/sklae/Documents/00_projets_perso/picoCTF/GeneralSkills/easy/RustFixme/fixme1)
error: expected `;`, found keyword `let`
 --> src/main.rs:5:37
  |
5 |     let key = String::from("CSUCKS") // How do we end statements in Rust?
  |                                     ^ help: add `;` here
...
8 |     let hex_values = ["41", "30", "20", "63", "4a", "45", "54", "76", "01", "1c", "7e", "59", "63", "e1", "61", "25", "7f",...
  |     --- unexpected token

error: argument never used
  --> src/main.rs:26:9
   |
25 |         ":?", // How do we print out a variable in the println function?
   |         ---- formatting specifier missing
26 |         String::from_utf8_lossy(&decrypted_buffer)
   |         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ argument never used
   |
help: format specifiers use curly braces, consider adding a format specifier
   |
25 |         ":?{}", // How do we print out a variable in the println function?
   |            ++

error[E0425]: cannot find value `ret` in this scope
  --> src/main.rs:18:9
   |
18 |         ret; // How do we return in rust?
   |         ^^^ help: a local variable with a similar name exists: `res`

For more information about this error, try `rustc --explain E0425`.
error: could not compile `rust_proj` (bin "rust_proj") due to 3 previous errors

```

J'en déduis que ce sont les erreurs de syntaxe que l'on doit corriger.
Une fois dans le code source, on voit qu'il y a des commentaires
aux endroits qui ont besoin d'une modification.

Pour le premier commentaire, on ajoute un ';' :

```rust
let key = String::from("CSUCKS") // How do we end statements in Rust?
```

```rust
let key = String::from("CSUCKS"); // How do we end statements in Rust?
```

Le second commentaire, on change `ret` pour `return` :

```rust
if res.is_err() {
        ret; // How do we return in rust?
    }
```

```rust
if res.is_err() {
        return; // How do we return in rust?
    }

```

Enfin, le troisième demande comment faire une print d'une variable :

```rust
 println!(
        ":?", // How do we print out a variable in the println function? 
        String::from_utf8_lossy(&decrypted_buffer)
    );

```

Il manque une string litteral pour le format :

```rust
println!(
        "{}, :?", // How do we print out a variable in the println function?
        String::from_utf8_lossy(&decrypted_buffer)
    );
```

On recompile:

```
 cargo build
   Compiling rust_proj v0.1.0 (/home/sklae/Documents/00_projets_perso/picoCTF/GeneralSkills/easy/RustFixme/fixme1)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.35s
```

Tout est beau, alors on peut run:

```
 cargo run
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.03s
     Running `target/debug/rust_proj`
picoCTF{4r3_y0u_4_ru$t4c30n_n0w?}, :?
```
