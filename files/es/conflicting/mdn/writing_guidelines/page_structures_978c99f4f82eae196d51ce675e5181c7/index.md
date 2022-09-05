---
title: Macros
slug: >-
  conflicting/MDN/Writing_guidelines/Page_structures_978c99f4f82eae196d51ce675e5181c7
tags:
  - Estructuras
  - Guide
  - Guía
  - Kuma
  - KumaScript
  - MDN Meta
  - Structures
  - TopicStub
translation_of: MDN/Structures/Macros
original_slug: MDN/Structures/Macros
---
{{MDNSidebar}}

La plataforma {{web.link("/es/docs/Project:MDN/Kuma#Herramientas_y_tareas", "Kuma")}} en la que se ejecuta MDN proporciona un potente sistema de macros, {{web.link("/es/docs/MDN/Contribute/Tools/KumaScript", "KumaScript")}}, estas te permiten hacer una amplia variedad de cosas de forma automática. Este artículo proporciona información sobre cómo invocar macros de MDN dentro de los artículos.

La {{web.link("/es/docs/MDN/Contribute/Tools/KumaScript", "guía de KumaScript")}} profundiza en cómo usar macros en MDN, por lo que esta sección es más una breve descripción general.

## Cómo se implementan las macros

Las macros en MDN se implementan usando código {{web.link("/es/docs/Web/JavaScript", "JavaScript")}} ejecutado por el servidor, interpretado usando [Node.js](https://nodejs.org/es/). Además de eso, tenemos una serie de bibliotecas que hemos implementado que brindan servicios y funciones orientados a wiki para permitir que las macros interactúen con la plataforma wiki y su contenido. Si estás interesado en obtener más información, consulta {{web.link("/es/docs/MDN/Contribute/Tools/KumaScript", "Guía de KumaScript")}}.

## Usar una macro en el contenido

Para usar realmente una macro, simplemente encierra la llamada a la macro entre un par de llaves dobles, con sus parámetros, si los hay, entre paréntesis; es decir:

```
\{{nombremacro(lista-de-parametros)}}
```

Algunas notas sobre las llamadas de macro:

- Los nombres de macro distinguen entre mayúsculas y minúsculas, pero se intentas corregir los errores comunes de uso de mayúsculas; puedes usar todo en minúsculas incluso si el nombre de la macro usa mayúsculas dentro de él, y puedes poner en mayúscula una macro cuyo nombre normalmente comienza con una letra minúscula.
- Los parámetros están separados por comas.
- Si no hay parámetros, puedes omitir los paréntesis por completo; `\{{nombremacro()}}` y `\{{nombremacro}}` son idénticos.
- Los parámetros numéricos pueden estar entre comillas o no. Depende de ti (sin embargo, si tienes un número de versión con varios decimales, debe estar entre comillas).
- Si recibes errores, revisa tu código detenidamente. Si aún no puedes averiguar qué está pasando, consulta {{web.link("/es/docs/MDN/Kuma/Troubleshooting_KumaScript_errors", "Solución de errores de KumaScript")}} para obtener ayuda.

Las macros están almacenadas en caché; para cualquier conjunto de valores de entrada (tanto parámetros como valores del entorno, tal como la URL para la que se ejecutó la macro), los resultados se almacenan y reutilizan. Esto significa que la macro solo se ejecuta realmente cuando cambian las entradas.

> **Nota:** Puedes forzar la reevaluación de todas las macros de una página si fuerzas la actualización de la página en tu navegador (es decir, una recarga).

Las macros pueden ser tan simples como insertar un bloque de texto más grande o intercambiar contenido de otra parte de MDN, o tan complejas como crear un índice completo de contenido buscando en partes del sitio, estilizando el resultado y agregando enlaces.

Puedes leer sobre las macros más utilizadas en {{web.link("/es/docs/MDN/Contribute/Structures/Macros/Commonly-used_macros", "Página de macros usadas comúnmente")}}; también, hay una {{web.link("/es/docs/templates", "lista completa de todas las macros")}}. La mayoría de las macros tienen documentación incorporada, como comentarios en la parte superior.