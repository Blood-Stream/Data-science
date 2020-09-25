# Bloodstream Data Science Documentation

## Introducción al Algoritmo de Recomendaciones

El algoritmo de recomendaciones de Bloodstream crea las mejores experiencias de usario para sus miembros. La siguiente arquitectura de datos es la que entrega esta experiencia, así como apoyo rápido. De tal forma que puede lidiar con grandes volúmenes de data, siendo responsivo a las interacciones de los usuarios y facilitar recomendaciones:

![Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Untitled.png](Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Untitled.png)

El diagrama esta dividido en tres partes:

***Tareas offline (Model training)***: donde se guarda la data para procesamiento offline.

***Tareas online (UX)***: que responde en tiempo real a los eventos e interacciones del usuario.

***Tareas nearline (Backup):*** que puede ejecutar tareas online, sin tener la responsabilidad directa de funcionar en tiempo real. 

![Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/DS_Bloodstream_Algorithm_-_distribution.jpg](Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/DS_Bloodstream_Algorithm_-_distribution.jpg)

## Computación Online (UX)

Con computación online, podemos responder rápido a los eventos y el uso reciente del cliente. Por ejemplo, generando una galería de videojuegos que se le recomiendan al usuario. Estos componentes están sujetos a disponibilidad y tiempo de respuesta que se entrega al cliente. 

Este nivel dentro del diagrama permite tener varias fuentes de datos disponibles, pero requiere de soporte de computación nearline y offline. 

## Computación Offline (Model Training)

La computación offline permite operar con más opciones algorítmicas. Por ejemplo, acá se generan estadísticas periódicas de los videojuegos mejores valorados y métricas. Este nivel requiere menos tiempo de respuesta que su par online. Nuevos algoritmos pueden ser desplegados a producción sin muchos requerimientos en el desempeño. 

![Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Offline_jobs.jpg](Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Offline_jobs.jpg)

Esta infraestructura permite realizar experimentos dentro de un ambiente ágil, sin comprometer la experiencia de usuario. Así mismo, permite almacenar datos y entrenar al modelo de recomendaciones.

## Computación Nearline (Backup)

La computación nearline permite comprometer los dos módulos previos. En gran medida, este backup funciona como su par online. Sin embargo, no está a cargo de mandar resultados al cliente. Más bien, los almacena para permitir un modelo asíncrono. 

Este nivel sirve para responder a eventos de usuario. Por ejemplo, guarda información como la valoración reciente de usuarios. 

## Machine Learning

La mayor parte del machine learning se realiza en la parte offline de la arquitectura. Esto permite que las tareas puedan ser programadas para ser ejecutadas periódicamente, ofreciendo un modelo asíncrono entre el servidor y el cliente. 

En este sentido, tenemos dos elementos a observar:

- ***Model training***: recolectamos data disponible y aplicamos algoritmos de machine learning para fijar parámetros. Este modelo es programado y almacenado para computación posterior. Aunque la mayoría de los modelos serán entrenados offline, se utilizan también algunos algoritmos de machine learning online.
- ***Batch computation:*** usamos modelos existentes y los alimentamos con la data correspondiente, generando resultados que serán mostrados posteriormente en las recomendaciones.

Para las funciones de estos modelos, se necesitarán utilizar datos limpios que son generados por las queries de la base de datos. Las queries deben de poder correr sobre grandes cantidades de datos y de forma distribuida. 

Hecho lo anterior, usamos un mecanismo para publicar los resultados:

1. Notificación al usuario cuando la recomendación está lista. 
2. Soporte a varios repositorios. 
3. Manejo de errores, que permita monitoreo y alertas

## Filtros Colaborativos

En principio se implementan ***filtros colaborativos*** para ******los sistemas de recomendación. Estos se basan en el hecho de que si hay dos personas (X y Y) en un mismo sistema y tienen gustos similares, entonces recomendarle a X juegos que le gusten a Y será de gran relevancia, en contraste a simplemente darle una opción aleatoria.

Contando con una gran cantidad de datos se usa algoritmos de recomendación rápida y eficiente. Por ejemplo: guardando gustos en una matriz binaria.

## Señales y Modelos

Nuestro modelo maneja tres tipos de inputs:

- ***Modelos***: archivos de parametros que han sido entrenados offline.
- ***Datos:*** información procesada que ha sido guardada en la base de datos.
- ***Señales***: información nueva para los algoritmos, que se obtiene del usuario en tiempo real.

![Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Sings_models.jpg](Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Sings_models.jpg)

## Distribución de Datos y Eventos

Nuestro objetivo es convertir interacciones en información que ayude a mejorar la experiencia de usuario. Por ello, las interfaces no solo tienen una estrategia sólida de UX sino que recolectan data de la mayor cantidad de eventos. Por ejemplo, clics, búsquedas, vistas o likes. De tal forma que los eventos pueden ser agregados a una base de datos para nuestros algoritmos. 

![Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Event_data_distribution.jpg](Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Event_data_distribution.jpg)

En este sentido, los eventos son pequeñas unidades de tiempo e información que son procesadas y almacenadas para un análisis posterior. La arquitectura de recomendaciones depende de computación distribuida y el data flow manejado por sistemas de logging para las partes iniciales del proceso. 

## Resultados de Recomendaciones

Los algoritmos de machine learning tienen el objetivo de realizar recomendaciones personalizadas.  Estas son dadas directamente desde listas que han sido computadas anteriormente. Esto es resultado de una combinación entre recomendaciones hechas offline y listas post-procesadas con algoritmos que leen señales en tiempo real. 

![Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Recommendations.jpg](Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Recommendations.jpg)

Varios repositorios son almacenados offline y en el backup para ser consumidas al momento de las peticiones. El objetivo principal de las bases de datos no es almacenar datos, sino manejar requerimientos. 

## Últimas Observaciones

El fin de esta arquitectura de datos es usar algoritmos sofisticados de machine learning que permitan escalamiento y manejo de Big data. Permitiendo también innovación ágil y flexible. Todo esto para generar resultados rápidos a los datos y eventos generados por los usuarios. 

---