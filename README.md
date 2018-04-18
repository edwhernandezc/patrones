# Patrones
# Patrones Creacionales

### Integrantes
1. Edwin Hernández Cabrera - 20152020013

## Sinlgeton
### Introducción
Es un patrón de diseño que permite restringir la creación de objetos pertenecientes a una clase o el valor de un tipo a un único objeto. Su intención consiste en garantizar que una clase sólo tenga una instancia y proporcionar un punto de acceso global a ella. Lo utilizamos porque permite acceso controlado a la única instancia, puede tener un control estricto sobre cómo y cuándo acceden los clientes a la instancia, Debe haber exactamente una instancia de una clase, y debe ser accesible a los clientes desde un punto de acceso conocido.

![GitHub Logo](https://github.com/paulagomez05/PatronesCreacionales/blob/master/2.png)

En el diagrama UML, la clase que es Singleton define una instancia para que los clientes puedan accederla. Esta instancia es accedida mediante un método de clase.Los clientes (quienes quieren acceder a la clase Singleton) acceden a la única instancia mediante un método llamado getInstance().

En el siguiente bloque de codigo podemos ver como implementamos el patron de diseño singleton el cual permite restringir la creacion de objetos y garantizar la instanciacion de una sola clase, este patron se ve implementado en el prestamo de bicicletas en nuestro programa.

![GitHub Logo](https://github.com/paulagomez05/PatronesCreacionales/blob/master/1.png)

## Prototype
### Introducción
El patrón prototype tiene un objetivo muy sencillo: crear a partir de un modelo.Permite crear objetos prediseñados sin conocer detalles de cómo crearlos. Esto lo logra especificando los prototipos de objetos a crear. Los nuevos objetos que se crearán de los prototipos, en realidad, son clonados. Vale decir, tiene como finalidad crear nuevos objetos duplicándolos, clonando una instancia creada previamente.

![GitHub Logo](https://github.com/paulagomez05/PatronesCreacionales/blob/master/prototype.gif)

En el siguiente bloque de codigo podemos ver como implementamos el patron creacional prototype el cual permite realizar las clonaciones necesarias de las naves; es un patron muy funcional a la hora de necesitar la creacion de objetos parametrizados.

![GitHub Logo](https://github.com/paulagomez05/JuegoPrototype/blob/master/3.png)

## Factory Method
### Introducción

Factory Method es un patrón de creación de objetos y normalmente se suele usar para solucionar el problema que se presenta cuando tenemos que crear la instancia de un objeto pero a priori no sabemos aún que tipo de objeto tiene que ser, generalmente, porque depende de alguna opción que seleccione el usuario en la aplicación o porque depende de una configuración que se hace en tiempo de despliegue de la aplicación. Define la interfaz de creación de un cierto tipo de objeto, permitiendo que las subclases decidan que clase concreta necesitan instancias.

![GitHub Logo](https://github.com/paulagomez05/PatronesCreacionales/blob/master/factory.jpg)

En el siguiente bloque de codigo podemos ver como se puede implementar el patron creacional Factory Method

<pre><code>
package FactoryMethod1;
public class Main
{
    public static void main(String[] args)
    {
         CreadorAbstracto creator = new Creador();
        IArchivo audio = creator.crear( Creador.AUDIO );
        audio.reproducir();
        IArchivo video = creator.crear( Creador.VIDEO );
        video.reproducir();
    }
}
// PRODUCTO, SEGUN UML//
package FactoryMethod2;
 public interface IArchivo
{
    public void reproducir();
}
// PRODUCTO CONCRETO, SEGUN UML//
package FactoryMethod2;
public class ArchivoAudio implements IArchivo
{
    public ArchivoAudio() {
    }
// CREADOR, SEGUN UML//
    package FactoryMethod1;
 public abstract class CreadorAbstracto
{
    public static final int AUDIO = 1;
    public static final int VIDEO = 2;
    // --------------------------------
     public abstract IArchivo crear(int tipo);
}
// CREADOR CONCRETO, SEGUN UML//
package FactoryMethod1;
public class Creador extends CreadorAbstracto
{
    public void Creador() {
    }
</code></pre>

# Patrones Estructurales
## Decorator
### Introducción
El patrón decorator permite añadir responsabilidades a objetos concretos de forma dinámica. Los decoradores ofrecen una alternativa más flexible que la herencia para extender las funcionalidades.
### Este patrón se debe utilizar cuando:
Hay una necesidad de extender la funcionalidad de una clase, pero no hay razones para extenderlo a través de la herencia.
Se quiere agregar o quitar dinámicamente la funcionalidad de un objeto.
![GitHub Logo](https://lh6.googleusercontent.com/vIoskk-tgi1crMhB0O-Cd3lQZwpYOEfs8_tPxCvTC5hK0yHjlIXHDIVLJa-gwRhoesr-BLI-nUhctVOn1FUAD6XWOVKtQNzUoZ8nayfwYarmy5JkpQ)
### Codigo
<pre><code>
  public abstract class Combo {

    String descripcion = "";

    public String getDescripcion() {
      return descripcion;
    }
    public abstract int valor();

    }

  public class ComboBasico extends Combo{

    public ComboBasico() {
      descripcion="Porcion de Papas Fritas, " +
      "salsa, queso, amburgueza sencilla, gaseosa";
    }

    @Override
    public int valor() {
      return 6200;
    }
  }

  public abstract class AdicionalesDecorator extends Combo{
    public abstract String getDescripcion();
    }

  public class Carne extends AdicionalesDecorator{
    Combo combo;

    public Carne(Combo combo){
      this.combo=combo;
    }

    @Override
    public String getDescripcion() {
      return combo.getDescripcion()+" , Porcion de Carne";
    }

    @Override
    public int valor() {
      return 2500+combo.valor();
    }
  }
}
</code>
</pre>
## Adapter
### Introducción
Busca una manera estandarizada de adaptar un objeto a otro. Se utiliza para transformar una interfaz en otra, de tal modo que una clase que no pudiera utilizar la primera, haga uso de ella a través de la segunda.
Es conocido como Wrapper (al patrón Decorator también se lo llama Wrapper, con lo cual es nombre Wrapper muchas veces se presta a confusión).
Una clase Adapter implementa un interfaz que conoce a sus clientes y proporciona acceso a una instancia de una clase que no conoce a sus clientes, es decir convierte la interfaz de una clase en una interfaz que el cliente espera. Un objeto Adapter proporciona la funcionalidad prometida por un interfaz sin tener que conocer que clase es utilizada para implementar ese interfaz. Permite trabajar juntas a dos clases con interfaces incompatibles.
### Este patrón se debe utilizar cuando
* Se quiere utilizar una clase que llame a un método a través de una interface, pero se busca utilizarlo con una clase que no implementa ese interface.
* Se busca determinar dinámicamente que métodos de otros objetos llama un objeto.
* No se quiere que el objeto llamado tenga conocimientos de la otra clase de objetos.
### Diagrama UML
![Diagrama UML](https://lh6.googleusercontent.com/RIOjG1cnE_Sy_X-eW6Hvs5YeG7tbyDeon1Lc1p2Ujkzg6PzXFD2UMr2kVz18w_Uif12nJQ3WJt8nNqBHSkvjGh1KY28BTrH8s1g4mSNQbXeu3Xi4yw)

## Bridge
### Introducción
Desacopla una abstracción de su implementación, de manera que ambas puedan variar de forma independiente. ¿Que quiere decir exactamente esto? Una abstracción se refiere a un comportamiento que una clase debería implementar, ya sea porque esta obligada por una interface o una clase abstracta. Por otro lado, con implementación se refiere a colocarle lógica a dicha obligación.
Con lo cual, este patrón permite modificar las implementaciones de una abstracción en tiempo de ejecución. Básicamente es una técnica usada en programación para desacoplar la interface de una clase de su implementación, de manera que ambas puedan ser modificadas independientemente sin necesidad de alterar por ello la otra.

Cuando un objeto tiene unas implementaciones posibles, la manera habitual de implementación es el uso de herencias. Muchas veces la herencia se puede tornar inmanejable y, por otro lado, acopla el código cliente con una implementación concreta. Este patrón busca eliminar la inconveniencia de esta solución.

### Este patrón se debe utilizar cuando

* Se desea evitar un enlace permanente entre la abstracción y su implementación. Esto puede ser debido a que la implementación debe ser seleccionada o cambiada en tiempo de ejecución
* Tanto las abstracciones como sus implementaciones deben ser extensibles por medio de subclases. En este caso, el patrón Bridge permite combinar abstracciones e implementaciones diferentes y extenderlas independientemente.
* Tanto las abstracciones como sus implementaciones deben ser extensibles por medio de subclases. En este caso, el patrón Bridge permite combinar abstracciones e implementaciones diferentes y extenderlas independientemente.
* Tanto las abstracciones como sus implementaciones deben ser extensibles por medio de subclases. En este caso, el patrón Bridge permite combinar abstracciones e implementaciones diferentes y extenderlas independientemente.
* Permite simplificar jerarquías demasiado pobladas.

### Diagrama UML
![Diagrama UML](https://lh6.googleusercontent.com/0KHlNjYDLgZjoaW5VipnnOIBXECMh5OC_37Ct4HmvjAwz_ZdU9AxKSjDq5OY5N6ztQNW0XyaG_Uf3I-2uggyaLfB7p--v63kqK5YQs6DtqHhRfUwm9E)

## Composite
### Introducción
El patrón Composite sirve para construir algoritmos u objetos complejos a partir de otros más simples y similares entre sí, gracias a la composición recursiva y a una estructura en forma de árbol. Dicho de otra forma, permite construir objetos complejos componiendo de forma recursiva objetos similares en una estructura de árbol. Esto simplifica el tratamiento de los objetos creados, ya que al poseer todos ellos una interfaz común, se tratan todos de la misma manera.

Este patrón busca representar una jerarquía de objetos conocida como “parte-todo”, donde se sigue la teoría de que las "partes" forman el "todo", siempre teniendo en cuenta que cada "parte" puede tener otras "parte" dentro.

### Este patrón se debe utilizar cuando
* Se busca representar una jerarquía de objetos como “parte-todo”.
* Se busca que el cliente puede ignorar la diferencia entre objetos primitivos y compuestos (para que pueda tratarlos de la misma manera).

### Diagrama UML
![Diagrama UML](https://1.bp.blogspot.com/-LYqFnV_rA-o/TeZnLi9Ow7I/AAAAAAAAJMc/Esp_EEepGM8/s1600/image00.jpg)


## Facade
### Introducción
Busca simplificar el sistema, desde el punto de vista del cliente, proporcionando una interfaz unificada para un conjunto de subsistemas, definiendo una interfaz de nivel más alto. Esto hace que el sistema sea más fácil de usar.

Este patrón busca reducir al mínimo la comunicación y dependencias entre subsistemas. Para ello, utilizaremos una fachada, simplificando la complejidad al cliente. El cliente debería acceder a un subsistema a través del Facade. De esta manera, se estructura un entorno de programación más sencillo, al menos desde el punto de vista del cliente (por ello se llama "fachada").

### Este patrón se debe utilizar cuando
* Se quiera proporcionar una interfaz sencilla para un subsistema complejo.
* Se quiera desacoplar un subsistema de sus clientes y de otros subsistemas, haciéndolo más independiente y portable.
* Se quiera dividir los sistemas en niveles: las fachadas serían el punto de entrada a cada nivel. Facade puede ser utilizado a nivel aplicación.

### Diagrama UML
![Diagrama UML](https://lh3.googleusercontent.com/zRSPCgsvEraePczqEnz812vs4Q1bIdsNfanLyuRMcOnPoguqR5Fn-cErEwr8K_Eh-LKjVzRfyiY2sCrqrhVZLoYjnVU6Kl_CXqkZsxGpOFgbXghuAXA)


## Flyweight
### Introducción
Busca eliminar o reducir la redundancia cuando tenemos gran cantidad de objetos que contienen información idéntica, además de lograr un equilibrio entre flexibilidad y rendimiento (uso de recursos).
Este patrón quiere evitar el hecho de crear un gran número estados de objeto para representar a un sistema. Permite compartir estados para soportar un gran número de objetos pequeños aumentando la eficiencia en espacio.

### Este patrón se debe utilizar cuando
* Para eliminar o reducir la redundancia cuando se tiene gran cantidad de objetos que contienen la misma información.
* Cuando la memoria es crítica para el rendimiento de la aplicación.
* La aplicación no depende de la identidad de los objetos.

### Diagrama UML
![Diagrama UML](https://lh6.googleusercontent.com/U8FtCPlWF05eCqgwYsQuO4IPhNEbo2eD7-VD-Zpd-FcR7A9xO_rDVOg08QWkdM2tiO4T1p2CaQeTJfmehzwPoKfTAvX4bga8klpg9P2LxRlGuwLQu10)

### Referencias
 http://migranitodejava.blogspot.com.co
 https://informaticapc.com
 https://www.genbetadev.com/metodologias-de-programacion
 http://joedicastro.com/pages/markdown.html
