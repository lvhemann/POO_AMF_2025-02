# POO_AMF_2025-02

## Conversão de um String para Inteiro

```bash
// ================= SUPERCLASSE =================
class Pokemon {             // <<Superclasse>>
    String nome;            // <<Atributo>>
    String tipo;            // <<Atributo>>

    void atacar() {         // <<Método>>
        System.out.println(nome + " atacou!");
    }

    void defender() {       // <<Método>>
        System.out.println(nome + " defendeu!");
    }
}

// ================= SUBCLASSES ==================
class Electric extends Pokemon {   // <<Subclasse>>
    void choque() {                // <<Método específico>>
        System.out.println(nome + " usou Choque do Trovão!");
    }
}

class Fire extends Pokemon {       // <<Subclasse>>
    void fogo() {                  // <<Método específico>>
        System.out.println(nome + " usou Lança-Chamas!");
    }
}

class Water extends Pokemon {      // <<Subclasse>>
    void agua() {                  // <<Método específico>>
        System.out.println(nome + " usou Jato d’Água!");
    }
}

class Grass extends Pokemon {      // <<Subclasse>>
    void raiz() {                  // <<Método específico>>
        System.out.println(nome + " usou Chicote de Vinha!");
    }
}

// ================= OBJETOS =====================
public class Main {
    public static void main(String[] args) {
        Electric pikachu = new Electric();   // <<Objeto>>
        pikachu.nome = "Pikachu";
        pikachu.tipo = "Elétrico";
        pikachu.choque();  // chama método da subclasse

        Fire charmander = new Fire();        // <<Objeto>>
        charmander.nome = "Charmander";
        charmander.tipo = "Fogo";
        charmander.fogo();  // chama método da subclasse
    }
}


```
