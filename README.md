# POO_AMF_2025-02

## Conversão de um String para Inteiro

```bash
import java.util.Scanner;

public class LeituraInteiro {  // CUIDADO COM O NOME DO SEU PROJETO 
    public static void main(String[] args) {
        Scanner entrada = new Scanner(System.in);

        System.out.print("Digite um número inteiro: ");
        String texto = entrada.nextLine(); // lê como String
        int x = Integer.parseInt(texto);   // converte para int

        System.out.println("Você digitou o número: " + x);
        entrada.close();
    }
}

```

## Conversão de String para número real (double)
```bash
import java.util.Scanner;

public class LeituraDouble {
    public static void main(String[] args) {
        Scanner entrada = new Scanner(System.in);

        System.out.print("Digite um número real: ");
        String texto = entrada.nextLine();     // lê como String
        double x = Double.parseDouble(texto);  // converte para double

        System.out.printf("Você digitou: %.2f%n", x);

        entrada.close();
    }
}
```

## Exemplo Completo
```bash
public class FormatDemo {
    public static void main(String[] args) {
        int n = 255;
        double pi = 3.14159;
        String nome = "Leonam";
        boolean ativo = true;

        System.out.printf("Decimal: %d%n", n);
        System.out.printf("Octal: %o%n", n);
        System.out.printf("Hex: %x%n", n);
        System.out.printf("Hex (maiúsculo): %X%n", n);

        System.out.printf("PI normal: %f%n", pi);
        System.out.printf("PI com 2 casas: %.2f%n", pi);
        System.out.printf("PI científica: %e%n", pi);

        System.out.printf("Nome: %s%n", nome);
        System.out.printf("Ativo: %b%n", ativo);

        System.out.printf("Com largura 5: %5d%n", 42);
        System.out.printf("Zeros à esquerda: %05d%n", 42);
        System.out.printf("Alinhado à esquerda: %-5dFIM%n", 42);
    }
}


```
