# Découverte du réseau

## Introduction

Ce TP consiste en une introduction à l'administration réseau. Vous découvrirez le rôle des trois [adresses IP](https://fr.wikipedia.org/wiki/Adresse_IP) que tout ordinateur doit connaitre pour accéder à internet : la sienne, bien sûr, mais aussi celle de sa [passerelle par défaut](https://fr.wikipedia.org/wiki/Routeur), et enfin celle de son [serveur DNS](https://fr.wikipedia.org/wiki/Domain_Name_System). Vous apprendrez que ces paramètres peuvent être configurés manuellement ou automatiquement. 
Enfin, vous terminerez avec quelques notions d'administration système sous Windows 10. 

## Préparation de la maquette

La figure suivante illustre la maquette de TP :

- Les trois PC sont branchés sur votre switch perso (``HP`` ou ``3Com``), lui-même relié au réseau de l'IUT
- Vous allez réaliser toutes les manipulations sur les PC de gauche et de droite (PC1 et PC3 sous ``Windows 10``)
- PC3 héberge également une VM sous ``Debian Linux``
- Le PC du milieu (PC2 sous ``Windows 10``) sera utilisé pour afficher le sujet de TP et réaliser le compte-rendu

<p align="center">
	<img src="images/maquette.png" width="75%">
</p>