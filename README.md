

# Smalltalk Introducción

#### Introducción Histórica
SMALLTALK es un lenguaje orientado a objetos puro, pues todas las entidades que maneja son objetos.
 El lenguaje se basa en conceptos tales como objetos y mensajes.
 SMALLTALK es descendiente del lenguaje SIMULA y tiene sus orígenes en el Centro de Estudios de Palo Alto de Xerox, en los comienzos de 1970.
  Su desarrollo se basa en gran parte en las ideas de Alan Kay. Las tres versiones principales del lenguaje son SMALLTALK-72, SMALLTALK-76 y SMALLTALK-80.
  SMALLTALK es mucho más que un lenguaje de programación, es un ambiente completo de desarrollo de programas. Éste integra de una manera consistente características tales como un editor, un compilador, un debugger, utilitarios de impresión, un sistema de ventanas y un manejador de código fuente.
  SMALLTALK elimina la frontera entre aplicación y sistema operativo, modelando todos los elementos como objetos.

####  Una nota importante
Diseñar nuevas aplicaciones SMALLTALK, requiere de conocimientos sobre las clases existentes en el sistema SMALLTALK. Frecuentemente la programación en SMALLTALK se denomina "Programación por extensión" Las nuevas aplicaciones son construidas por extensión de las librerías de clases de SMALLTALK
#### Estructura de un sistema smalltalk
Un sistema smalltalk esta compuesto por  :

 - IDE entorno de desarrollo 
 - LENGUAJE IMAGEN se encarga de guardar la   copia de nuestros objetos
 -   MAQUINA VIRTUAL se encarga de ejecutar el   sistema.

#### Descarga e instalación de Pharo
Para descargar y ejecutar Pharo nos dirigimos a https://pharo.org/ y entramos a la sección de descargas
![Pharo instalacion](https://i.imgur.com/LdFFbPV.png)

Una vez allí nos dirigimos hasta el apartado **Pharo Standalone**  y descargamos en el caso de Windows la **Pharo VM** y la **Pharo image**
![enter image description here](https://i.imgur.com/o5DIG90.png)

Por ultimo descomprimimos la Pharo VM y la Pharo image, es preferible crear un directorio para guardar nuestra Pharo imagen.

Luego en la carpeta de la VM que descomprimimos debemos encontrar la aplicación **Pharo.exe** la abrimos y nos sale una ventana donde seleccionamos la imagen que descargamos y descomprimimos, luego de esto deberíamos ver una ventana similar a esta:

![enter image description here](https://i.imgur.com/1PIcLL2.png)

##### libros Pharo
http://books.pharo.org/

##### Curso Pharo
https://mooc.pharo.org/

####  Conceptos Básicos
	### clase
	### instancia de clase (objeto)
	### mensaje
	### herencia

La programación en Smalltalk consiste en crear clases, crear instancias y especificar la secuencia de mensajes entre objetos
	
#### Sintaxis Básica
La sintaxis en Smalltalk es muy simple, minimalista, elegante ya que fue originalmente pensada para niños, los programas se parecen oraciones.


La sintaxis en Smalltalk es del tipo:

    objeto mensaje

Existen 3 tipos de mensajes

 1. **Unarios** el receptor recibe un solo argumento
 2. **Binarios**
 3. **Typo Keyword** pueden recibir uno o mas parámetros

#### Precedencia de mensajes

 - Primero se ejecutan los paréntesis
 - Luego los mensajes unarios
 - finalmente los de tipo keyword
 

##### Hola mundo en Smalltalk

    Transcript show: 'Hola mundo'.
    
En este caso estamos enviando al objeto **Transcript** el mensaje **show** y pasamos como parámetro la cadena de caracteres 'Hola mundo'

> para cadenas de caracteres usamos ' ' comillas simples y para hacer
> comentarios usamos "" comillas dobles
> Las sentencias finalizan con un  punto ( . ) similar a ; en otros lenguajes como c o java



#### Variables
Las variables locales se declaran entre plecas |  |  :

    |variable_1 variable_2 .... variable_n|

####  Comentarios 
Para hacer comentarios usamos  " " comillas dobles

    "Este es un comentario en SmallTalk"

#### Asignación de variables

La asignación de variables se hace con `:=` y la comparación con `=`
	
	
```smalltalk
"Ejemplo Asignacion"
 numero1:=23.

"Ejemplo Comparacion"
 numero1 = numero2.

```

#### Ejemplo 1
  
```smalltalk
"Declaramos Variables"
|numero1 numero2|
   
"Limpiamos la consola"
Transcript clear.
    
"Asignamos 11 a la variable numero1"
 numero1:=11.
    
"Imprimimos el contenido de la variable"
Transcript show: numero1.
    
"Imprimimos un salto de linea"
 Transcript cr.
    
"Asignamos 34 a la variable numero2"
 numero2:=34.
    
"Imprimimos el contendio de la variable numero 2"
Transcript show: numero2.
```

#### Palabras Reservadas
Existen solo 6 palabras reservadas en Pharo , que no se pueden utilizar como nombres de variables.
```smalltalk
true
false
self
super
nil
thisContext
```

#### Bloques de código 

Todo lo que está entre corchetes `[ ]` es un bloque *closures*, estos encierran una o más sentencias de código y pueden ser asignados a una variable y ejecutados luego. También pueden recibir parámetros, son llamados muchas veces *métodos anónimos*.
Como todo en Smalltalk los bloque de código también son objetos.

Los bloques de código responden al mensaje `[] value` que se encarga de ejecutar el código dentro de bloque

```smalltalk
"Bloque de codigo simple sin argumentos"
|numero1|
numero1:=[ 3 + 3 ].
Transcript show: numero1 value
```

también responden al mensaje `[:varname| code ] value:` el cual nos permite pasar argumentos a nuestro bloque

```smalltalk
"Bloque de codigo simple con 1 argumento"
|numero1|
numero1:=[ :x | x+5].
Transcript show: (numero1 value: 5)
```

```smalltalk
"Bloque de codigo simple con varios argumentos"
|suma|
suma:=[ :a :b | a+b].
Transcript show: (suma value:5 value:9)
```
#### Ejemplo  bloques de código

```smalltalk
| holaMundo |
Transcript clear.
"Asignamos a la variable holaMundo el bloque de codigo que esta entre []"
holaMundo:= [ 
Transcript show: 'hola'; cr.
Transcript show: 2*5 ; cr
].


"Posteriormente en algun momento cualquiera podemos llamar a nuestra variable y ejecutar el bloque de codigo las veces que quisieramos enviando el mensaje value"
holaMundo value.
holaMundo value.
```

#### Ejemplo 2 bloques de código con parámetros
Podemos enviar parámetros a los bloques de código de esta  manera
```smalltalk
| sumador |
Transcript clear.
"Asignamos a la variable sumador el bloque de codigo que esta entre [] "
"para definir los parametros usamos :<nombre_del_parametro>"
"luego usamos la pleca | y a continuacion nuestro codigo como hicimos en el ejemplo anterior"
sumador:= [ :x | x+1].

"Por ultimo llamamos a la variable que contiene el bloque de codigo  y le enviamos el argumento usando :"
Transcript show: (sumador value:2);cr.
Transcript show: (sumador value:30)
```

El resultado en nuestro Transcript debería ser

 3
 31

#### Estructuras de Control

En Smalltalk no existen estructuras tales como *if, while, while_true* que podemos ver en en otros lenguajes, pero tenemos formas análogas de hacer esto mediante el envío  de mensajes que ya tenemos definidos a los objetos. Estos mensajes son:

 - (condicion)IfTrue:[ ..... ]
 - (condicion)ifFalse:[ .... ]
 - (condicion)ifTrue:[ .....] ifFalse:[.....]

Todos estos mensajes van a ser comprendidos por instancias de las clases **False** e instancias de las clases **True** .

#### Ejemplo ifTrue, ifFalse

```smalltalk
Transcript clear.
"Si es verdadero ejecuta el codigo y sino no hace nada"
(1 > 2) ifTrue: [Transcript show: 'Es mayor'; cr].
"Si es falso ejecuta el codigo y sino no hace nada"
(1 < 2) ifTrue: [Transcript show: 'Es menor'; cr].
```
#### Ejemplo ifTrue  ifFalse (Else)
```smalltalk
(1 > 2)ifTrue:[Transcript show:'es verdadero'] ifFalse:[Transcript show:'Es Falso'].
```
### Mensajes de iteración

 - timesRepeat: [ ... ]
 - [... ]whileTrue:[ ... ]
 - [...]whileFalse:[...]
 - do:[...]

#### Ejemplos bloques de iteración
```smalltalk
"Times Repeat ejemplo"
|n|

Transcript clear.

n := 1.
"Itera 10 veces acumulando el valor en la variable"
10 timesRepeat: [ n:=n*2 ].

Transcript show: n. 
```

```smalltalk
"While True ejemplo"
|i n|

Transcript clear.

n := 1.
i := 0.
"va a iterar mientras que el valor en la variable i sea menor a 10"
[ i < 10 ]whileTrue:[
	n := n * 2.
	i	:= i + 1.
].

Transcript show: n. 
```


### Arreglos

##### Array
El arreglo mas común en SmallTalk es el *Array* y la forma de utilizarlo es mandarle mensajes.


```smalltalk
| numeros |
Transcript clear.

"Asignamos a la variable numeros la instancia de un objeto array de maximo 5 elementos"

numeros := Array new:5.
"Agregamos elementos al array. Con at: le decimos en que posicion y con put: el valor que queremos guardar en esa posicion "
numeros at:1 put:5.
numeros at:2 put:2/5.
numeros at:3 put:'Ministerio'.

"Mostramos los elementos indicando la posicion del elemento que queremos mostrar"
Transcript show: (numeros at:1);cr.
Transcript show: (numeros at:2);cr.
Transcript show: (numeros at:3);cr.

```
La salida será:
	
       5
       (2/5)
       Ministerio

A diferencia de muchos otros lenguajes en smalltalk los índices de los arreglos comienzan desde `1`

En los arreglos podemos almacenar cualquier tipo de objeto


##### OrderedCollection
A diferencia de los objetos de tipo Array que tienen un tamaño fijo, los objetos de tipo `OrderedCollection` tienen un tamaño de tipo dinámico, esto quiere decir que van aumentar o reducir  su tamaño a medida que vayamos agregando o quitando elementos

```smalltalk
| numeros |
Transcript clear.

"Asignamos a la variable numeros la instancia de un objeto OrderedCollection, a diferencia de Array no necesitamos especificar el tamaño maximo"

numeros := OrderedCollection new.
"Agregamos elementos al array. En este caso no es necesario especificar la posicion donde se va almacenar cada elemento y usamos add en vez de put"
numeros add:5.
numeros add:2/5.
numeros add:'Ministerio'.

"Usamos do, para iterar sobre el objeto y mostrar sus elementos"
"Toma cada elemento de la coleccion y lo imprime"
numeros do: [:numero| Transcript show: numero; cr]

"el parametro :numero indica cada uno de los elementos que estoy iterando"
```

la salida debería ser la misma que con Array

### Implementación de clases y mensajes

Para definir una nueva clase nos dirigimos al menú y cliqueamos en **browse** y luego en **System browser**
![pharo system browser](https://i.imgur.com/2eetQE7.jpg)
Una vez hecho eso se nos abre una ventana con todas las clases y paquetes en nuestro sistema smalltalk. 
![system browser ](https://i.imgur.com/HHMOob5.jpg)

En la parte inferior vemos la pestaña `+ New Class` definimos nuestra nueva clase `Persona` de la siguiente manera:

```smalltalk
Object subclass: #Persona
	instanceVariableNames: '' 
	classVariableNames: ''
	package: 'Ministerio'
```

Es muy importante agregar el package donde va estar guardada la clase, esto nos ayudara a encontrarla y nos evita definirla en la base del sistema donde podemos llegar a sobre escribir alguna clase de nuestro sistema y romperlo. Una vez definida la clase le damos `ctrl+s` para guardar
Ahora si hacemos clic en `scoped view`podremos ver nuestro package `'Ministerio'` y al cliquear dentro de el veremos la clase `Persona` que acabamos de crear

![class-browser](https://i.imgur.com/EAlnMQO.png)

#### Métodos
Ahora supongamos que queremos definir los siguientes métodos a nuestra clase:

 - **nombre** -> nos permite setear un nombre
 - **apellido** -> nos permite setear el apellido
 - **nombreCompleto** -> nos devuelve el nombre completo de la persona.

Primero debemos definir en nuestra clase nuestras variables de instancia, es decir las variables que van a guardar el estado del objeto, entonces definimos `instanceVariableNames: 'nombre apellido'` y damos `ctrl +s` para actualizar los cambios en nuestra clase

```smalltalk
Object subclass: #Persona
	instanceVariableNames: 'nombre apellido' 
	classVariableNames: ''
	package: 'Ministerio'
```

Ahora en el **System browser** cliqueamos en nuestra clase y vemos lo siguiente:
![definiendo metodos](https://i.imgur.com/bJOV8li.png)

> debemos ver que estén seleccionados **Inst. side** y  **Methods**.

Debajo en la pestaña `+Inst.side methods` reemplazamos la plantilla que nos da por defecto y escribimos nuestro método `nombre`

```smalltalk
"empezamos por el nombre del metodo seguido de un parametro que recibe en este caso unNombre"
"luego asigamos a nuestra variable nombre de instancia que habiamos definido anteriormente el parametro unNombre"
nombre: unNombre 
	nombre := unNombre 
```

Damos `ctrl+s` para guardar nuestro método

de manera análoga definimos el método `apellido`

```smalltalk
	apellido: unApellido
		apellido := unApellido.
```

por ultimo cliqueando nuevamente en la pestaña `+Inst side methods`definimos el método `nombreCompleto`

```smalltalk
"definimos el nombre del metodo y retornamos una concatenacion del nombre y el apellido"
	nombreCompleto
		^ nombre , ' ', apellido .
```
A diferencia de los otros métodos, este no recibe ningún parámetro y usamos el carácter `^` para indicar que vamos a retornar un valor, esto es muy similar a lo que en otros leguajes se conoce como `return` el objeto `,` nos permite concatenar el **nombre** y el **apellido**.

Ahora podemos ver que nuestro **System browser** se actualizo con los nuevos métodos `apellido:`  `nombre:` y  `nombreCompleto` , también vemos a la izquierda que se crearon los paquetes de métodos `accessing` y `as yet unclassified` 
![métodos definidos](https://i.imgur.com/G94OloK.png)


Ahora podemos ejecutar el siguiente código en el **Playground**:

```smalltalk
| persona |

persona := Persona new.
persona nombre: 'Pedro'.
persona apellido: 'Perez'.

Transcript show: persona nombreCompleto.
```

debemos ver en nuestro `Transcript` el mensaje 

    Pedro Perez

#### Constructores en Smalltalk
Los constructores nos sirven para definir el estado inicial de un objeto luego de enviar el mensaje `new`
Supongamos que tenemos la clase `NumeroComplejo`  y  tiene los atributos `parteReal y parteImaginaria`


  Instanciamos un  objeto de la misma:
```smalltalk
"Constructores en pharo"
|n|
n:= NumeroComplejo new.
```
Al chequear el objeto que se creo veremos que los atributos se encuentran en `nil` en su estado inicial
![constructores 1](https://i.imgur.com/Jyeqau2.png)

Pero supongamos que queremos que al crear el objeto la parte real e imaginaria sean 0, entonces para  tener esa inicialización nos valemos del método **initialize** que se va ejecutar después de que el objeto se crea y nos permite inicializar los valores por defecto de los atributos del objeto.
Dentro de nuestra clase creamos el método ** initialize**
```smalltalk
"llamamos a super para darle chance a la clase base de que ejecute sus inicializaciones y luego inicializamos nuestros atributos"
 initialize
super.
"hacemos nuestras inicializaciones "
  parteReal:=0.
  parteImaginaria:=0.
```

ahora vemos que al crearse el objeto esta inicializado como queríamos

![constructores 2](https://i.imgur.com/8QcWCAo.png)

### Colecciones en Smalltalk
Un resumen 
  
```smalltalk
"Colleciones de Objetos"
|misNumeros subIndice tam exists elemento|

"Instanciamos un objeto de la coleccion"
misNumeros:= OrderedCollection new.
"agregamos elementos"
misNumeros add:9.
misNumeros add:4.
misNumeros add:5.
misNumeros add:3.
misNumeros add:1.
misNumeros add:89.
misNumeros add:12.

"Nos devuelve el indice de un elemento dentro de la coleccion- el primero que encuentra"
subIndice:= misNumeros indexOf:9. 

"Tamaño de una coleccion"
tam:= misNumeros size.

"Accedemos a un elemento especifico de la coleccion"
elemento:= misNumeros at:2.

"Remueve el primer elemento de la coleccion y guarda la referencia en la variable"
elemento := misNumeros removeFirst.

"Remueve el ultimo elemento de la coleccion y guarda la referencia en la variable"
elemento := misNumeros removeLast

"Chequea si un elemento se encuentra en la collecion"
exists:= misNumeros includes:anObject

```

### Exceptions
//en progreso
###  Pruebas  Automatizadas con SUnit
//en progreso
#### Pruebas Unitarias
Son aquellas que verifican una pequeña funcionalidad de nuestro código, son pruebas que evalúan la funcionalidad de un objeto de manera aislada.
Para poder estructurar una prueba unitaria la dividimos en 3 partes:

 - **Arrange**: Se establecen todas las precondiciones necesarias, i.e. declarar variables, instanciar objeto etc.
 - **Act**: Se envía el mensaje sobre el objeto que queremos testear.
 - **Assert**: Se verifica  que el resultado de la prueba sea el esperado

#### Pruebas Integración

