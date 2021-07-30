# Découverte de Windows 10

L'objectif de ce TP est d'apprendre à gérer un PC sous ``Windows 10`` : vérifier l'accès à internet, administrer les utilisateurs et gérer les partages de fichiers. S'il vous reste du temps, vous découvrirez les rudiments du langage ``PowerShell``. 

> :warning: A partir de cette séance de TP, vous allez travailler en binôme. Vous ne rendrez qu’un CR par table. Il doit être déposé sur Eprel au format PDF. Il est impératif de déposer votre CR à l’heure, c’est à dire avant la fin du TP.

## Contexte

Vous êtes chargé concevoir le [système d'information](https://fr.wikipedia.org/wiki/Syst%C3%A8me_d%27information) (SI) d'une petite entreprise constituée de trois employés. 

Ces utilisateurs travaillent chacun sur leur PC :

- ``Pinkman`` appartient à l'équipe de ``R&D``. Il utilise ``PC1``. 
- ``White`` et ``Gus`` font partie de l'équipe des ``Admins``. Ils travaillent sur ``PC2`` et ``PC3``, respectivement. 

<p align="center">
	<img src="images/contexte.png" width="75%">
</p>

Dans le cadre de leur travail, ils ont régulièrement besoin d'échanger des fichiers. Plutôt que de les laisser galérer avec des clés USB, vous décidez de leur mettre à disposition :

- Des dossiers partagés en réseau, sur leur PC
- Un serveur de fichiers (FTP)
- Un stockage dans le *cloud*

## Maquette

La figure suivante illustre la maquette de TP :

- Les trois PC, sous ``Windows 10``, jouent le rôle des ordinateurs des trois employés de l'entreprise
- ``PC3`` héberge également une VM ``Debian`` qui joue le rôle du serveur FTP

<p align="center">
	<img src="images/maquette.png" width="75%">
</p>

[Lancez la restauration](https://doc2-iutrt.readthedocs.io/en/latest/divers.html#lancer-la-restauration-d-un-os) de ``Windows 10`` sur tous les PC. [Importez une VM](https://doc2-iutrt.readthedocs.io/en/latest/virtualbox.html#importer-une-vm) ``Debian Stretch`` sur ``PC3`` et configurez-la en [mode ``Accès par pont``](https://doc2-iutrt.readthedocs.io/en/latest/virtualbox.html#configurer-la-carte-reseau-d-une-vm-en-mode-acces-par-pont). 

Enfin, ouvrez une session sur les trois PC et la VM, avec les [identifiants de l'IUT](https://doc2-iutrt.readthedocs.io/en/latest/divers.html#identifiants-de-l-iut).

## Préparation

Sur une feuille A4, dessinez un schéma de votre maquette en faisant apparaitre :
- Les PC et les VM
- Le câblage interconnectant ces ordinateurs
- L'OS utilisé sur chaque PC et VM

## Sommaire

[Configuration réseau](part1.md)
