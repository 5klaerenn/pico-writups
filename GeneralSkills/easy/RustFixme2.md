# Rust fixme 2

## Description

The Rust saga continues? 
I ask you, can I borrow that, pleeeeeaaaasseeeee? 
Download the Rust code here. 

## Write-up

flag: picoCTF{4r3_y0u_h4v1n5_fun_y31?}

Comme pour la première partie du challenge, il y a des commentaires
aux endroits que l'on devra modifier. 

Premier : 

```rust
fn decrypt(encrypted_buffer:Vec<u8>, borrowed_string: &String){ // How do we pass values to a function that we want to change?
```

et plus bas : 

```rust
  let party_foul = String::from("Using memory unsafe languages is a: "); // Is this variable changeable?
  decrypt(encrypted_buffer, &party_foul); // Is this the correct way to pass a value to a function so that it can be changed?
```

Quand on essaye de `build`, on a l'erreur suivante : 

```rust
 cargo build
   Compiling rust_proj v0.1.0 (/home/sklae/Documents/00_projets_perso/picoCTF/GeneralSkills/easy/RustFixme/fixme2)
error[E0596]: cannot borrow `*borrowed_string` as mutable, as it is behind a `&` reference
 --> src/main.rs:9:5
  |
9 |     borrowed_string.push_str("PARTY FOUL! Here is your flag: ");
  |     ^^^^^^^^^^^^^^^ `borrowed_string` is a `&` reference, so the data it refers to cannot be borrowed as mutable
  |
help: consider changing this to be a mutable reference
  |
3 | fn decrypt(encrypted_buffer:Vec<u8>, borrowed_string: &mut String){ // How do we pass values to a function that we want to change?
  |                                                        +++

error[E0596]: cannot borrow `*borrowed_string` as mutable, as it is behind a `&` reference
  --> src/main.rs:20:5
   |
20 |     borrowed_string.push_str(&String::from_utf8_lossy(&decrypted_buffer));
   |     ^^^^^^^^^^^^^^^ `borrowed_string` is a `&` reference, so the data it refers to cannot be borrowed as mutable
   |
help: consider changing this to be a mutable reference
   |
 3 | fn decrypt(encrypted_buffer:Vec<u8>, borrowed_string: &mut String){ // How do we pass values to a function that we want to change?
   |                                                        +++

For more information about this error, try `rustc --explain E0596`.
error: could not compile `rust_proj` (bin "rust_proj") due to 2 previous errors
```

La première modif à faire est donc de rendre le param borrowed_string mutable. 

Le build suivant amène l'erreur : 

```bash
 cargo build
   Compiling rust_proj v0.1.0 (/home/sklae/Documents/00_projets_perso/picoCTF/GeneralSkills/easy/RustFixme/fixme2)
error[E0308]: mismatched types
  --> src/main.rs:35:31
   |
35 |     decrypt(encrypted_buffer, &party_foul); // Is this the correct way to pass a value to a function so that it can be cha...
   |     -------                   ^^^^^^^^^^^ types differ in mutability
   |     |
   |     arguments to this function are incorrect
   |
   = note: expected mutable reference `&mut String`
                      found reference `&String`
note: function defined here
  --> src/main.rs:3:4
   |
 3 | fn decrypt(encrypted_buffer:Vec<u8>, borrowed_string: &mut String){ // How do we pass values to a function that we want to...
   |    ^^^^^^^                           ----------------------------

For more information about this error, try `rustc --explain E0308`.
error: could not compile `rust_proj` (bin "rust_proj") due to 1 previous error

```

On change donc le type de la variable borrowed_string: 
```rust
let mut party_foul = String::from("Using memory unsafe languages is a: "); // Is this variable changeable?
    decrypt(encrypted_buffer, &mut party_foul);
```

Le build fonctionne. On run : 

```bash
 cargo run
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.03s
     Running `target/debug/rust_proj`
Using memory unsafe languages is a: PARTY FOUL! Here is your flag: picoCTF{4r3_y0u_h4v1n5_fun_y31?}
```
