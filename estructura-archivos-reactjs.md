# Estructura de archivos React Js

## Estructura básica de carpetas en un proyecto generado con create-react-app

```start project first way
npx create-react-app nombre-proyecto
```

> ⇨📂 node-modules 

> ⇨📂 public 

> ⇨📂 src

## Estructura básica de carpetas en un proyecto generado con vite

```start project second way
npm create vite@latest
type your project name
indicate your framework 
select a variant
```

> ⇨📂 node-modules 

> ⇨📂 public 

> ⇨📂 src


La mayor parte del tiempo vamos a utilizar la carpeta raiz ***src*** para la creación de carpetas en nuestro proyecto

## Formas recomendadas para estructurar el proyecto 

// Nota: La estructura de carpetas dependera en gran parte de las definiciones de trabajo dentro del equipo de desarrollo

- Agrupación por funcionalidades o rutas
- Agrupando por tipo de archivo
- [Atomic desing](https://andela.com/insights/structuring-your-react-application-atomic-design-principles/)

***

## Uno de lo más utilizados y recomendados es ***Agrupación por tipo de archivos***

* Esta forma es muy utilizada ya que es sencilla de mantener y los archivos quedan bien estructurado.

* Si su proyecto requiere el uso de otras carpetas se podrán crear, cómo por ejemplo **📂utils**, **📂config** lo único seria seguir manejando la agrupación por tipo de archivo.

* Puedes crear las carpetas que necesites para su proyecto en este caso se muestra una estructura básica las cuales se sugieren que deberia de tener el proyecto.


> ⇨📂 node-modules

> ⇨📂 public

> ⇩📂 src
    
        ⇨📂 components 

        ⇨📂 services  

        ⇨📂 assets

        ⇨📂 pages

# Veamos cómo se trabajaria con esta estructura

### 📂 components 

* Se recomienda crear todos los componentes globales por ejemplo ***navbar, footer*** en una carpeta **components** en la carpeta raiz **src**. 

* Son los componentes que se requieren en más de una página

* Cómo podemos observar dentro de **components** se crean otras carpetas que agrupan los archivos similares.

> ⇩📂 components 

        ⇩📂 navbar

            Navbar.jsx

            navbar.test.js
        
        ⇩📂 footer

            Footer.jsx

            footer.test.js

            footer.css

### 📂 services

* Se recomienda crear esta carpeta para las peticiones a las apis 

* Es una mala práctica crear las peticiones a la api desde el mismo componente

* La mejor forma es crear un archivo que exporte una función con la petición para luego ser implementada donde se requiera

> ⇩📂 services
    
        users_service.js 

        products_service.js

### 📂 assets

* Es recomendada también una carpeta donde se va a almacenar todo lo relacionado con archivos de multimedia

> ⇩📂 assets

        foto.png

        img.svg

        video.mp4

### 📂 pages

* Por ultimo se recomienda la carpeta donde van a estar las páginas, de la misma forma los archivos similares estaran agrupados en una carpeta

* Vemos que **📂profile** y **📂user** tienen una carpeta **📂components** esto es porque en esta carpeta van a estar agrupados todos los componentes que solo
van a existir en una única página 

* En este caso **📂profile** va a tener todos los archivos similares agrupados, pero si esta página utiliza muchos componentes seria difícil de mantener
por es se sugiere crear una carpeta **📂components**


> ⇩📂 pages

        ⇩📂 profile
            ⇩📂 components
                ⇩📂 card

                    Card.jsx

                    card.css

                    card.test.js

            Profile.jsx 


        ⇩📂 user
            ⇨📂 components

            User.jsx 

## Creacion de componentes en React

> Nombramiento de componentes

* Se recomienda comenzar siempre los nombres de los componentes con una letra mayuscula.
* El nombramiento de los componentes en react usualmente se capitaliza para que pueda ser renderizado sin problemas.
      
		import todo from './components/todo';
		<todo /> // error

		import Todo from './components/todo';
		<Todo /> // ok

* Aunque nombremos el hook en minúscula lo importante es que a la hora de importarlo sea con el nombre capitalizado, 
  sin embargo, lo recomendable es directamente capitalizar a la hora de nombrar este.

> Creacion de componentes

* Dentro de react hay varias formas a la hora de crear un componente, a continuación se muestran las mas usuales: 

```first way
const MiComponent = function({prop1,prop2}){
	return(
		//JSX
	)
}
```

```second way
const MiComponent = ({prop1,prop2}) => (/*JSX*/);
```
* El uso de estas formas para crear tus componentes dependera en gran medida de como te sientas a la hora de trabajar con cada una de ellas

## Importaciones y Exportaciones en react

> Importaciones

* En react podemos importar todo el modulo o simplemente hacer un destructuring para obtener sólo lo que necesitamos.

```
import Router from 'react-router';
const {Link} = Router;
```

* Seria equivalente a esto si hacemos destructuring

```
import {Link} from 'react-router';
```

> Exportaciones

* Dentro de react hay dos formas de exportar un componente, se puede exportar por **default** o **named**

``` first way
export function Greet() {
  return (
    <div className="App">
      <h1>Hello</h1>
    </div>
  );
}

export function Talk() {
  return (
    <div className="App">
      <h1>How are you?</h1>
    </div>
  );
}
```

* Podriamos importar este componente en otro archivo de la siguiente forma: 

```
import {Talk, Greet} from "./components/source.jsx"
```

``` second way
export default function App() {
  return (
    <div className="App">
      <h2>Hello world!</h2>
    </div>
  );
}
```

* Si quisieramos importar em componente App, se realizaria de la siguiente forma: 

```
import Application from "./components/App.jsx"
```
* No tenemos que usar llaves, ni tampoco es necesario usar el mismo nombre del enlace del archivo fuente



## Convenciones de diseño

Un buen diseño utiliza un formato que destaque la estructura del código y haga que el código sea más fácil de leer.

* Escriba solo una instrucción por línea.
* Escriba solo una declaración por línea.
* Si a las líneas de continuación no se les aplica sangría automáticamente, hágalo con una tabulación (cuatro espacios).
* Agregue al menos una línea en blanco entre las definiciones de método y las de propiedad.
* Utilice nombres descriptivos para las variables.
* Utilice paréntesis para que las cláusulas de una expresión sean evidentes, como se muestra en el código siguiente.
```cs
if (condicción)
{
    // acción
}



## Mantener los componentes siempre compactos

La ventaja de tener componentes siempre compactos es la facilidad de su reutilización y mantenibilidad.
Una buena práctica para tener componentes legibles y compactos es evitar las definiciones de funciones de utilidad en el mismo cuerpo del componente.

* Se recomienda mover estas funciones de utilidad a la carpeta **📂utils** dentro del directorio de la página donde son usados.
* Las funciones de utilidad que se utilicen en componentes de páginas diferentes, irán en la carpeta **📂utils** en el directorio 📂 src.
* Evitar funciones o métodos muy extensos, aplicando en lo posible el concepto de extracción de métodos. Las nuevas funciones que resulten de este proceso deberán ir en la carpeta **📂 utils** correspondiente
* Revisar si es posible y viable dividir el componente en componentes más pequeños

Nota: Se recomienda usar ESLINT y Prettier dentro de tu entorno de trabajo

// Nota (Sugerencia):  Consideramos que seria bueno añadir algo de información con relación a: 
						- Eliminar duplicidad y codigo inutilizable 
						- Convenciones de pruebas unitarias en react 
						- Mantener los componentes siempre compactos 
						- Emplear ESLint para linting
