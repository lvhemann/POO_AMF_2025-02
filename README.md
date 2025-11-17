
##  SRP – Responsabilidade única

```bash
class ProcessadorPagamento {
    public void processar(double valor) {
        System.out.println("Processando pagamento de R$ " + valor);
    }
}
class GeradorRecibo {
    public void gerar(double valor) {
        System.out.println("Recibo: pagamento de R$ " + valor);
    }
}
class EmailService {
    public void enviar(String email) {
        System.out.println("Enviando recibo para " + email);
    }
}
```


```bash
class PagamentoController {
    private ProcessadorPagamento processador = new ProcessadorPagamento();
    private GeradorRecibo recibo = new GeradorRecibo();
    private EmailService email = new EmailService();

    public void pagar(double valor, String emailCliente) {
        processador.processar(valor);
        recibo.gerar(valor);
        email.enviar(emailCliente);
    }
}
```

```bash
public class Main {
    public static void main(String[] args) {
        PagamentoController controller = new PagamentoController();

        controller.pagar(250.00, "cliente@email.com");
    }
}
```

## OCP - Aberto/Fechado
```bash
public interface Desconto {
    double aplicar(double valor);
}
```

```bash
public class DescontoPromocional implements Desconto {

    @Override
    public double aplicar(double valor) {
        return valor * 0.90; // 10% de desconto
    }
}

public class DescontoFidelidade implements Desconto {

    @Override
    public double aplicar(double valor) {
        return valor * 0.85; // 15% de desconto
    }
}

public class DescontoSazonal implements Desconto {

    @Override
    public double aplicar(double valor) {
        return valor * 0.80; // 20% de desconto
    }
}

public class CalculadoraDesconto {

    public double calcular(double valor, Desconto desconto) {
        return desconto.aplicar(valor);
    }
}
```

```bash

public class Main {

    public static void main(String[] args) {

        CalculadoraDesconto calc = new CalculadoraDesconto();

        double valorBase = 100.0;

        System.out.println("Valor base: R$ " + valorBase);

        double valorPromo = calc.calcular(valorBase, new DescontoPromocional());
        System.out.println("Desconto Promocional (10%): R$ " + valorPromo);

        double valorFidelidade = calc.calcular(valorBase, new DescontoFidelidade());
        System.out.println("Desconto Fidelidade (15%): R$ " + valorFidelidade);

        double valorSazonal = calc.calcular(valorBase, new DescontoSazonal());
        System.out.println("Desconto Sazonal (20%): R$ " + valorSazonal);
    }
}
```

## Substituição

```bash
public interface VeiculoMovel {
    void acelerar();
}
```

```bash
public class Carro implements VeiculoMovel {

    @Override
    public void acelerar() {
        System.out.println("O carro está acelerando com motor a combustão...");
    }
}

public class Bicicleta implements VeiculoMovel {

    @Override
    public void acelerar() {
        System.out.println("A bicicleta está ganhando velocidade com pedalada...");
    }
}

public class CarroEletrico implements VeiculoMovel {

    @Override
    public void acelerar() {
        System.out.println("O carro elétrico está acelerando silenciosamente...");
    }
}
```

```bash
public class Main {

    public static void main(String[] args) {

        VeiculoMovel carro = new Carro();
        VeiculoMovel bicicleta = new Bicicleta();
        VeiculoMovel carroEletrico = new CarroEletrico();

        testarAceleracao(carro);
        testarAceleracao(bicicleta);
        testarAceleracao(carroEletrico);
    }

    public static void testarAceleracao(VeiculoMovel veiculo) {
        veiculo.acelerar();
    }
}

```


## Princípio da Segregação de Interfaces 

```bash
public interface Impressora {
    void imprimir(String documento);
}

public interface Scanner {
    void escanear(String documento);
}
```

```bash
public class ImpressoraSimples implements Impressora {

    @Override
    public void imprimir(String documento) {
        System.out.println("Imprimindo documento: " + documento);
    }
}

public class ScannerSimples implements Scanner {

    @Override
    public void escanear(String documento) {
        System.out.println("Escaneando documento: " + documento);
    }
}

```

```bash
public class DispositivoMultifuncional implements Impressora, Scanner {

    @Override
    public void imprimir(String documento) {
        System.out.println("[Multifuncional] Imprimindo: " + documento);
    }

    @Override
    public void escanear(String documento) {
        System.out.println("[Multifuncional] Escaneando: " + documento);
    }
}
```

```bash
package dispositivos;

public class Main {

    public static void main(String[] args) {

        Impressora impSimples = new ImpressoraSimples();
        Scanner scannerSimples = new ScannerSimples();
        DispositivoMultifuncional multi = new DispositivoMultifuncional();

        System.out.println("=== Dispositivos Simples ===");
        impSimples.imprimir("Contrato de Locação");
        scannerSimples.escanear("Documento de Identidade");

        System.out.println("\n=== Dispositivo Multifuncional ===");
        multi.imprimir("Relatório de Vendas");
        multi.escanear("Comprovante de Pagamento");
    }
}


```



## Princípio da Inversão de Dependência - DIP 


```bash
public interface ProcessadorPagamento {
    void processar();
}

```

```bash
public class ProcessadorDePagamentoComCartao implements ProcessadorPagamento {

    @Override
    public void processar() {
        System.out.println("Processando pagamento com CARTÃO de crédito...");
    }
}

public class ProcessadorDePagamentoComPix implements ProcessadorPagamento {

    @Override
    public void processar() {
        System.out.println("Processando pagamento via PIX...");
    }
}

```

```bash
public class Pedido {

    private ProcessadorPagamento processador;

    public Pedido(ProcessadorPagamento processador) {
        this.processador = processador;
    }

    public void finalizar() {
        System.out.println("Finalizando pedido...");
        processador.processar();
        System.out.println("Pedido finalizado com sucesso!\n");
    }
}

```

```bash
public class Main {

    public static void main(String[] args) {

        // Pedido pago com CARTÃO
        ProcessadorPagamento procCartao = new ProcessadorDePagamentoComCartao();
        Pedido pedidoCartao = new Pedido(procCartao);
        pedidoCartao.finalizar();

        // Pedido pago com PIX
        ProcessadorPagamento procPix = new ProcessadorDePagamentoComPix();
        Pedido pedidoPix = new Pedido(procPix);
        pedidoPix.finalizar();
    }
}
```


## Exercícios
1. SRP — Single Responsibility Principle
Crie uma classe User que viole o princípio SRP, contendo múltiplas responsabilidades (ex.: cadastro (nome, email e senha), login, validação etc.).
Estruture o código separando as responsabilidades em classes diferentes, de forma que cada classe tenha apenas um motivo para mudar.


2. Implemente uma classe PaymentProcessor que siga o princípio OCP.
Ela deve aceitar diferentes tipos de pagamento (ex.: Cartão, Pix, Boleto, Carteira Digital), sem exigir alterações na classe principal quando um novo método de pagamento for criado.
Use interfaces ou classes abstratas para permitir que novas formas de pagamento sejam adicionadas apenas criando novas classes.

3. Crie uma hierarquia de classes de veículos, onde Veiculo seja a classe base.
As classes derivadas (como Carro, Moto, Caminhao) devem obedecer ao princípio LSP: qualquer tipo de veículo deve poder substituir um Veiculo sem alterar o comportamento esperado no código cliente.


4. Desenvolva uma interface inicial para um sistema de controle de acesso (por exemplo, contendo métodos como login, logout, consultarRegistros, gerarRelatorios, etc.).
Em seguida, divida essa interface grande em interfaces menores, mais específicas, garantindo que as classes concretas implementem apenas métodos que realmente utilizam.


5. Crie uma classe Car que inicialmente depende diretamente de um tipo específico de Engine (por exemplo, CombustionEngine).Mostre como isso viola o DIP.
Depois, reestruture o código para que Car dependa de uma abstração (Engine), permitindo que diferentes tipos de motores (combustão, elétrico, híbrido etc.) possam ser utilizados sem modificar a classe Car.






