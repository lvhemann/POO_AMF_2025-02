# POO_AMF_2025-02
# Aula 27/10

## Exemplo Carro e Motor
```bash
// Classe Motor
class Motor {
    private int id;
    private String modelo;

    // Construtor
    public Motor(int id, String modelo) {
        this.id = id;
        this.modelo = modelo;
    }

    // Getters
    public int getId() {
        return this.id;
    }

    public String getModelo() {
        return this.modelo;
    }
}

// Classe Carro (tem um Motor → composição)
class Carro {
    private int id;
    private String modelo;
    private Motor motor; // composição

    // Construtor
    public Carro(int id, String modelo, Motor motor) {
        this.id = id;
        this.modelo = modelo;
        this.motor = motor;
    }

    // Getters
    public int getId() {
        return this.id;
    }

    public String getModelo() {
        return this.modelo;
    }

    public Motor getMotor() {
        return this.motor;
    }
}

// Programa principal
public class Main {
    public static void main(String[] args) {
        Motor motor1 = new Motor(101, "V8 Turbo");
        Carro carro1 = new Carro(1, "Camaro", motor1);

        System.out.println("Carro ID: " + carro1.getId());
        System.out.println("Carro Modelo: " + carro1.getModelo());
        System.out.println("Motor ID: " + carro1.getMotor().getId());
        System.out.println("Motor Modelo: " + carro1.getMotor().getModelo());
    }
}


```

## Exemplo Composição Livro
```bash
// Classe Autor
class Autor {
    private int id;
    private String nome;
    private Livro livro;

    public Autor(int id, String nome) {
        this.id = id;
        this.nome = nome;
    }

    public void setLivro(Livro livro) {
        this.livro = livro;
    }

    public Livro getLivro() {
        return this.livro;
    }

    public String getNome() {
        return this.nome;
    }
}

// Classe Livro
class Livro {
    private int id;
    private String nome;
    private Autor autor;

    public Livro(int id, String nome, Autor autor) {
        this.id = id;
        this.nome = nome;
        this.autor = autor;
    }

    public Autor getAutor() {
        return this.autor;
    }

    public String getNome() {
        return this.nome;
    }
}

// Programa principal
public class Main {
    public static void main(String[] args) {
        Autor autor1 = new Autor(1, "José de Alencar");
        Livro livro1 = new Livro(101, "Iracema", autor1);

        // Associação explícita
        autor1.setLivro(livro1);

        System.out.println("Autor: " + autor1.getNome());
        System.out.println("Livro: " + autor1.getLivro().getNome());
    }
}


```

## Exemplo Celular

```bash
// Classe Bateria
class Bateria {
    // Atributo
    private int carga; // nível da bateria em %

    // Construtor
    public Bateria(int cargaInicial) {
        this.carga = Math.min(cargaInicial, 100); // garante máximo de 100%
    }

    // Métodos
    public void usar(int quantidade) {
        this.carga = Math.max(0, this.carga - quantidade); // nunca abaixo de 0
    }

    public void recarregar(int quantidade) {
        this.carga = Math.min(100, this.carga + quantidade); // nunca acima de 100
    }

    public int getCarga() {
        return this.carga;
    }

    public boolean temCarga() {
        return this.carga > 0;
    }
}

// Classe Tela
class Tela {
    // Atributo
    private boolean ligada;

    // Construtor
    public Tela() {
        this.ligada = false; // começa desligada
    }

    // Métodos
    public void ligar() {
        this.ligada = true;
        System.out.println("Tela ligada!");
    }

    public void desligar() {
        this.ligada = false;
        System.out.println("Tela desligada!");
    }

    public boolean isLigada() {
        return this.ligada;
    }
}

// Classe Celular (composição: TEM uma Bateria e TEM uma Tela)
class Celular {
    // Atributos
    private Bateria bateria;
    private Tela tela;
    private boolean ligado;

    // Construtor
    public Celular(int cargaInicial) {
        this.bateria = new Bateria(cargaInicial);
        this.tela = new Tela();
        this.ligado = false;
    }

    // Métodos
    public void ligar() {
        if (this.bateria.temCarga()) {
            this.ligado = true;
            this.tela.ligar();
            System.out.println("Celular ligado!");
        } else {
            System.out.println("Não é possível ligar. Bateria descarregada!");
        }
    }

    public void desligar() {
        this.ligado = false;
        this.tela.desligar();
        System.out.println("Celular desligado!");
    }

    public void usar() {
        if (this.ligado && this.bateria.temCarga()) {
            System.out.println("Usando o celular...");
            this.bateria.usar(20); // gasta 20% por uso
            System.out.println("Carga atual: " + this.bateria.getCarga() + "%");

            if (!this.bateria.temCarga()) {
                System.out.println("Bateria acabou! O celular desligou.");
                this.desligar();
            }
        } else if (!this.ligado) {
            System.out.println("Ligue o celular antes de usar.");
        } else {
            System.out.println("Bateria descarregada!");
        }
    }

    public void recarregar(int qtd) {
        this.bateria.recarregar(qtd);
        System.out.println("Recarregando... Bateria agora em " + this.bateria.getCarga() + "%");
    }
}

// Programa principal
public class Main {
    public static void main(String[] args) {
        Celular celular = new Celular(40); // começa com 40%

        celular.ligar();
        celular.usar();
        celular.usar();
        celular.usar(); // aqui a bateria acaba
        celular.ligar(); // não liga mais
        celular.recarregar(50);
        celular.ligar(); // agora liga de novo
    }
}


```
