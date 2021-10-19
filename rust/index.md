# Cargo

Cargo is a package manager, the build system, test runner and doc generator.

Comando que gera a estrutura de um projeto no diretório atual.
cargo new projeto
    Created binary (application) `hello` package

O resultado do comando será a estrutura:
projeto
|_Cargo.toml (config file)
|__src
|______main.rs

## cargo.toml

[package]
name = "projeto" // Nome do package, independente do nome do diretório
version = "0.1.0"
authors = ["Bruno Barcellos <bbarcellosf@gmail.com>"]
edition = "2018"

[dependecies]

## rust

Rust é uma linguagem fortemente tipada, se um valor puder ter seu tipo identificado, a linguuagem não cobra a necessidade de anotação de tipo.

let foo = 2;
let foo: i32 = 2;

i32 = integer 32 bits

The let statement can destructure the data on the right hand side and use it.

let (x, y) = (0, 100);

Varáveis são imutáveis por padrão. Garante safety, concurrence and speed.

Varável mutável
let mut x = 2;

## Constantes

Utiliza palavra reservada const ao invés de let
Utiliza o padrão de nomenclatura screaming snake case WARP_FACTOR
A anotação de tipagem é obrigatória
É obrigatório que o valor seja uma expressão constante.

## Escopo

O escopo de uma variável começa onde ela é declarada e se extende até o fim do bloco. Um bloco é uma coleção de statements dentro de chaves. Não existe garbage collector, as variáveis são automaticamente destruídas quando seu escopo acaba.

fn main() {
    let x = 5;
    {
        let y = 99;
        println!("{}, {}", x, y); // Funciona
    }
    println!("{}, {}", x, y); // Erro, pois y não existe mais.
}

## Shadow

fn main() {
    let x = 5;
    {
        let x = 99;
        println!("{}", x); // 99
    }
    println!("{}", x); // 5
}

Outras formas de shadow incluem

let mut x = 5; // x é mutável.
let x = x; // x se torna imutável.

let x = "texto";
let x = make_image(x);

## Memory safety

Rust garante memoru safety forçando que uma variável obrigatoriamente seja inicializada antes de ser utilizada. Do contrário, um erro será lançado em tempo de compilação.

let x: i32;
if true {
    x = 2;
}

Mesmo que a condição lógica seja sempre verdadeira, validações de condições acontecem em tempo de execução. Assim, o compilador não consegue garantir que a variável será inicializada.

if true {
    x = 2;
} else {
    x = 4;
}

Neste caso, o compilador consegue garantir que a variável será inicializada independente da validação da condição lógica testada.

rustc é o compilador que cargo utiliza por debaixo dos panos.

[The Manifest Format](https://doc.rust-lang.org/cargo/reference/manifest.html)
