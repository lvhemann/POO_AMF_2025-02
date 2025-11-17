
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
