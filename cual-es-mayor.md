# 2. ¿Cuál es mayor? 🙌

## 💡 Introducción 💡 <a id="1-introduccion"></a>

Este desafío consiste en construir un juego en el que el usuario debe seleccionar el mayor entre dos números generados aleatoriamente: [**¡Aquí puedes encontrar el demo!**](https://greater-than.stackblitz.io)\*\*\*\*

¿Estás lista?

**Por supuesto que estás lista, desde el día en que naciste 😝**

## Paso 1: Crear el título ⭐️

Lo primero que haremos será construir los títulos y los botones. Para ello simplemente iremos al archivo **app.component.html** y empezaremos reemplazando su contenido con el siguiente código:

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<h1>¿Cuál es mayor? 🙌</h1>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Deberías ver algo así: 👇

![En Stackblitz no tienes que refrescar el navegador, &#xE9;l autom&#xE1;ticamente te muestra los cambios &#x270C;&#xFE0F;](.gitbook/assets/image%20%288%29.png)

## Paso 2: Agregar los botones 💻

Ahora vamos agregar **los botones.** Para hacerlo vamos a usar la etiqueta **&lt;button&gt;**:

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<h1>¿Cuál es mayor? 🙌</h1>
<button>7</button>
<button>9</button>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Deberías ver algo así: 👇

![](.gitbook/assets/image%20%283%29.png)

## Paso 3: Agregar el score 🏁

¡Esta es tu oportunidad de brillar! Ayúdanos agregando el título de **Score** utilizando la etiqueta **&lt;h1&gt;.** Cuando lo hagas, debería verse así: 👇

![](.gitbook/assets/image%20%289%29.png)

## Paso 4: Agregar los estilos 💅

Nuestra interfaz luce bien, pero podría lucir mejor 😏. Vamos a agregar un poco de **CSS** para darle color a nuestro videojuego. Reemplaza el contenido de **app.component.css** con éste:

{% code-tabs %}
{% code-tabs-item title="app.component.css" %}
```css
* {
  font-family: Lato;
}

button {
  background: hotpink;
  border: 3px solid black;
  border-radius: 4rem;
  font-size: 3rem;
  width: 5rem;
  box-shadow: 2px 2px 10px 0px gray;
  margin: 1rem;
  outline: none;
  cursor: pointer;
  transition: box-shadown 2s;
}

button:hover {
  background: #ff409f;
}

button:active {
  box-shadow: inset 2px 2px 10px 0px black;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Ahora nuestra aplicación debería verse mucho mejor: 👇

![](.gitbook/assets/image%20%284%29.png)

¡Ya casi terminamos! 👏

## Paso 5: Generar los números 📱

¡Ahora es momento de pasar a la lógica! Nosotros utilizaremos TypeScript, que es lo mismo que JavaScript sólo que mejorado 🤝.

Lo primero que haremos es que definiremos las variables que vamos a usar en el archivo **app.component.ts**:

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```typescript
export class AppComponent {
  leftNumber;
  rightNumber;
  score = '';  
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

El segundo paso es inicializar los números. Para ello debemos empezar creando una función que genere números de manera aleatoria. La llamaremos **generateRandomNumber\(\):**

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```typescript
export class AppComponent {
  leftNumber;
  rightNumber;
  score = '';
  
  generateRandomNumber() {
    const maxNumber = 10;
    const randomDecimal = Math.random() * maxNumber;
    const randomNumber = Math.round(randomDecimal);
    return randomNumber;
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Échale un ojo por un momento. Analiza su funcionamiento. Trata de inferir cómo funciona 👆.

Listo? 😀

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️**

**1.** Primero definimos una variable llamada **maxNumber.** Ésta almacenará el número más alto que deseamos generar al azar. Puedes cambiarlo por **100** o **1000. 👍**

**2.** En segundo lugar generamos el número aleatorio utilizando la función **Math.random\(\).** Ésta es una función propia de JavaScript y lo que hace es devolvernos un valor aleatorio entre **0** y **1.** Al multiplicarlo por **10** estamos generando un número al azar entre **0** y **10**. 😉

**3.** El último paso es remover los decimales adicionales. Ya que de otro modo tendríamos números como **6.3** o **1.5.** Para sólo basta con utilizar la función **Math.round\(\)** que nos permite redondear números. ⭐️
{% endhint %}

Ahora, para generar los números aleatorios basta con que los asignemos: 👇

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```typescript
export class AppComponent {
  leftNumber;
  rightNumber;
  score = '';
  
  generateNumbers() {
    this.leftNumber = this.generateRandomNumber();
    this.rightNumber = this.generateRandomNumber();
  }
  
  generateRandomNumber() {
    const maxNumber = 10;
    const randomDecimal = Math.random() * maxNumber;
    const randomNumber = Math.round(randomDecimal);
    return randomNumber;
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Como habrás notado simplemente creamos la función **generateNumbers\(\)** que se encarga de llamar la función que creamos para cada número. 👍

Para que el código funcione debemos asegurarnos de llamar a la función que acabamos de crear. Para ello podemos usar el constructor: 👇

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```typescript
export class AppComponent {
  leftNumber;
  rightNumber;
  score = '';
  
  constructor() {
    this.generateNumbers();
  }
  
  generateNumbers() {
    this.leftNumber = this.generateRandomNumber();
    this.rightNumber = this.generateRandomNumber();
  }
  
  generateRandomNumber() {
    const maxNumber = 10;
    const randomDecimal = Math.random() * maxNumber;
    const randomNumber = Math.round(randomDecimal);
    return randomNumber;
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

¡Eso es todo! Sólo hace falta mostrar los números, que es el paso más sencillo. Abre el archivo **app.component.html** y reemplaza su contenido así: 👇

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<h1>¿Cuál es mayor? 🙌</h1>
<button>{{leftNumber}}</button>
<button>{{rightNumber}}</button>
<h1>Score</h1>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️**

**String Interpolation** es la técnica a través de la cual mostramos los números en la vista \(HTML\). Para ello simplemente basta con tener las variables declaradas y utilizar las llaves para mostrarla así: **{{ myVariable }}** 
{% endhint %}

¡Cada vez que recargues el navegador verás números generados de manera aleatoria! 🎉🎉🎉

![](.gitbook/assets/merge_from_ofoct.jpg)

## Paso 6: No repetir números 🖐

¡Parece ser que en algunas ocasiones los números se repiten! Debemos evitar esto \(porque de otro modo no podríamos jugar el juego 😝\).

Cuando ambos números generados aleatoriamente sean iguales vamos a volver a llamar a la función 👇

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```typescript
...
generateNumbers() {
  this.leftNumber = this.generateRandomNumber();
  this.rightNumber = this.generateRandomNumber();
  if (this.leftNumber === this.rightNumber) {
      this.generateNumbers();
  }
}
...
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Fácil verdad? 😊

## Paso 7: Comparemos! 👽

¡Es momento de comparar qué número es mayor! Lo cual es muy sencillo. Para esto necesitamos una función que:

1. Compare los dos números
2. Actualice el **Score** respectivamente
3. Genere números nuevos

Para hacerlo simplemente basta con ir al archivo **app.component.ts** y agregar la siguiente función:

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```typescript
...
  isGreater(firstValue, secondValue) {
    if (firstValue > secondValue) {
      this.score = this.score + '😁';
    } else {
      this.score = this.score + '❌';
    }
    this.generateNumbers();
  }
...
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Analiza el código de arriba. Trata de interpretarlo. ¿Lo comprendes? 😉

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️**

**1.** Primero creamos una función que recibe dos números. Los números que vamos a comparar **👍**

**2.** En segundo lugar hacemos la comparación. Dependiendo del resultado concatenamos los emojis respectivos \(😉 o ❌\).

**3.** El último paso es generar nuevos números aleatorios para continuar jugando. ⭐️
{% endhint %}

Estamos a punto de acabar. Sólo nos basta con hacer los que botones llamen la función que acabamos de crear cada vez que sean oprimidos. 💪

Para hacerlo vamos a ir a **app.component.html** y vamos a reemplazar el siguiente código:

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<h1>¿Cuál es mayor? 🙌</h1>

<button (click)="isGreater(leftNumber, rightNumber)">{{leftNumber}}</button>
<button (click)="isGreater(rightNumber, leftNumber)">{{rightNumber}}</button>

<h1>Score:</h1>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Analiza el código. ¿Parece coherente? 👆

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️**

**1.** Primero que todo estamos utilizando una técnica llamada **Event Binding.** Ella nos permite agregar eventos a nuestra vista. En este caso utilizamos el evento de **Click**, pero pueden ser muchos tipos: **\(keyup\)**, **\(change\)**, **\(resize\)**, etc  💻

**2.** Luego simplemente escribimos el método que deseamos llamar cuando el evento se ejecute. En este caso estamos llamando a la función **isGreater\(\)** que creamos anteriormente.

**3.** Notarás que el primer botón pasamos **leftNumber** y luego **rightNumber**, pero en el segundo botón invertimos el orden. Esto es porque la función que creamos va a determinar si el **primer parámetro** que se le pasó es mayor que el **segundo parámetro**. ⭐️
{% endhint %}

**¡Revisa tu aplicación!**

Cada vez que hagas click en un botón debería generar nuevos números aleatorios. 📱

## 😎 Tu Misión 😎

Parece que nuestra aplicación está lista excepto por un pequeño detalle 😵. Parece que no está mostrando el **Score.**

⭐️ Utiliza **String Interpolation** para mostrar el **Score**. Usa la etiqueta **&lt;h2&gt;** ⭐️

¡Cuando lo hayas hecho, habrás terminado el primer desafío!

{% hint style="info" %}
\*\*\*\*[**Aquí**](https://stackblitz.com/edit/greater-than?file=src%2Fapp%2Fapp.component.html) puedes encontrar el ejercicio resuelto.
{% endhint %}

## 🎉 ¡**LO LOGRASTE!** 🎉

{% hint style="success" %}
Has completado el **desafío \#2**, ahora vamos a el **desafío \#3 👇**
{% endhint %}

