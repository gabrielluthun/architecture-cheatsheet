# L'architecture dans le milieu du développement 

## Table des matières
- [1. Introduction](#1-introduction)
   - [1.1 Notions clés](#11-notions-clés)
   - [1.2 Les différentes architectures](#12-les-différentes-architectures)

## 1. Introduction
### 1.1 Notions clés
**Architecture** : l'organisation dans laquelle les différents composants d'une application vont être séparés et vont communiquer entre eux

**Couche** : une couche est une organisation logique d'un projet **(front, back, BDD...)**
*Note : pour Docker, il faut une image par couche*

**Service** : grosses unités de fonctionnalités
**Microservice** : petites unités de fonctionnalités

### 1.2 Les différentes architectures
**Architecture monolithique** : rapide à mettre en place, mais difficile à maintenir et à échelle
Avec le CI/CD, il faut essayer d'avoir un projet le plus léger possible

**Architecture 3-tiers** : HTML, CSS, JS dans le front, PHP dans le back, SQL dans la BDD (utilisation classique)

**Architecture SPA** : Single Page Application
*1 seule page HTML, CSS et JS, tout le contenu est servi par le serveur et injecté dans la page*

*Pour aller plus loin :*
*- **SSR : Server Side Rendering** : le principe est de générer le HTML sur le serveur et de l'injecter dans la page*
*- **CSR : Client Side Rendering** : le principe est de générer le HTML sur le client (dans le navigateur)*

**Architecture orienté service** : compromis entre l'architecture monolithique et l'architecture microservice



