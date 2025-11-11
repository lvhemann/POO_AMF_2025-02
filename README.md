# POO_AMF_2025-02

## Aula sobre interfaces

```bash
// ===== Interfaces =====
interface Nadador {
    void nadar();
}

interface Voador {
    void voar();
}

// ===== Implementação concreta =====
class Pato implements Nadador, Voador {

    @Override
    public void nadar() {
        System.out.println("O pato está nadando no lago.");
    }

    @Override
    public void voar() {
        System.out.println("O pato está voando sobre a água.");
    }
}

// ===== Classe principal para teste =====
public class Main {
    public static void main(String[] args) {
        Pato p = new Pato();
        p.nadar();
        p.voar();
    }
}
```

## Aula sobre classes abstratas

```bash
abstract class Animal {
    String nome;
    void dormir() {
        System.out.println(nome + " está dormindo...");
    }
    abstract void emitirSom(); // deve ser implementado
}

lass Cachorro extends Animal {
    @Override
    void emitirSom() {
        System.out.println("Au");}}

class Gato extends Animal {
    @Override
    void emitirSom() {
        System.out.println("Miau!");}}

class Vaca extends Animal {
    @Override
    void emitirSom() {
        System.out.println("Muuuu!"); }}

public class Main {
    public static void main(String[] args) {

        // Criando cada objeto com new e definindo o nome
        Cachorro cachorro = new Cachorro();
        cachorro.nome = "Rex";

        Gato gato = new Gato();
        gato.nome = "Mimi";

        Vaca vaca = new Vaca();
        vaca.nome = "Mimosa";



        // Cada animal faz seu som
        cachorro.emitirSom();
        gato.emitirSom();
        vaca.emitirSom();
        galinha.emitirSom();
        leao.emitirSom();
        cobra.emitirSom();
}

```



