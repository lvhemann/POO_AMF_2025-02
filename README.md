<img width="961" height="193" alt="image" src="https://github.com/user-attachments/assets/0b04480d-3dbc-4785-9735-e2c9c999d31f" /># POO_AMF_2025-02

## Exemplo do carro
```bash
// Definição da classe Carro (o molde ou receita)
static class Carro {
    
    // === ATRIBUTOS (características de cada carro) ===
    String marca;   // Marca do carro (ex.: Volkswagen, Honda, Ferrari)
    String modelo;  // Modelo do carro (ex.: Fusca, Civic, F8)
    int ano;        // Ano de fabricação do carro

    // === MÉTODOS (ações que o carro pode realizar) ===

    // Método para ligar o carro
    void ligar() {
        System.out.println(marca + " " + modelo + " está ligado!");
    }

    // Método para acelerar o carro
    void acelerar() {
        System.out.println(marca + " " + modelo + " está acelerando!");
    }
}

```

## Como usar no código
```bash
// Classe principal (onde o programa começa)
public class Main {
    public static void main(String[] args) {
        // Criando o primeiro objeto (carro1)
        Carro carro1 = new Carro();  // "new Carro()" cria um novo objeto da classe Carro
        carro1.marca = "Volkswagen";
        carro1.modelo = "Fusca";
        carro1.ano = 1980;

        // Criando o segundo objeto (carro2)
        Carro carro2 = new Carro();
        carro2.marca = "Honda";
        carro2.modelo = "Civic";
        carro2.ano = 2020;

        // Criando o terceiro objeto (carro3)
        Carro carro3 = new Carro();
        carro3.marca = "Ferrari";
        carro3.modelo = "F8";
        carro3.ano = 2022;

        // Chamando métodos nos objetos
        carro1.ligar();
        carro2.acelerar();
        carro3.ligar();
        carro3.acelerar();
    }
}
```
# Exemplo

## Estacionamento (Classe e dois método)
```bash
static class Carro {
    String placa;
    String modelo;
    String cor;
    boolean estacionado; // controla se o carro está ou não estacionado

    void estacionar() {
        if (!estacionado) {
            estacionado = true;
            System.out.println("Carro " + placa + " estacionou.");
        } else {
            System.out.println("Carro " + placa + " já estava estacionado.");
        }
    }

    void sair() {
        if (estacionado) {
            estacionado = false;
            System.out.println("Carro " + placa + " saiu.");
        } else {
            System.out.println("Carro " + placa + " já estava fora.");
        }
    }
}

```

## Objeto 
```bash
public class Main {
    public static void main(String[] args) {
        // Criando o objeto
        Carro c1 = new Carro();
        c1.placa = "XYZ-9876";
        c1.modelo = "Onix";
        c1.cor = "Branco";
        c1.estacionado = false; // começa fora

        c1.estacionar();
        c1.sair();
        c1.sair(); // tentativa de sair novamente
    }
}

```
