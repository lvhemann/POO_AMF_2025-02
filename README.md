# POO_AMF_2025-02
## Lista de exercício

Enredo:
Um mercado deseja registrar produtos para calcular o valor total da compra.
Cada produto possui um nome, um preço unitário e uma quantidade comprada.
O sistema deve mostrar o valor total gasto com esse produto.

1) Passo

Resuma o que o programa precisa fazer, com suas palavras:
* Exemplo de resposta esperada:
“O sistema deve armazenar os dados de um produto (nome, preço e quantidade) e calcular o valor total (preço × quantidade).”

2) Planejar a classe

Escreva:
Nome da classe: __________
Atributos: __________
Métodos: __________

Exemplo de resposta esperada:
Classe: Produto
Atributos: nome, preco, quantidade
Métodos: calcularTotal(), exibirInfo()

# Estrutura do Código

```bash
class Produto {
    String nome;
    double preco;
    int quantidade;

    void calcularTotal() {
        // implementar
    }

    void exibirInfo() {
        // implementar
    }
}

```

```bash
class Produto {
    String nome;
    double preco;
    int quantidade;

    void calcularTotal() {
        double total = preco * quantidade;
        System.out.println("Total gasto: R$" + total);
    }

    void exibirInfo() {
        System.out.println("Produto: " + nome + " | Preço: R$" + preco + " | Quantidade: " + quantidade);
    }
}

```
```bash
public class Mercado {
    public static void main(String[] args) {
        Produto p1 = new Produto();
        p1.nome = "Arroz";
        p1.preco = 5.50;
        p1.quantidade = 3;

        p1.exibirInfo();
        p1.calcularTotal();

        System.out.println();

        Produto p2 = new Produto();
        p2.nome = "Leite";
        p2.preco = 4.00;
        p2.quantidade = 2;

        p2.exibirInfo();
        p2.calcularTotal();
    }
}
```

## Exercícios para serem entregues

O que deve ser entregue
Resumo do problema (explicação com suas palavras).
Planejamento da classe (nome, atributos, métodos).
Código da classe (com métodos implementados).
Programa principal testando pelo menos 2 objetos diferentes.


1) Um pet shop deseja cadastrar cães para banho e tosa.
Cada cachorro tem um nome, uma raça e uma idade.
O sistema deve permitir cadastrar o cachorro e depois mostrar suas informações.


2) Uma garagem precisa registrar os carros que chegam.
Cada carro tem uma marca, um modelo e um ano.
O sistema deve mostrar as informações do carro registrado.

3) Um mercado deseja calcular o valor total de um produto comprado em certa quantidade.
Cada produto possui um nome, um preço unitário e uma quantidade.
O sistema deve calcular e exibir o valor total da compra.

4) Uma escola deseja registrar os alunos e calcular suas médias.
Cada aluno tem um nome e duas notas.
O sistema deve calcular a média e informar se o aluno está aprovado (média ≥ 7) ou reprovado.

5) Um banco precisa controlar contas.
Cada conta tem um número e um saldo.
O sistema deve permitir depositar e sacar valores, mostrando o saldo atualizado após cada operação.

6) Um jogo precisa criar personagens que têm nome e pontos de vida (começam em 100).
O personagem pode sofrer dano, perdendo vida, ou se curar, recuperando pontos de vida.
O sistema deve mostrar o status do personagem após cada ação.

7) Um banco deseja controlar suas contas.
Toda conta tem um número e um saldo.
Existem dois tipos de conta:
Conta Corrente, que tem também uma taxa de saque.
Conta Poupança, que pode render juros.
O sistema deve permitir criar contas, realizar depósitos, saques e rendimentos.

8) Uma empresa deseja registrar seus funcionários.
Todo funcionário possui um nome e um salário base.
Existem dois tipos de funcionários:
O Gerente, que tem também um setor.
O Vendedor, que tem também um valor de comissão.
O sistema deve permitir cadastrar gerentes e vendedores e exibir suas informações.
