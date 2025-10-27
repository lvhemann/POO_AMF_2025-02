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

## Exemplo Pokemon
```bash
// ===== Classe base =====
class Pokemon {
    protected String nome;
    protected String tipo;
    protected int hp;
    protected String habilidade1;
    protected String habilidade2;
    protected String habilidade3;
    protected String habilidade4;

    public Pokemon(String nome, String tipo, int hp,
                   String habilidade1, String habilidade2, String habilidade3, String habilidade4) {
        this.nome = nome;
        this.tipo = tipo;
        this.hp = hp;
        this.habilidade1 = habilidade1;
        this.habilidade2 = habilidade2;
        this.habilidade3 = habilidade3;
        this.habilidade4 = habilidade4;
    }

    // Métodos “1 a 4” genéricos (podem ser sobrescritos nas subclasses)
    public void usarHabilidade1() { System.out.println(nome + " usa " + habilidade1 + "!"); }
    public void usarHabilidade2() { System.out.println(nome + " usa " + habilidade2 + "!"); }
    public void usarHabilidade3() { System.out.println(nome + " usa " + habilidade3 + "!"); }
    public void usarHabilidade4() { System.out.println(nome + " usa " + habilidade4 + "!"); }

    // Útil se quiser escolher por número
    public void usarHabilidade(int slot) {
        switch (slot) {
            case 1: usarHabilidade1(); break;
            case 2: usarHabilidade2(); break;
            case 3: usarHabilidade3(); break;
            case 4: usarHabilidade4(); break;
            default: System.out.println(nome + " não tem habilidade " + slot + "."); 
        }
    }
}

// ===== Família Eevee =====
class Eevee extends Pokemon {
    public Eevee() {
        super(
            "Eevee", "Normal", 55,
            "Quick Attack", "Swift", "Bite", "Sand Attack"
        );
    }

    // Pode personalizar o “efeito visual” de cada slot se quiser
    public void usarHabilidade1() { System.out.println(nome + " avança veloz com " + habilidade1 + "!"); }
    public void usarHabilidade2() { System.out.println(nome + " lança estrelas com " + habilidade2 + "!"); }
    public void usarHabilidade3() { System.out.println(nome + " desfere uma mordida com " + habilidade3 + "!"); }
    public void usarHabilidade4() { System.out.println(nome + " reduz a precisão com " + habilidade4 + "!"); }
}

class Vaporeon extends Eevee {
    public Vaporeon() {
        super(); // chama o construtor da Eevee
        this.nome = "Vaporeon";
        this.tipo = "Água";
        this.hp = 130;
        // substitui o “moveset” nos 4 slots
        this.habilidade1 = "Water Pulse";
        this.habilidade2 = "Hydro Pump";
        this.habilidade3 = "Aqua Ring";
        this.habilidade4 = "Ice Beam";
    }

    public void usarHabilidade1() { System.out.println(nome + " emite ondas d’água com " + habilidade1 + "!"); }
    public void usarHabilidade2() { System.out.println(nome + " dispara um jato massivo com " + habilidade2 + "!"); }
    public void usarHabilidade3() { System.out.println(nome + " regenera-se com " + habilidade3 + "!"); }
    public void usarHabilidade4() { System.out.println(nome + " congela o alvo com " + habilidade4 + "!"); }
}

class Jolteon extends Eevee {
    public Jolteon() {
        super();
        this.nome = "Jolteon";
        this.tipo = "Elétrico";
        this.hp = 65;
        this.habilidade1 = "Thunder Shock";
        this.habilidade2 = "Thunderbolt";
        this.habilidade3 = "Pin Missile";
        this.habilidade4 = "Thunder";
    }

    public void usarHabilidade1() { System.out.println(nome + " aplica um choque com " + habilidade1 + "!"); }
    public void usarHabilidade2() { System.out.println(nome + " descarrega energia com " + habilidade2 + "!"); }
    public void usarHabilidade3() { System.out.println(nome + " dispara agulhas com " + habilidade3 + "!"); }
    public void usarHabilidade4() { System.out.println(nome + " invoca um raio com " + habilidade4 + "!"); }
}

class Flareon extends Eevee {
    public Flareon() {
        super();
        this.nome = "Flareon";
        this.tipo = "Fogo";
        this.hp = 65;
        this.habilidade1 = "Ember";
        this.habilidade2 = "Flame Charge";
        this.habilidade3 = "Flamethrower";
        this.habilidade4 = "Fire Blast";
    }

    public void usarHabilidade1() { System.out.println(nome + " lança brasas com " + habilidade1 + "!"); }
    public void usarHabilidade2() { System.out.println(nome + " acelera envolto em chamas com " + habilidade2 + "!"); }
    public void usarHabilidade3() { System.out.println(nome + " incinera com " + habilidade3 + "!"); }
    public void usarHabilidade4() { System.out.println(nome + " explode fogo devastador com " + habilidade4 + "!"); }
}

// ===== Família Gastly =====
class Gastly extends Pokemon {
    public Gastly() {
        super(
            "Gastly", "Fantasma/Veneno", 30,
            "Lick", "Night Shade", "Confuse Ray", "Mean Look"
        );
    }

    public void usarHabilidade1() { System.out.println(nome + " atinge com língua espectral: " + habilidade1 + "!"); }
    public void usarHabilidade2() { System.out.println(nome + " distorce a sombra com " + habilidade2 + "!"); }
    public void usarHabilidade3() { System.out.println(nome + " confunde o inimigo com " + habilidade3 + "!"); }
    public void usarHabilidade4() { System.out.println(nome + " impede a fuga com " + habilidade4 + "!"); }
}

class Haunter extends Gastly {
    public Haunter() {
        super();
        this.nome = "Haunter";
        this.hp = 45;
        this.habilidade1 = "Shadow Punch";
        this.habilidade2 = "Hex";
        this.habilidade3 = "Shadow Claw";
        this.habilidade4 = "Curse";
    }

    public void usarHabilidade1() { System.out.println(nome + " golpeia das sombras com " + habilidade1 + "!"); }
    public void usarHabilidade2() { System.out.println(nome + " amplifica aflições com " + habilidade2 + "!"); }
    public void usarHabilidade3() { System.out.println(nome + " rasga com " + habilidade3 + "!"); }
    public void usarHabilidade4() { System.out.println(nome + " lança uma maldição com " + habilidade4 + "!"); }
}

class Gengar extends Haunter {
    public Gengar() {
        super();
        this.nome = "Gengar";
        this.hp = 60;
        this.habilidade1 = "Shadow Ball";
        this.habilidade2 = "Dream Eater";
        this.habilidade3 = "Dark Pulse";
        this.habilidade4 = "Hypnosis";
    }

    public void usarHabilidade1() { System.out.println(nome + " libera esfera sombria: " + habilidade1 + "!"); }
    public void usarHabilidade2() { System.out.println(nome + " devora sonhos com " + habilidade2 + "!"); }
    public void usarHabilidade3() { System.out.println(nome + " emite pulso sombrio com " + habilidade3 + "!"); }
    public void usarHabilidade4() { System.out.println(nome + " coloca o alvo para dormir com " + habilidade4 + "!"); }
}

// ===== Programa principal (sem arrays) =====
public class Main {
    public static void main(String[] args) {
        // Eevee e evoluções
        Eevee eevee = new Eevee();
        eevee.usarHabilidade1();
        eevee.usarHabilidade2();
        Vaporeon vaporeon = new Vaporeon();
        vaporeon.usarHabilidade2();  // Hydro Pump
        Jolteon jolteon = new Jolteon();
        jolteon.usarHabilidade4();   // Thunder
        Flareon flareon = new Flareon();
        flareon.usarHabilidade3();   // Flamethrower

        System.out.println("-----");

        // Gastly, Haunter, Gengar
        Gastly gastly = new Gastly();
        gastly.usarHabilidade2();    // Night Shade
        Haunter haunter = new Haunter();
        haunter.usarHabilidade1();   // Shadow Punch
        Gengar gengar = new Gengar();
        gengar.usarHabilidade2();    // Dream Eater
    }
}


```
