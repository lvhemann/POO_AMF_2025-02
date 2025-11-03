# POO_AMF_2025-02
## Lista de exercício

1) Crie a classe Imovel, que possui um endereço e um preço.

a. crie uma classe Novo, que herda Imovel e possui um adicional no preço. Crie métodos de
acesso e impressão deste valor adicional.

b. crie uma classe Velho, que herda Imovel e possui um desconto no preço. Crie métodos de
acesso e impressão para este desconto.

2) Crie uma classe para representar uma conta corrente, com métodos para depositar uma quantia, sacar
uma quantia e obter o saldo. Para cada saque será debitada também uma taxa de operação equivalente à
0,5% do valor sacado. Crie, em seguida, uma subclasse desta classe anterior para representar uma conta
corrente de um cliente especial. Clientes especiais pagam taxas de operação de apenas 0,1% do valor
sacado. Faça testes com as duas classes e verifique seus resultados.

3) Implemente uma classe Ingresso com os atributos evento:String e valorBase:double, métodos de acesso, valorFinal() e exibeDados() (mostra evento, base e final).
Crie duas subclasses:
Vip com adicional:double → sobrescreva valorFinal() para valorBase + adicional e exibeDados().
Estudante com desconto:double → sobrescreva valorFinal() para max(0, valorBase − desconto) e exibeDados().

4) Implemente a classe Produto com nome:String e precoBase:double, métodos de acesso, precoFinal() e exibeDados() (mostra nome, base e final).
Crie duas subclasses:

ProdutoNacional com impostoPercent:double → sobrescreva precoFinal() para precoBase * (1 + impostoPercent/100) e exibeDados().

ProdutoImportado com impostoPercent:double e taxaDesembaraco:double → precoFinal() = precoBase * (1 + impostoPercent/100) + taxaDesembaraco; sobrescreva exibeDados().
