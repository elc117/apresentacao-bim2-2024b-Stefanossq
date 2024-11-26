# 🏁 **Animal Thread Race** 🐇🐢🐐
### **Threads e Herança em Java**

---

## **📖 Problema**  
**Resolver a Prática da Aula 21:**  
> Crie um novo programa, **BetterThreadRace.java**, contendo uma **classe base abstrata (`AnimalRunner`)** da qual serão derivadas três classes de animais. Faça as modificações necessárias para que o novo programa funcione como o original, mas com um código mais estruturado e reutilizável.

---

## **💡 Solução**  
 

### **Como resolver o problema?**
1. Criar a **superclasse** `AnimalRunner`, que contém o comportamento em comum da corrida, e o método abstrato RunAnimal() para cada animal.  

2.(`Rabbit`, `Turtle`, `Goat`) implementados como uma **subclasse de `AnimalRunner`**,  com o comportamento comum controlado na superclasse e o método runAnimal() sendo específico de cada um.

3. A classe principal, **BetterThreadRace**, instancia os animais e executa as threads.

---

## **🛠️ Estrutura do Código**

1. **Classe Base: `AnimalRunner`**: define a estrutura básica para todos os animais, como o início da corrida e o controle da execução. O método `run()` controla a corrida e chama o método abstrato `runAnimal()`, que será implementado nas subclasses.
2. **Subclasses (`Rabbit`, `Turtle`, `Goat`)**: Cada uma dessas classes herda de `AnimalRunner` e implementa o jeito de correr.
3. **Classe Principal: `BetterThreadRace`**: A classe principal gerencia a execução das threads. Ela cria instâncias dos animais e inicia a execução das threads para simular a corrida.

---

### 📜 **Código**

```java
abstract class AnimalRunner implements Runnable {
    protected String name;

    
    public AnimalRunner(String name) {
        this.name = name;
    }

    
    public abstract void runAnimal();

    @Override
    public void run() {
        
        System.out.println(name + " is at the start of the race!");
        for (int pos = 10; pos > 0; pos--) {
            runAnimal(); 
            System.out.println(name + " is at position " + pos);
        }
        System.out.println(name + " finished the race!");
    }
}

class Rabbit extends AnimalRunner {
    public Rabbit(String name) {
        super(name);
    }

    @Override
    public void runAnimal() {
        System.out.println(name + " is running fast!");
    }
}

class Turtle extends AnimalRunner {
    public Turtle(String name) {
        super(name);
    }

    @Override
    public void runAnimal() {
        System.out.println(name + " is running slow!");
    }
}

class Goat extends AnimalRunner {
    public Goat(String name) {
        super(name);
    }

    @Override
    public void runAnimal() {
        System.out.println(name + " aaaaaa");
    }
}

public class BetterThreadRace {
    public static void main(String[] args) {
     
        Thread rabbit = new Thread(new Rabbit("Snowball"));
        Thread turtle = new Thread(new Turtle("Donatello"));
        Thread goat = new Thread(new Goat("Goat"));

        
        rabbit.start();
        turtle.start();
        goat.start();
    }
}

---

![bandicam-2024-11-26-01-07-59-493](https://github.com/user-attachments/assets/bbe7d3c0-9d81-4b49-a0ae-37e9385ce4ec)

