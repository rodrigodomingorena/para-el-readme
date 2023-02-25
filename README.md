# Mi primer sitio con JavaScript: [Sauce | Restaurante de Tradición][index-page]

En el año 2021 comencé a dar mis primeros pasos en el mundo del desarrollo web aprendiendo las tecnologías y prácticas básicas para desarrollar sitios estáticos. Este proceso de aprendizaje se ve reflejado en lo que es mi [primer proyecto][mi-primer-sitio-repo]. Si no lo conocés, recomiendo que le eches una mirada, aunque sea rápida, para poder tener un mejor contexto de dónde es que viene y el por qué de este nuevo proyecto.

Este es una continuación de aquel primer sitio estático que tanto me ayudó a llevar a la práctica y afianzar los conocimientos de aquellas herramientas que iba estudiando. ¿Cuál es la diferencia? Como habrás notado en el título de esta introducción, ahora dicho sitio está desarrollado con funcionalidades dinámicas gracias a que en el transcurso del año 2022 tuve la oportunidad de comenzar a introducirme en el aprendizaje de JavaScript. Este proceso fue muy parecido al llevado a cabo en la realización de aquel primer proyecto.

Los recursos principales que utilicé para esta introducción a JavaScript fueron, con amplia diferencia, dos: [El tutorial de JavaScript Moderno][js-info] y [*MDN Web Docs*][MDN]. El primero fue una gran hoja de ruta que me guió a través de las múltiples partes fundamentales a incorporar en el proceso de aprendizaje de este lenguaje. A su vez, los contenidos me parecieron extremadamente pedagógicos y de una minuciosidad que no encontré en casi ningún otro recurso disponible para principiantes. Así es que me dio las herramientas necesarias para poder comenzar a entender y llevar a la práctica gran parte de sus características y funcionalidades principales. Por otro lado, el segundo me sirvió como una documentación mucho más técnica que me ayudó a completar el «mapa conceptual» del lenguaje en partes en las cuales [El tutorial de JavaScript Moderno][js-info] no ahondaba debido a su enfoque más pedagógico, recién mencionado, y no tan técnico al estilo documentación como sí lo es [*MDN Web Docs*][MDN].

En fin, en este trayecto comprendí que tenía la suerte haber desarrollado un primer proyecto lo suficientemente grande al cual podía dotarlo de muchísimas funcionalidades a través de JavaScript. Realmente las posibilidades son infinitas. Es así que aproveché esta base que es el proyecto «[Mi primer sitio][mi-primer-sitio-repo]» para refactorizarlo, convirtiéndolo en un sitio web dinámico en cuyo proceso iba a terminar de incorporar gran parte de las características que he ido aprendiendo este último año.

Ahora bien, ¿por qué un sitio web desarrollado con Vanilla JavaScript y no con una librería o *framework* de los que son usados actualmente? La raíz de esta decisión es la misma por la cual desarrollé un primer sitio totalmente estático: el objetivo principal fue estudiar, aprender y entender de la forma más consistente posible las bases del lenguaje de programación JavaScript y su estrecha interrelación con los navegadores web. Una vez comenzado a cumplir este objetivo (JavaScript es gigante, imposible abarcarlo todo en un proyecto de estudio como este) me adentraré en el aprendizaje de una librería o *framework* de desarrollo (muy probablemente [React JS][react]) para así poder dar un paso más en mi camino a convertirme en un desarrollador *front-end*.

A continuación voy a detallar algunas partes de este proyecto para que al momento de explorar el repositorio puedas tener un acercamiento más ameno a sus contenidos.

## Índice de contenidos
+ [Refactorización de componentes](#refactorización-de-componentes)

## Refactorización de componentes

Como mencioné en la introducción, me encontré en la afortunada situación de tener un primer proyecto como base lo suficientemente grande que me daría la oportunidad de experimentar con él para poder aplicar múltiples funcionalidades a través de JavaScript. Sin embargo, esto no significa que tomé el código estructural del primer proyecto y simplemente le agregué unos cuantos archivos «.js» para dotarlo de dinamismo.

En su lugar, este proceso comenzó con el intento de refactorizar cada parte de aquella estructura propensa a ser mejorada. Esto lo realicé atendiendo a diferentes criterios que tuve la oportunidad de afianzar y comprender con mayor profundidad luego de un año más de estudio. Considero que en el primer proyecto estos criterios fueron, o bien logrados a medias o directamente desatendidos por mi falta de experiencia y práctica.

Alguno de los criterios principales a tener en cuenta en este nuevo proyecto fueron los relacionados a la escalabilidad, lograr una estructura más atomizada e independiente entre cada una de sus partes, ajustar la arquitectura de directorios de Sass a estas nuevas estructuras, corregir ciertas denominaciones de clases basadas en [BEM][bem] para conseguir manipular de forma más óptima el DOM, lograr un código HTML lo más limpio posible de clases innecesarias que dificulten su lectura y entendimiento, entre otros.

Obviamente, estos casos se dan en mayor o menor medida a lo largo de todo el proyecto, desde componentes extremadamente grandes y complejos heredados del primero y posteriormente atomizados e independizados de una forma más óptima en este, hasta otros que casi no necesitaron modificación alguna debido a que su estructura ya se encontraba lo suficientemente optimizada para ser utilizada. Si conocés el proyecto «[Mi primer sitio][mi-primer-sitio-repo]», seguramente al explorar los archivos HTML y CSS/Sass de este nuevo proyecto reconocerás más fácilmente estos cambios y mejoras enumeradas.

A modo de ejemplo, a continuación menciono un caso de refactorización que necesitó abarcar criterios tales como la escalabilidad, la previsibilidad de entrada de datos de gran longitud, adición de nuevas funcionalidades, mejores denominaciones de clases para su manejo tanto en CSS como en JavaScript, entre otros.

### [Nutritional Info][nutritional-info]

+ #### Adición de opciones de cantidad y unidades de peso personalizadas

  En el primer proyecto, el usuario solamente contaba con una información nutricional estática [cada 300 gramos de alimento][nutritional-info-static-grams]. En este nuevo desarrollo se le da la posibilidad de introducir una cantidad numérica personalizada además de poder elegir qué tipo de unidad de peso representa dicha cantidad. En esta instancia se contemplan tres tipos de unidades: gramos, kilogramos y platos (donde cada plato equivale a 300 gramos).
  
  Naturalmente, esta refactorización implicó un aumento de la complejidad del subcomponente [Main][nutritional-info-main] del [Nutritional Info][nutritional-info]. Aun así, se logró mantener su independencia, además de que se prevé un crecimiento futuro del proyecto pudiéndose agregar cuantas opciones de unidades de peso hagan falta, como se puede visualizar en los siguientes ejemplos.
  
  > Animación que muestra el subcomponente Main del Nutritional Info con las nuevas opciones disponibles para el usuario.

  ![Opciones de cantidad y unidades de peso disponibles para el usuario](./assets/media/readme/refactor/gif/nutritional-info-main-options.gif "Opciones de cantidad y unidades de peso disponibles para el usuario")
  
  > Animación que muestra la capacidad del subcomponente Main de albergar cuantas opciones de unidades de peso sean necesarias en caso de necesitar incorporar alguna nueva en el futuro.

  ![Capacidad de escalar cantidad de opciones de unidades de peso](./assets/media/readme/refactor/gif/nutritional-info-main-future-options.gif "Capacidad de escalar cantidad de opciones de unidades de peso")
  
+ #### Soporte para entrada de datos de gran longitud
  
  En mi primer sitio, al tratarse de un desarrollo estático y, por ende, teniendo cierta previsibilidad de los datos a ser presentados, cometí el error de no contemplar la posibilidad de que dichos datos fuesen extremadamente grandes. En consecuencia, esto rompería por completo el diseño y maquetación del componente.
  
  En esta ocasión, al haberle dado la posibilidad al usuario de que decida él mismo la extensión de los datos a ser presentados, me vi obligado a tener presente este escenario que en aquella ocasión fue ignorado. Es así que dichos errores fueron abordados y posteriormente arreglados, dándole la posibilidad al usuario de poder ingresar datos de una longitud arbitraria sin que eso signifique que el componente se vea afectado en su presentación.
  
  > Animación que muestra el componente [Nutritional Info][info-nutricional] en el proyecto «[Mi primer sitio][mi-primer-sitio-repo]» y cómo al forzar la longitud de los datos presentados, se rompe el diseño y la maquetación.
  
  ![Rotura del diseño y maquetación para datos de gran longitud](./assets/media/readme/refactor/gif/nutritional-info-overflow-break.gif "Rotura del diseño y maquetación para datos de gran longitud")
  
  > Animación que muestra el componente [Nutritional Info][nutritional-info] refactorizado y cómo al forzar la longitud de los datos presentados, el diseño y la maquetación se mantienen.

  ![Soporte del diseño y maquetación para datos de gran longitud](./assets/media/readme/refactor/gif/nutritional-info-overflow-fixed.gif "Soporte del diseño y maquetación para datos de gran longitud")
  
   Obviamente, es muy difícil que el usuario tenga un interés genuino en ingresar una cantidad de, por ejemplo, kilogramos tan grande que haga que el recuento de calorías y gramos desborde los contenedores. Aun así, es un caso del que hay que estar prevenido y tratar de manejarlo para evitar errores y renderizados defectuosos.


























[index-page]: https://rodrigodomingorena.github.io/mi-primer-sitio-con-js/
[mi-primer-sitio-repo]: https://github.com/rodrigodomingorena/mi-primer-sitio

[nutritional-info]: ./pages/plate.html#L179
[nutritional-info-static-grams]: https://github.com/rodrigodomingorena/mi-primer-sitio/blob/master/pages/plato-1.html#L175
[nutritional-info-main]: ./pages/plate.html#L182

[info-nutricional]: https://github.com/rodrigodomingorena/mi-primer-sitio/blob/master/pages/plato-1.html#L165




[js-info]: https://es.javascript.info/
[mdn]: https://developer.mozilla.org/en-US/
[react]: https://beta.reactjs.org/
[bem]: https://github.com/rodrigodomingorena/mi-primer-sitio#metodolog%C3%ADa-bem
