# POO_AMF_2025-02

## Aula sobre interfaces

```bash
// ===== Interfaces =====
interface Nadador {
    void nadar();
}

interface Voador {
    void voar();
}

// ===== Implementação concreta =====
class Pato implements Nadador, Voador {

    @Override
    public void nadar() {
        System.out.println("O pato está nadando no lago.");
    }

    @Override
    public void voar() {
        System.out.println("O pato está voando sobre a água.");
    }
}

// ===== Classe principal para teste =====
public class Main {
    public static void main(String[] args) {
        Pato p = new Pato();
        p.nadar();
        p.voar();
    }
}
```

