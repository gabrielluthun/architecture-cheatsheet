# L'architecture dans le milieu du développement 

## Table des matières
- [1. Introduction](#1-introduction)
   - [1.1 Notions clés](#11-notions-clés)
   - [1.2 Les différentes architectures](#12-les-différentes-architectures)
- [2. Architecture en tiers](#2-architecture-en-tiers)
   - [2.1 Architecture N-tiers](#21-architecture-n-tiers)

## 1. Introduction
### 1.1 Notions clés
**Architecture** : l'organisation dans laquelle les différents composants d'une application vont être séparés et vont communiquer entre eux

**Couche** : une couche est une organisation logique d'un projet **(front, back, BDD...)**
*Note : pour Docker, il faut une image par couche*

**Service** : grosses unités de fonctionnalités
**Microservice** : petites unités de fonctionnalités, n'ont **pas le droit de communiquer entre eux**, par souci d'interdépendance
*1 image Docker = 1 microservice*

La différence entre un service et un microservice est le nombre de composants qui le compose : un service peut se découper en microservices, comme si l'on découpait un **problème en plusieurs petits problèmes**

### 1.2 Les différentes architectures
**Architecture monolithique** : rapide à mettre en place, mais difficile à maintenir et à échelle
Avec le CI/CD, il faut essayer d'avoir un projet le plus léger possible

**Architecture 3-tiers** : HTML, CSS, JS dans le front, PHP dans le back, SQL dans la BDD (utilisation classique)
**Architecture n-tiers** : plusieurs couches, plusieurs serveurs (front, back, BDD...)

**Architecture SPA** : Single Page Application
*1 seule page HTML, CSS et JS, tout le contenu est servi par le serveur et injecté dans la page*

**Architecture orienté service** : compromis entre l'architecture monolithique et l'architecture microservice

*Pour aller plus loin :*
*- **SSR : Server Side Rendering** : le principe est de générer le HTML sur le serveur et de l'injecter dans la page*
*- **CSR : Client Side Rendering** : le principe est de générer le HTML sur le client (dans le navigateur)*

## 2. Architecture en tiers

### 2.1 Architecture N-tiers

*Chaque couche ne peut communiquer qu'avec les couches suivantes*

Voilà un schéma **explicatif** résumant l'architecture N-tiers :

![Architecture N-tiers](/assets/architecture-n-tier-schema.png)

#### Explication détaillée du schéma

Le schéma illustre le flux de données dans une architecture N-tiers typique :

1. **Côté Client (Front-end)**
   - Interface utilisateur (UI)
   - Envoie des requêtes HTTP vers le serveur
   - Reçoit et affiche les réponses

2. **Côté Serveur (Back-end)**
   - **Couche de Présentation (Controllers)**
     - Point d'entrée des requêtes HTTP
     - Gère les routes de l'API
     - Utilise des DTOs (Data Transfer Objects) pour :
       - Transformer les requêtes entrantes en objets métier
       - Transformer les objets métier en réponses
   
   - **Couche Business (Services)**
     - Contient la logique métier de l'application
     - Traite les données selon les règles métier
     - Orchestre les opérations entre présentation et persistance
     - Ne communique jamais directement avec la BDD
   
   - **Couche Persistance (Repository/DAO)**
     - Gère toutes les interactions avec la base de données
     - Convertit les objets métier en requêtes SQL
     - Transforme les résultats SQL en objets métier

3. **Base de Données**
   - Stockage permanent des données
   - Communique uniquement avec la couche de persistance

**Points clés :**
- Chaque couche a une **responsabilité unique** et bien définie
- La communication se fait uniquement de gauche à droite *(toujours sur le schéma)*
- Une couche ne peut communiquer qu'avec la couche **directement** en-dessous d'elle
- Les DTO **protègent** la logique métier en créant une barrière entre l'API et le code métier


