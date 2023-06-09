# Plantilla para TP Integrador usando JFlex y JCup (Java)

## Prerequisitos.

Para poder usar esta plantilla deberá instalar:
1.  [JDK 18](https://www.oracle.com/java/technologies/javase/jdk18-archive-downloads.html)

### Instalación en Windows
1. Bajarse [Windows x64 Installer](https://www.oracle.com/java/technologies/javase/jdk18-archive-downloads.html)
2. Setear JAVA_HOME como variable de entorno en variables del sistema ([Instructivo](https://docs.oracle.com/cd/E19182-01/821-0917/inst_jdk_javahome_t/index.html#:~:text=To%20set%20JAVA_HOME%2C%20do%20the,Program%20Files%5CJava%5Cjdk1.))
3. Corroborar que JAVA_HOME fue seteado correctamente abriendo la terminal de símbolos del sistema (command prompt) ejecuntando el siguiente comando:
```
echo %JAVA_HOME%
```

## Herramientas:

Este proyecto usa [JFlex](https://www.jflex.de/) como Analizador Léxico y [Cup](http://www2.cs.tum.edu/projects/cup/) como Analizador Sintáctico.
Este compilador generará código listo para correr en el procesador [DOSBox](https://www.dosbox.com/).
Toda la documentación referente a ambas herramientas la encontrará en las páginas adjuntas.

## Compilación.

Abrir una terminal en el directorio raíz del proyecto y correr el siguiente comando:

Para Linux/Mac:
```
./mvnw clean install
```


Para Windows:
```
./mvnw.cmd clean install
```

El mismo generará los ejecutables y correrá los tests.

## Ejecución.

Abrir una terminal en el directorio raíz del proyecto y correr el siguiente comando:

Para Linux/Mac:
```
./mvnw clean install -Drun-compiler
```


Para Windows:
```
./mvnw.cmd clean install -Drun-compiler
```

Dicho comando compilará el proyecto y luego correrá el script run.sh o run.bat (Para Unix o Windows respectivamente) presente en el directorio raíz.
Dichos scripts se pueden correr directamente desde la terminal siempre y cuando el proyecto se haya compilado primero.

## Archivo de prueba:

El mismo se encuentra en target/input/test.txt y es copiado del código fuente presente en src/main/resources/input/test.txt.
Agregar en este archivo todos los casos de prueba detallados en la consigna.

## Archivos Generados

En la carpeta target/output se generarán automáticamente los siguientes archivos:

- intermediate.code.txt
- symbol-table.txt
- final.asm

En la carpeta target/asm se copiarán todos los archivos necesarios para correr el programa fuente final, incluyendo el final.asm generado.
La carpeta target/asm contiene la herramienta DOSBox, junto con el ensamblador y el linker.
En ella encontrará un archivo assembler de ejemplo y un [README](src/main/resources/asm/readme.MD) con instrucciones de cómo correrlo.
La misma también contiene el script run.bat que ejecutará el programa generado por su compilador.

## Tests:

En la plantilla ya están incluídos dos casos de prueba automatizados y listos para ser corridos:

- LexerTest (Analizador Léxico)
- ParserTest (Analizador Sintáctico)

A tener en cuenta:
1. Los Tests vienen deshabilitados por defecto ya que las funcionalidades que son probadas no están implementadas aún.
2. Al tope de la clase está presente la annotation [@Disabled](https://howtodoinjava.com/junit5/junit-5-disabled-test-example/) para dicho propósito
3. Cada grupo podrá ir habilitando los tests a medida que vayan implementado las funcionalidades.
4. Vea los criterios de aprobación de cada entrega para ver qué tests deben funcionar en cada punto de control.
5. Cada grupo podrá agregar tests que considere apropiados a los tests ya provistos, sin remover ninguno de los test base.
6. Cada grupo deberá agregar al menos un test para cada uno de sus temas especiales.

# Trabajo Práctico Integrador de Lenguajes y Compiladores

## Consideraciones Generales

Es necesario cumplir con las siguientes consideraciones para evaluar el TP:

1. Cada grupo deberá desarrollar el compilador teniendo en cuenta:
   - Todos los temas comunes.
   - Los temas especiales asignados.
   - El método de generación intermedia asignado.
   - El profesor que le ha sido asignado.

Nota: Los grupos y sus respectivas asignaciones están listados en esta [planilla](https://docs.google.com/spreadsheets/d/1b51HqEtF7h6dG8lfSI5Ww22tkSWS7fM88WEWhBb_QRA/edit?usp=sharing).

2. Cada grupo deberá designar un integrante para el envío de los correos durante todo el cuatrimestre.
3. El TP deberá respetar la estructura provista en esta planilla y ser entregado a través de un enlace al repositorio de GitHub generado.
4. Para generar su propio repositorio GitHub seleccione la opción "Use this template".
5. Se fijan a continuación puntos de control con fechas y requerimientos determinados.


### Primera Entrega:

**Objetivo**: Realizar un analizador léxico y sintáctico con las herramientas provistas. 
El programa ejecutable deberá mostrar por pantalla las reglas sintácticas que va analizando el parser en base a un archivo de entrada (test.txt). 
Las impresiones deben ser claras. Las reglas que no realizan ninguna acción no deben generar salida.

La entrega 1.0.0 incluirá:

- El archivo lexer con la definición de todos los componentes léxicos.
- El archivo parser con la definición de la gramática del lenguaje y la lógica de generación de la tabla de símbolos.
- El archivo symbol-table.txt deberá contener la lista de variables y constantes con sus respectivos atributos.
- El archivo ejecutable lyc-compiler-1.0.0.
- El archivo de pruebas test.txt que contendrá ejemplos de todos los temas comunes y especiales (selecciones, ciclos anidados, temas especiales, verificación de cotas para las constantes, chequeo de longitud de los nombres de los identificadores, comentarios, etc).
  - Dicho archivo debe ser único (no enviar diferentes escenarios de prueba en diferentes archivos).
  - Las líneas de código que ejemplifican casos de error en tiempo de compilación deberán presentarse en el documento de manera comentadas y acompañadas de un mensaje descriptivo.

Nota: Los archivos requeridos ya son provistos/generados por la plantilla, lo que debe agregarse es la implementación de la funcionalidad en ellos.

##### Criterio de aprobación:
- Todos los casos de prueba presentes en la plantilla elegida deberán pasar.
- La tabla de símbolos debe generarse respetando la estructura descrita en la consigna.

Cree el tag 1.0.0 en su repositorio.

Envíe el enlace del tag generado del repositorio generado enviado a: lenguajesycompiladores@gmail.com

Asunto: NombredelDocente_GrupoXX (Ej Daniel_Grupo03, Eleazar_Grupo02, Facundo_Grupo15)

Fecha de entrega: 14/02/2023


### Segunda Entrega:

**Objetivo:** Realizar un generador de código intermedio utilizando el archivo parser generado en la primera entrega. El programa ejecutable deberá procesar el archivo de entrada (prueba.txt) y devolver el código intermedio del mismo junto con la tabla de símbolos.

La entrega 2.0.0 incluirá:

- El archivo lexer con la definición de todos los componentes léxicos.
- El archivo parser con la definición de la gramática del lenguaje y la lógica de generación de la tabla de símbolos.
- El archivo symbol-table.txt deberá contener la lista de variables y constantes con sus respectivos atributos.
- El archivo intermediate-code.txt y que contiene el código intermedio generado.
- El archivo ejecutable lyc-compiler-2.0.0.jar.
- El archivo de pruebas test.txt que contendrá ejemplos de todos los temas comunes y especiales (selecciones, ciclos anidados, temas especiales, verificación de cotas para las constantes, chequeo de longitud de los nombres de los identificadores, comentarios, etc).
    - Dicho archivo debe ser único (no enviar diferentes escenarios de prueba en diferentes archivos).
    - Las líneas de código que ejemplifican casos de error en tiempo de compilación deberán presentarse en el documento de manera comentadas y acompañadas de un mensaje descriptivo.

Nota: Los archivos requeridos ya son provistos/generados por la plantilla, lo que debe agregarse es la implementación de la funcionalidad en ellos.

##### Criterio de aprobación:
- El código intermedio debe generarse correctamente.
- Deben agregarse validaciones semánticas (Por ej: validación de tipos en asignación, variable ya declarada, etc.)

Cree el tag 2.0.0 en su repositorio.

Envíe el enlace del tag generado enviado a: lenguajesycompiladores@gmail.com

Asunto: NombredelDocente_GrupoXX    (Ej Daniel_Grupo03, Eleazar_Grupo02)

Fecha de entrega: 24/02/2023

### Entrega final

***Objetivo***: Realizar un compilador utilizando el archivo generado en la segunda entrega. 
El programa ejecutable deberá procesar el archivo de entrada (test.txt), compilarlo y ejecutarlo.

La entrega 3.0.0 incluirá:

- El archivo lexer con la definición de todos los componentes léxicos.
- El archivo parser con la definición de la gramática del lenguaje y la lógica de generación de la tabla de símbolos.
- El archivo symbol-table.txt deberá contener la lista de variables y constantes con sus respectivos atributos.
- El archivo intermediate-code.txt y que contiene el código intermedio generado.
- El archivo ejecutable lyc-compiler-3.0.0.
- El archivo de pruebas test.txt que contendrá ejemplos de todos los temas comunes y especiales (selecciones, ciclos anidados, temas especiales, verificación de cotas para las constantes, chequeo de longitud de los nombres de los identificadores, comentarios, etc).
    - Dicho archivo debe ser único (no enviar diferentes escenarios de prueba en diferentes archivos).
    - Las líneas de código que ejemplifican casos de error en tiempo de compilación deberán presentarse en el documento de manera comentadas y acompañadas de un mensaje descriptivo.
- El archivo assembler que se llamará final.asm
- El archivo por lotes run.bat que incluirá las sentencias necesarias para compilar con TASM y TLINK el archivo final.asm generado por el compilador

Nota: Los archivos requeridos ya son provistos/generados por la plantilla, lo que debe agregarse es la implementación de la funcionalidad en ellos.

##### Criterio de aprobación:
- El código assembler debe generarse correctamente.
- El programa de prueba debe ejecutarse sin problemas en DOSBox.

Cree el tag 3.0.0 en su repositorio.

Envíe el enlace del tag generado enviado a: lenguajesycompiladores@gmail.com

Asunto: NombredelDocente_GrupoXX    (Ej Daniel_Grupo03, Eleazar_Grupo02)

Fecha de entrega: 02/03/2023


## Temas comunes

Los temas comunes se describen [aquí](Temas%20Comunes.md)

## Temas especiales

Los temas especiales se describen [aquí](Temas%20Especiales.md)


## ¿Qué herramientas puedo usar para el Trabajo Práctico?

La cátedra provee plantillas para desarrollar el TP principalmente en Java o Kotlin.
Estas plantillas son completas: proveen casos de prueba, gestión de dependencias y uso de herramientas modernas.
Sin embargo, estamos abierto al uso de otras tecnologías.
El uso de otras herramientas requerirá un trabajo de investigación adicional al grupo/equipo que así lo decida, y mayor
autonomía en las particularidades de implementación (dado que los docentes no conocemos todas las herramientas y no podremos dar soporte
a cada una de ellas).

De igual forma, el esfuerzo de investigación de otras herramientas será tenido en cuenta positivamente en la evaluación definitiva.

Dejamos a continuación, las plantillas disponibles:


[Plantilla para TP Integrador usando JFlex y JCup - Java](https://github.com/Lenguajes-y-Compiladores-UnLaM/compiler-java)

[Plantilla para TP Integrador usando JFlex y JCup - Kotlin](https://github.com/Lenguajes-y-Compiladores-UnLaM/compiler-kotlin)

[Plantilla para TP Integrador usando Flex y Bison - C](https://github.com/Lenguajes-y-Compiladores-UnLaM/compiler-c)



