# POO_AMF_2025-02

## Getters e Setters

```bash
public class Pessoa {
private String nome; // detalhe interno
private int idade; // detalhe interno
private boolean ativo = true;


public Pessoa(String nome, int idade) { // construtor
setNome(nome); // reutiliza validação do setter
setIdade(idade);
}


public String getNome() { return nome; }
public void setNome(String nome) {
if (nome == null || nome.isBlank()) throw new IllegalArgumentException("nome vazio");
this.nome = nome.trim();
}


public int getIdade() { return idade; }
public void setIdade(int idade) {
if (idade < 0 || idade > 130) throw new IllegalArgumentException("idade inválida");
this.idade = idade;
}


public boolean isAtivo() { return ativo; }
public void setAtivo(boolean ativo) { this.ativo = ativo; }
}
```
## Getter e Setter

```bash
public class Pessoa {
    // ===== Atributos privados =====
    private String nome;
    private int idade;
    private boolean ativo;

    // ===== Construtor =====
    public Pessoa(String nome, int idade, boolean ativo) {
        this.nome = nome;
        this.idade = idade;
        this.ativo = ativo;
    }

    // ===== Getters e Setters =====
    
    // String → getNome / setNome
    public String getNome() {
        return nome;
    }

    public void setNome(String nome) {
        this.nome = nome;
    }

    // int → getIdade / setIdade
    public int getIdade() {
        return idade;
    }

    public void setIdade(int idade) {
        if (idade < 0) {
            throw new IllegalArgumentException("Idade não pode ser negativa");
        }
        this.idade = idade;
    }

    // boolean → isAtivo / setAtivo
    public boolean isAtivo() {
        return ativo;
    }

    public void setAtivo(boolean ativo) {
        this.ativo = ativo;
    }
}


```

```bash
public class Main {
    public static void main(String[] args) {
        Pessoa p = new Pessoa("Maria", 20, true);

        // Usando getters
        System.out.println("Nome: " + p.getNome());
        System.out.println("Idade: " + p.getIdade());
        System.out.println("Ativo: " + p.isAtivo());

        // Usando setters
        p.setNome("João");
        p.setIdade(25);
        p.setAtivo(false);

        System.out.println("Novo nome: " + p.getNome());
        System.out.println("Nova idade: " + p.getIdade());
        System.out.println("Ativo? " + p.isAtivo());
    }
}


```


## Exemplo de Public, private e protected
```bash
// Classe base
public class Pessoa {
    // Atributo privado: só pode ser acessado dentro da própria classe
    private String cpf;

    // Atributo protegido: pode ser acessado por subclasses ou no mesmo pacote
    protected String nome;

    // Atributo público: acessível de qualquer lugar
    public int idade;

    // Construtor
    public Pessoa(String cpf, String nome, int idade) {
        this.cpf = cpf;
        this.nome = nome;
        this.idade = idade;
    }

    // Getter público para acessar o cpf (já que é private)
    public String getCpf() {
        return cpf;
    }

    // Método público
    public void apresentar() {
        System.out.println("Nome: " + nome + ", Idade: " + idade);
    }
}

// Classe filha (subclasse)
class Aluno extends Pessoa {
    private String matricula;

    public Aluno(String cpf, String nome, int idade, String matricula) {
        super(cpf, nome, idade);
        this.matricula = matricula;
    }

    public void mostrarDadosAluno() {
        // cpf é PRIVATE → não pode acessar diretamente
        // System.out.println(cpf); // ERRO

        // nome é PROTECTED → pode acessar aqui
        System.out.println("Nome do aluno: " + nome);

        // idade é PUBLIC → pode acessar de qualquer lugar
        System.out.println("Idade do aluno: " + idade);

        // Para cpf, usa o getter público
        System.out.println("CPF do aluno: " + getCpf());

        System.out.println("Matrícula: " + matricula);
    }
}

// Classe principal
public class Main {
    public static void main(String[] args) {
        Aluno a = new Aluno("123.456.789-00", "Maria", 20, "2025A01");

        // Acessando métodos públicos
        a.apresentar();
        a.mostrarDadosAluno();

        // Atributo público → acessível diretamente
        a.idade = 21;

        // Atributo protegido → não acessível aqui (fora da subclasse/pacote)
        // a.nome = "João"; // ERRO se estiver em outro pacote

        // Atributo privado → nunca acessível diretamente
        // a.cpf = "000.000.000-00"; // ERRO

        System.out.println("CPF (via getter): " + a.getCpf());
    }
}



```
