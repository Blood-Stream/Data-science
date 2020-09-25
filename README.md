# Bloodstream Data Science Documentation

## Introduction to the Recommendation Algorithm


Bloodstream recommendation algorithm creates the best user experiences for its users. The following data structure is behind it, allowing to execute fastly. In this way it's capable of dealing with large chunks of data, being resposive to interactions while easing recommendations:

![Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Untitled.png](Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Untitled.png)

The diagram is divided in three parts:

***Tareas offline (Model training)***: where data is storaged for later offline processing.

***Tareas online (UX)***: that responds in real time to users' events and interactions.

***Tareas nearline (Backup):*** that can execute online tasks, without having the direct duty to function in real time.

![Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/DS_Bloodstream_Algorithm_-_distribution.jpg](Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/DS_Bloodstream_Algorithm_-_distribution.jpg)

## Online Computing

With online computing we can respond fastly to events and the recent client's interaction. For instance, generating a videogames gallery for user recommendation sake. this components are subject to availability and time response that is delivered to the client. 

This level within the diagram allows to have several data sources, but requires support from offline and nearline computation. 

## Offline Computation (Model Training)

Offline computation allos to operate more algorithmic options. For instance, here periodic statistics and metrics of the the best-rated videogames are generated. This level requires less response time compared to the online side. New algorithms can be deployed withouch much performance requirements. 

![Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Offline_jobs.jpg](Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Offline_jobs.jpg)

This infraestructure allows to perform experiments within an agil environment without compromising the user experience. Likewise, allows to storage data and train recommendation models. 

## Computación Nearline (Backup)

Nearline computation allows to compromise the latter modules. In a way, it's a backup for the online side. However, it's not in charge of sending results to the client side. Rather, it storages data to allow an async model. 

This level serves to respond to users' events. For instance, it storages data as recent user's rating. 

## Machine Learning

Most of machine learning happens on the offline side of the architecture. This allows tasks to be scheduled to be exectured periodically, generating an async model amid the server and the client. 

In this sense, we have to models:

- ***Model training***: we collect data and apply it to machine learning algorithms to fix parameters. This model is programmed and storaged for later computation. Although most models are trained offline, online algorithms are also executed online.
- ***Batch computation:*** we use existing models and feed them the corresponding data, generating results that are going to be latter delivered. 

For the functionalities of these mdoels, we need clean data to generate queries in the database. Queries should run large data on a distributed fashion. 

With this, we use a mechanism to publish results:

1. User notifications when the recommendation is ready.
2. Support to several repositories.
3. Error handing, that allows monitoring and alerts.

## Signals and Models

Our model manages three input types:

- ***Modelos***: trained parameter files.
- ***Datos:*** processed data that is storaged in the database.
- ***Señales***: data for algorithms, that is extracted from the user in real time.

![Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Sings_models.jpg](Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Sings_models.jpg)

## Data and Events Distribution

Our goal is to turn interactions into data that allows the best UX. For this purpose, interfaces not only follow a solid UI strategy byt collect data from the largest number of events. For instance, clicks, searches, visits or likes. this way, events can be added to the database for our algorithms. 

![Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Event_data_distribution.jpg](Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Event_data_distribution.jpg)


In this sense, events are short time and info units that are processed and storaged for later analysis. Recommendation architecture depends on distributed computation and data flow that is managed by the logging systems for the starting parts of the process. 

## Recommendation Results

Our machine learnign algorithms have the goal to generate personalized recommendations. These are given from lists that have been computed beforehand. This is result of the combinaiton amid offline recommendations and post-processed lists with algorithms that read signs in real time.

![Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Recommendations.jpg](Bloodstream%20Data%20Science%20Documentation%202364fb87b0584eb99afe52821e9382e9/Recommendations.jpg)

Several repositories are storaged offline and the backup is consuments at the time of requests. The main objective of the data bases is not only to storage data, but to manage requests. 

## Last Observations

El fin de esta arquitectura de datos es usar algoritmos sofisticados de machine learning que permitan escalamiento y manejo de Big data. Permitiendo también innovación ágil y flexible. Todo esto para generar resultados rápidos a los datos y eventos generados por los usuarios. 

The goal of this data architecture is to use sophistiated machine learning algorithms that allow escalation and Big data management, in order to trigger agile and flexible innovation. All the latter to generate fast data results and events generated by users.

---
