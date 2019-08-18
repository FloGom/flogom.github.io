---
title:  "Utiliser une vieille machine pour l'impression 3D"
categories: [old computers]
tags: [old computers]
layout: post
---


### Est-ce bien sage?

## 1 Objectifs et cahier des charges

L'objectif est d'utiliser une vieille machine pour réaliser 
des impressions 3D.


### 1.a Cahier des charges

Le cahier des charges est le suivant (les spécifications sont 
rangées par ordre décroissant d'importance:
1. Préparer un fichier gcode pour l'impression 3D à partir 
d'un .stl, et le charger sur une carte SD.
2. Piloter l'imprimante 3D.
3. Modéliser et préparer des objets pour l'impression 3D.

L'idée principale est de tester la faisabilité d'utiliser 
une vieille machine pour l'impression 3D, et de voir s'il 
est possible de lui donner une seconde vie.
Les spécifications précédentes semblent classées par ordre 
croissant de difficulté.


### 1.b Logiciels envisagés pour répondre au cahier des charges

| Spécification | Logiciel                 |
|---------------|--------------------------|
| 1.            | Ultimaker 3 ou 4, Slic3r |
| 2.            | Pronterface, Ultimaker   |
| 3.            | FreeCAD, Blender         |


### 1.c Compatibilité des logiciels

| Logiciel | Systèmes | CPU | RAM | Carte Graphique |
|----------|----------|-----|-----|-----------------|
|Ultimaker Cura 4 | Win. Vista, Mac OS 10.7, Ubuntu 15.04|  |  |  OpenGL2 comp.|
|FreeCAD          |
| Slic3r          |
| Pronter Face    |



## 2 PC Pentium 4 sous Linux
Premier essai avec un Pentium 4 sous Linux Lubuntu.
L'ordinateur possède les caractéristiques suivantes:

| Caractéristique  | Valeur              |
|------------------|---------------------|
| Marque           | Dell                |
| Modèle           | Dimension 5150      |
|       CPU        | Pentium 4 à 3 GHz   |
| RAM              | 2 Go                |
| Carte Graphique  | NVidia Geforce 7300 |

Le système d'exploitation installé est Lubuntu. Plusieurs versions
 ont été installées pour résoudre des problèmes de driver de carte
 graphique.
Les drivers NVidia ne sont pas installables car les nouvelles
 versions d'Ubuntu ont cassé la compatibilité avec certaines
 dépendances.

|Version Lubuntu | Driver         | Fonctionne                    |
|----------------|----------------|-------------------------------|
| 14.04          | NVidia 390.135 | Partiellement (pb résolution) |
| 16.04          | Nouveau        | Oui, OpenGL2                  |
| 18.04          | Nouveau        | Oui, OpenGL2                  |
| 18.10          | Nouveau        | Pas testé                     |
| 19.04          | Nouveau        | Oui, OpenGL                   |

## 3 Macbook Blanc 2006
### 3.a Sous Mac OS 10.7
Le système installé, Mac OS 10.7, est la dernière version compatible 
avec l'ordinateur.
Compatibilité des logiciels:

| Logiciel       | Fonctionne | Compatibilité |
|----------------|------------|---------------|
|Ultimaker Cura 4| Non        | 10.7, OpenGL2 |
|FreeCAD         | Non        | 10.11         |
|Slic3r 1.3.0    | Non        |               |
|Slic3r 1.2.9    | Oui        | 10.7          |
|Printrun        | Oui        |               |


### 3.b Sous Virtual Box 4.3.40

La virtualisation est une option supplémentaire pour faire tourner 
des vieilles machines avec de nouveau logiciels.
Virtual Box n'est pas compatible avec 10.7 dans les dernières versions.
 La dernière version compatible avec Lion est la 4.3.0.

Sous Virtal Box la dernière version Lubuntu compatible à 
l'installation est la 14.04 Trusty Tahr, pour AMD64.
Cela parait logique Virtual box 4.3 datant de 2015.
Les vieilles images sont téléchargeables depuis un miroir russe 
tenu par l'université de PERM:
[Linux PSU - Ubuntu release](http://linux.psu.ru/ubuntu-releases/)

| Logiciel                | Fonctionne | Commentaire             |
|-------------------------|------------|-------------------------|
|Ultimaker Cura 4.2       | Oui        | App Image               |
|Ultimaker Cura 3.6       | Oui        | App Image               |
|FreeCAD 0.18.3           | Oui        | App Image               |
|FreeCAD 0.18.3 via ppa   | Non        | Problème de dépendances |
|Slic3r 1.3.0             | Oui        | App Image               |

Pour plus de confort installer 
[AppImageLauncher](https://github.com/TheAssassin/AppImageLauncher).

### 3.c FreeCAD version Windows avec Winebottler
Pour Mac OS 10.7 la dernière version de Wine Bottler 
est la version 1.8.6
A noter, WineBottler est compatible uniquement avec 
les versions 32 bits des applications.

Slic3r 1.2.9 fonctionnant déjà nativement sous Mac OS 10.7, 
WineBottler est utilisé uniquement pour obtenir la dernière version 
de FreeCAD.

FreeCAD s'installe correctement et démarre, mais n'est pas utilisable.
La vue 3D ne s'affiche pas après la création d'un nouveau fichier.
Ce bug persiste avec les Winetricks suivants cochés:
- d3dx9
- d3dx10
- glut
- ddr=opengl
- win7

Crash à la fabrication du prefix:
- python 2.6
- python 2.7

## Conclusion

Les configurations qui fonctionnent après installation sont résumées dans le 
tableau suivant:

| Configuration | Machine | Système | 1. Slicer | 2. Pilotage | 3. Modélisation 3D |
|---------------|---------|---------|-----------|-------------|--------------------|
| A             |Dell Dimension 5150 | Lubuntu 16.04 | | | FreeCAD 0.18.3 |