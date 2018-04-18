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
<code>
public abstract class Combo {
  
 String descripcion = "";
  
 public String getDescripcion() 
 {
  return descripcion;
 }
 
 public abstract int valor();
 
}
+
+
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
+
+
public abstract class AdicionalesDecorator extends Combo{
 
 public abstract String getDescripcion();
}
+
+
public class Carne extends AdicionalesDecorator{
 
 Combo combo;
  
 public Carne(Combo combo)
 {
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
</code>
### Referencias
 http://migranitodejava.blogspot.com.co 

 https://informaticapc.com 
 
 https://www.genbetadev.com/metodologias-de-programacion
 http://joedicastro.com/pages/markdown.html
