

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
Un sistema smalltalk esta compuesto por  

IDE
entorno de desarrollo
LENGUAJE
IMAGEN
se encarga de guardar la copia de nuestros objetos 
MAQUINA VIRTUAL
se encarga de ejecutar el sistema


#### Descarga e instalación de Pharo
>en progreso


##### libros pharo
http://books.pharo.org/

##### Curso pharo
https://mooc.pharo.org/

####  Conceptos Básicos
	### clase
	### instancia de clase
	### mensaje
	### herencia

La programación en SmallTalk consiste en crear clases, crear instancias y especificar la secuencia de mensajes entre objetos
	
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
 

##### Hola mundo en SmallTalk

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
 "ejemplo Asignacion"
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
