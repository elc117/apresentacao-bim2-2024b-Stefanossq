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

2. Cada animal (`Rabbit`, `Turtle`, `Goat`) implementados como uma **subclasse de `AnimalRunner`**, reutilizando o código da superclasse e personalizando apenas o método `runAnimal()`.

3. A classe principal, **BetterThreadRace**, cria as threads para os animais e inicia a corrida.

---

## **🛠️ Estrutura do Código**

1. **Classe Base: `AnimalRunner`**: define a estrutura básica para todos os animais, como o início da corrida e o controle da execução. O método `run()` controla a corrida e chama o método abstrato `runAnimal()`, que será implementado nas subclasses.
2. **Subclasses (`Rabbit`, `Turtle`, `Goat`)**: Cada uma dessas classes herda de `AnimalRunner` e implementa o jeito de correr.
3. **Classe Principal: `BetterThreadRace`**: A classe principal gerencia a execução das threads. Ela cria instâncias dos animais e inicia a execução das threads para simular a corrida.

---

### 📜 **Código**

```java
abstract class AnimalRunner {
    protected String name;

    public AnimalRunner(String name) {
        this.name = name;
    }

    
    public abstract void runAnimal();
}

class Rabbit extends Thread {  
    public Rabbit(String name) {
        super(name);
    }

    public void runAnimal() { 
        System.out.println(getName() + " is running fast");
    }

    @Override
    public void run() {
        System.out.println(getName() + " rabbit is at the start of the race!");
        for (int pos = 10; pos > 0; pos--) {
            runAnimal();
            System.out.println(getName() + " is at position " + pos);
        }
        System.out.println(getName() + " rabbit finished the race!");
    }
}

class Turtle implements Runnable {
    private String name;

    public Turtle(String name) {
        this.name = name;
    }

    public void runAnimal() {
        System.out.println(name + " is running slow");
    }

    @Override
    public void run() {
        System.out.println(name + " turtle is at the start of the race!");
        for (int pos = 10; pos > 0; pos--) {
            runAnimal(); 
            System.out.println(name + " is at position " + pos);
        }
        System.out.println(name + " turtle finished the race!");
    }
}

class Goat implements Runnable {
    private String name;

    public Goat(String name) {
        this.name = name;
    }

    public void runAnimal() {
        System.out.println(name + " aaaaaa");
    }

    @Override
    public void run() {
        System.out.println(name + " goat is at the start of the race!");
        for (int pos = 10; pos > 0; pos--) {
            runAnimal(); 
            System.out.println(name + " is at position " + pos);
        }
        System.out.println(name + "  finished the race!");
    }
}

public class BetterThreadRace {
    public static void main(String[] args) {
       
        Rabbit r = new Rabbit("Snowball");
        Thread t = new Thread(new Turtle("Donatello"));
        Thread g = new Thread(new Goat("goat"));

        
        r.start();  
        t.start();  
        g.start();  
    }
}
