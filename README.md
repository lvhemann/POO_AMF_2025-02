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

## ExemploPagamentos

```bash
// Classe abstrata
abstract class Pagamento {
    protected double valor;

    public Pagamento(double valor) {
        this.valor = valor;
    }

    public void emitirRecibo() {
        System.out.println("Recibo emitido para o valor de R$ " + String.format("%.2f", valor));
    }

    // Método abstrato
    abstract void realizarPagamento();
}

// ===== Implementações =====
class Pix extends Pagamento {
    public Pix(double valor) { super(valor); }

    @Override
    void realizarPagamento() {
        System.out.println("Pagamento de R$ " + String.format("%.2f", valor) + " via PIX.");
    }
}

class Dinheiro extends Pagamento {
    public Dinheiro(double valor) { super(valor); }

    @Override
    void realizarPagamento() {
        System.out.println("Pagamento de R$ " + String.format("%.2f", valor) + " em dinheiro.");
    }
}

// >>> Cartão de Crédito com número de vezes (parcelas)
class CartaoCredito extends Pagamento {
    private final int parcelas; // número de vezes

    public CartaoCredito(double valor, int parcelas) {
        super(valor);
        if (parcelas < 1) throw new IllegalArgumentException("Parcelas deve ser >= 1");
        this.parcelas = parcelas;
    }

    public int getParcelas() { return parcelas; }

    public double getValorParcela() {
        // sem juros, apenas divisão simples
        return valor / parcelas;
    }

    @Override
    void realizarPagamento() {
        if (parcelas == 1) {
            System.out.println("Pagamento no Cartão de Crédito à vista: R$ "
                + String.format("%.2f", valor));
        } else {
            System.out.println("Pagamento no Cartão de Crédito em " + parcelas + "x de R$ "
                + String.format("%.2f", getValorParcela()) + " (total R$ "
                + String.format("%.2f", valor) + ").");
        }
    }
}

// ===== Main de demonstração =====
public class Main {
    public static void main(String[] args) {
        Pagamento p1 = new Pix(150.00);
        Pagamento p2 = new CartaoCredito(300.00, 1);   // crédito à vista
        Pagamento p3 = new CartaoCredito(1200.00, 6);  // crédito parcelado em 6x
        Pagamento p4 = new Dinheiro(50.00);

        p1.realizarPagamento();
        p2.realizarPagamento();
        p3.realizarPagamento();
        p4.realizarPagamento();

        // Exemplo de uso de métodos específicos
        if (p3 instanceof CartaoCredito cc) {
            System.out.println("Cada parcela: R$ " + String.format("%.2f", cc.getValorParcela()));
        }

        // Recibo (método concreto da abstrata)
        p3.emitirRecibo();
    }
}


```


