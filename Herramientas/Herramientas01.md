## RAPTOR Avalonia es la edición multiplataforma del intérprete educativo de diagramas de flujo RAPTOR. Permite a estudiantes crear, visualizar y ejecutar algoritmos paso a paso sin lidiar con sintaxis compleja, funcionando de forma nativa en Windows, macOS y Linux.
### Características principales
- **Multiplataforma real**. Desarrollado sobre el framework Avalonia UI y .NET, elimina la limitación histórica de depender únicamente de Windows.
- **Ejecución visual**. Ilumina cada símbolo del diagrama en tiempo real mientras muestra los valores de las variables en el panel lateral y los resultados en la Master Console.
- **Modos de aprendizaje**. Soporta el modo Novato (espacio de trabajo básico) e Intermedio (uso de subdiagramas, procedimientos, paso de parámetros y recursividad), aunque no incluye el modo Orientado a Objetos de la versión clásica de Windows.
- **Formato de archivos**. Guarda los proyectos en formato moderno .rap (basado en XML). Si tienes archivos antiguos en formato binario, debes cambiarles la extensión a .oldrap antes de abrirlos para migrarlos.
###  Descarga e instalación 
1. **Requisitos previos**. Necesitas tener instalado el entorno de ejecución .NET Runtime 8.0 en tu computadora.
2. **Descarga oficial**. Ingresa a la página oficial de RAPTOR y elige el instalador correspondiente a tu sistema operativo (instalador para Windows, paquete para Mac o archivo ZIP para Linux).
3. **Descarga oficial**. Ingresa a la página oficial de RAPTOR y elige el instalador correspondiente a tu sistema operativo (instalador para Windows, paquete para Mac o archivo ZIP para Linux).

## Flowgorithm es una herramienta educativa gratuita para Windows diseñada para crear, probar y ejecutar algoritmos mediante diagramas de flujo antes de escribir código en un lenguaje tradicional.
### Características principales
- **Aprendizaje visual**. Permite construir la lógica de un programa conectando bloques gráficos (variables, entradas, salidas, condicionales If, ciclos While, For y funciones) sin preocuparse por errores de sintaxis como llaves o puntos y coma
- **Ejecución paso a paso**. Al correr el diagrama, resalta cada símbolo conforme se ejecuta, muestra los resultados en una consola integrada y despliega una ventana de vigilancia (Variable Watch) con el valor en tiempo real de cada variable.
- **Traducción automática a código**. Incluye un visor que convierte el diagrama de flujo en tiempo real a más de 18 lenguajes de programación reales (como Python, C++, C#, Java, JavaScript y PHP), ayudando a los estudiantes a entender cómo se traduce su lógica gráfica a código escrito.
- **Tipado estricto**. A diferencia de otros programas similares como RAPTOR, obliga a declarar explícitamente el tipo de dato de cada variable (Integer, Real, String, Boolean), lo que facilita la transición posterior hacia lenguajes tipados como C++ o Java.
### Disponibilidad y formato
- **Sistema operativo**. Está desarrollado de forma nativa únicamente para Windows (en macOS y Linux requiere ejecutarse mediante herramientas como Wine o máquinas virtuales).
- **Formato de archivo**. Guarda sus proyectos en archivos .fprg con estructura interna basada en XML.

----
## Formatos .rap y .fprg
Ambos formatos (.fprg y .rap) son archivos XML##, pero su arquitectura interna es muy distinta. Mientras que Flowgorithm utiliza un árbol XML sencillo basado en bloques anidados, RAPTOR Avalonia serializa directamente sus objetos de memoria mediante DataContractSerializer de .NET (incluyendo referencias circulares z:Id/z:Ref, espacios de nombres de C# y coordenadas geométricas).

### Diferencias clave entre ambos formatos
- Declaración de variables. Flowgorithm exige nodos <declare> con tipo de dato estricto; RAPTOR infiere el tipo dinámicamente al asignar un valor y ignora las declaraciones vacías
- Lógica de los bucles (While y For). En Flowgorithm, un ciclo While se repite mientras la condición sea verdadera; en RAPTOR, el bucle Loop termina cuando la condición de salida se vuelve verdadera (por lo que toda condición While debe invertirse con not (...)).
- Sintaxis de expresiones. Flowgorithm usa &&, ||, ! y & para concatenar texto, mientras que RAPTOR utiliza and, or, not y +.

---

## El código fuente en C# de RAPTOR Avalonia es completamente de código abierto (open source) y está alojado en el repositorio oficial carlislemc/RAPTOR_Avalonia_MVVM en GitHub, desarrollado por su creador Martin Carlisle.

# Trabajo para el INSTRUCTOR

Construcción de un TRANSPILER .fprg a .rap

### Ventajas para el instructor de tener el código fuente disponible
- **Inspección exacta del modelo de datos***. Puedes revisar directamente las clases en C# (como Oval, Rectangle, Parallelogram, IF_Control y Loop) para ver todos los atributos marcados con [DataContract] y [DataMember] que exige el archivo .rap.
- **Creación de un generador nativo en C#**. En lugar de construir el XML manualmente, se puede importar las clases del proyecto en una pequeña aplicación de consola en C# (.NET), instanciar los objetos del diagrama en memoria y llamar directamente a **DataContractSerializer** para que genere un archivo .rap 100 % válido sin errores de esquema.
- **Extensión directa de la herramienta**. Si se desea integrar la importación de archivos .fprg dentro de la misma interfaz gráfica de RAPTOR Avalonia, se puede compilar una propia versión agregando una opción en el menú File -> Import Flowgorithm.
---

## Construcción de una herramienta didáctica .fprg -> .rap
### IDE USADO 

Visual Studio Code con C# Dev Kit









