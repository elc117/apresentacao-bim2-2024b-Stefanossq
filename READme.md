# 🏁 **Animal Thread Race** 🐇🐢🐐
### **Threads e Herança em Java**

---

## **📖 Problema**  
**Resolver a Prática da Aula 21:**  
> Crie um novo programa, **BetterThreadRace.java**, contendo uma **classe base abstrata (`AnimalRunner`)** da qual serão derivadas três classes de animais. Faça as modificações necessárias para que o novo programa funcione como o original, mas com um código mais estruturado e reutilizável.

---

## **💡 Solução**  
 

### **Como resolver o problema?**
1. Criar a **superclasse** `AnimalRunner`,que tem o comportamento comum de todos animais.  

2. Cada animal (`Rabbit`, `Turtle`, `Goat`) implementados como uma **subclasse de `AnimalRunner`**, reutilizando o código da superclasse e personalizando apenas o método `runLikeAnimal()`.

3. A classe principal, **BetterThreadRace**, cria as threads para os animais e inicia a corrida.

---

## **🛠️ Estrutura do Código**

 *1* Utilizar herança e threads para simular a corrida de três animais: Coelho (Rabbit), Tartaruga (Turtle) e Bode (Goat).  
 
   
   *2* Cada animal herda a classe base `AnimalRunner`, que define o comportamento comum a todos os animais. 
   
   *3*  Método `runLikeAnimal()` define o comportamento específico de cada animal durante a corrida.

A estrutura do código é organizada da seguinte forma:

1. **Classe Base: `AnimalRunner`**: define a estrutura básica para todos os animais, como o início da corrida e o controle da execução. O método `run()` controla a corrida e chama o método abstrato `runLikeAnimal()`, que será implementado nas subclasses.
2. **Subclasses (`Rabbit`, `Turtle`, `Goat`)**: Cada uma dessas classes herda de `AnimalRunner` e implementa o comportamento específico de como o animal se comporta na corrida.
3. **Classe Principal: `BetterThreadRace`**: A classe principal gerencia a execução das threads. Ela cria instâncias dos animais e inicia a execução das threads para simular a corrida.

---

### 📜 **Código**

```java
abstract class AnimalRunner extends Thread {
    protected String name;

    public AnimalRunner(String name) {
        this.name = name;
    }

    @Override
    public void run() {
        System.out.println(name + " is at the start of the race!");
        for (int pos = 10; pos > 0; pos--) {
            runLikeAnimal();
            System.out.println(name + " is at position " + pos);
        }
        System.out.println(name + " finished the race!");
    }

    protected abstract void runLikeAnimal();
}

class Rabbit extends AnimalRunner {
    public Rabbit(String name) {
        super(name);
    }

    @Override
    protected void runLikeAnimal() {
        System.out.println(name + " is running fast");
    }
}

class Turtle extends AnimalRunner {
    public Turtle(String name) {
        super(name);
    }

    @Override
    protected void runLikeAnimal() {
        System.out.println(name + " is running slow");
    }
}

class Goat extends AnimalRunner {
    public Goat(String name) {
        super(name);
    }

    @Override
    protected void runLikeAnimal() {
        System.out.println(name + " aaaaa");
    }
}

public class BetterThreadRace {
    public static void main(String[] args) {
        AnimalRunner rabbit = new Rabbit("Snowball");
        AnimalRunner turtle = new Turtle("Donatello");
        AnimalRunner goat = new Goat("goat");

        rabbit.start();
        turtle.start();
        goat.start();
    }
}


