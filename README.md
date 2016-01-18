**Escuela Colombiana de Ingeniería**

**Arquitecturas de Software - ARSW**

***Taller – Reflexividad de los lenguajes.***

Se debe subir un avance al momento de terminar la sesión de laboratorio.

Se quiere desarrollar una herramienta que apoye la detección de cuellos de botella en aplicaciones (un tipo de ‘perfilamiento’). Para esto, se quiere que usted desarrolle una serie de anotaciones que permitan a los desarrolladores definir a qué métodos se les realizarán pruebas de desempeño, y luego, con una herramienta de línea de comando (similar a jUnit), ejecutar las operaciones indicadas, medir su tiempo de respuesta, y luego mostrar al usuario un listado con el tiempo tomado por cada una de las operaciones.

En esta primera versión, para que una clase pueda ser ‘perfilada’, debe implementar la interfaz ‘Perfilable’ e implementar sus métodos correspondientes, y sólo se soportarán pruebas de operaciones sin parámetros:

	/**
	* @obj retornar los nombres de los métodos que se pueden perfilar en esta aplicación
	* @return Un arreglo, sin elementos nulos, con los nombres de los métodos que se deben probar
	*/
	public String[] getTesteableMethodNames();

	/**
	* @obj retornar un arreglo con el mismo número de elementos de la propiedad 'testeableMethods',
	*      donde cada posición corresponde al número de veces que se deben ejectuar los métodos indicados
	*      en dicha propiedad (la correspondencia número de veces/método la da el índice)
	*/
	public int getTestCount();

 
**Parte I.**

1.	Haga un programa que funcione por línea de comando, y que reciba como parámetro el nombre de la clase que se va a probar. Por ejemplo, para perfilar una clase  (que hereda la interfaz indicada), la herramienta se debe poder invocar como:

```
~shell>  mvn exec:java -Dexec.mainClass="edu.eci.pdsw.view.Perfilator"   -Dexec.args="paquete1.paquete2.ClaseAProbar"
```

Para hacer esto, utilice el API de Reflection de manera que se pueda:

	a.	Verificar que la clase implementa la interfaz indicada. En caso de que no, mostrar un mensaje de error.
	
	b.	En caso de que sí implemente la interfaz, usar los métodos implementados de dicha interfaz para identificar qué métodos se quieren probar de la clase.
	
	c.	Crear una instancia de la clase, y ejecutar en la misma los métodos indicados, el número de veces indicado, midiendo el tiempo total que toma su ejecución.
	
	d.	Al terminar, el programa debe imprimir los nombres de los métodos ejecutados, el número de veces cuya ejecución fue repetida, y el tiempo total tomado.

2.	Haga los ajustes que sean necesarios para que la clase ‘ClaseAProbar’ suministrada se pueda perfilar. Luego, realice la medición para la misma.

**Parte II.**

La primera versión del perfilador tiene un defecto importante: hace perder legibilidad al código de las clases ‘perfilables’, ya que obliga a que éstas implementen métodos que no tienen nada que ver con el concepto al cual están asociadas. Por esto, se quiere que desarrolle una segunda versión del perfilador (no borre la anterior!) que use como metadatos anotaciones (usted decide si son anotaciones de clase o de método, y cómo usarlas, dependiendo de qué considere más práctico). 

En esta nueva versión, para poder perfilar una clase, la misma ya no debe depender de la interfaz ‘Perfilable’, sino utilizar de alguna manera la anotación creada. Tenga en cuenta que se deben conservar las mismas características de la primera versión: se puede elegir qué métodos se perfilarán, y cuantas veces se repetirá la ejecución de los mismos.


