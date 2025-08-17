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

