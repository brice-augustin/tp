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

Avant toute chose, [lancez la restauration](https://doc2-iutrt.readthedocs.io/en/latest/divers.html#lancer-la-restauration-d-un-os) de ``Windows 10`` sur vos PC.

Pendant la restauration, profitez-en pour câbler votre maquette comme indiqué. Le PC du milieu possède plusieurs cartes réseau. *Vous êtes libres de choisir n'importe laquelle.* 
Pour chaque câble branché sur un port de votre switch, vérifiez *systématiquement* que le voyant d'état correspondant s'allume sur la face avant du switch. *Si ce n'est pas le cas, c'est que vous avez commis une erreur de câblage !*

Démarrez les OS et ouvrez une session sur les trois PC avec les [identifiants de l'IUT](https://doc2-iutrt.readthedocs.io/en/latest/divers.html#identifiants-de-l-iut). 

Enfin, [importez une VM](https://doc2-iutrt.readthedocs.io/en/latest/virtualbox.html#importer-une-vm) ``Debian Stretch`` sur PC3 (*pensez à réinitialiser son adresse MAC*) et configurez-la en [mode ``Accès par pont``](https://doc2-iutrt.readthedocs.io/en/latest/virtualbox.html#configurer-la-carte-reseau-d-une-vm-en-mode-acces-par-pont).

## Préparation

Avant de commencer à configurer votre maquette, répondez aux questions suivantes sur une feuille :

- Comment appelle-t-on la représentation du masque suivant : ``/24`` ?
- Convertissez le masque précédent en notation décimale à point. 
- Calculez l'adresse du réseau auquel appartient l'adresse ``172.16.110.42/24``. 
- Dans un réseau IP, quel est le rôle de la passerelle par défaut ?
- Quel est le rôle d'un serveur DNS ?

Dessinez un schéma de votre maquette en faisant apparaitre :

- Les ordinateurs utilisés (physiques et VM) et le câblage
- L'OS utilisé sur chaque PC et VM

Faites valider votre préparation par votre chargé de TP.


## Check-list pour se connecter à internet

Ouvrez un navigateur Web sur PC1 et PC3 et vérifiez que vous avez accès à internet (affichez la page de ``www.perdu.com``). 

Cela vous semble magique ? Pourtant, ça ne l'est pas : au démarrage, vos PC ont demandé et obtenu *automatiquement* toutes les informations nécessaires pour accéder à internet. 

Ces paramètres sont au nombre de trois :
- L'adresse IP du PC (accompagnée de son masque)
- L'adresse IP de la passerelle par défaut
- L'adresse IP du serveur DNS

Dans cette partie, vous allez inspecter tous les éléments impliqués dans une connexion à internet. Ils sont représentés sur la figure suivante.

<a name="fig-connexion-internet"></a>

<p align="center">
	<img src="images/connexion-internet.png" width="75%">
</p>

### Adresse IP et masque

[Affichez les cartes réseau](https://doc2-iutrt.readthedocs.io/en/latest/windows.html#afficher-les-cartes-reseau) de PC1 puis [déterminez son adresse IP](https://doc2-iutrt.readthedocs.io/en/latest/windows.html#determiner-l-adresse-ip-de-la-carte-reseau-ethernet-4). Faites de même sur PC3.

Échangez vos résultats avec vos voisins et remplissez le tableau suivant :

PC | Nom de la carte | Adresse IP | Masque
------- | --------| ---------- | -----
``PC Exemple`` | ``Ethernet 4`` | ``198.51.100.42`` | ``255.255.0.0``
``PC1`` |  |  |
``PC3`` |  |  |
``PC1 voisin`` |  |  |
``PC3 voisin`` |  |  |
``PC fantôme`` | Néant | 172.16.110.3 | 255.255.255.0

Depuis PC1, [lancez un ping](https://doc2-iutrt.readthedocs.io/en/latest/windows.html#lancer-un-ping-vers-l-adresse-ip-8-8-8-8) vers PC3, puis vers les PC de vos voisins pour confirmer qu'ils peuvent communiquer ensemble. 
Enfin, [lancez un ping](https://doc2-iutrt.readthedocs.io/en/latest/windows.html#lancer-un-ping-vers-l-adresse-ip-8-8-8-8) vers une adresse IP non attribuée (*PC fantôme*) pour observer un échec de ping. 

### Passerelle par défaut

[Affichez l'adresse de la passerelle par défaut](https://doc2-iutrt.readthedocs.io/en/latest/windows.html#afficher-l-adresse-de-la-passerelle-par-defaut) de PC1 et PC3. Échangez cette information avec vos voisins et [lancez un ping](https://doc2-iutrt.readthedocs.io/en/latest/windows.html#lancer-un-ping-vers-l-adresse-ip-8-8-8-8) vers cette adresse. 

*Notez cette information car vous en aurez besoin plus tard.*

Paramètre | Valeur
----- | -----
Passerelle de PC1 |
Passerelle de PC3 |
Passerelle de PC1 *voisin* |
Passerelle de PC3 *voisin* |

> :information_source: Comment un PC utilise-t-il la passerelle pour communiquer avec l'extérieur ? C'est une des nombreuses questions auxquelles nous répondrons ... plus tard !

### Serveur DNS

[Affichez l'adresse IP du serveur DNS](https://doc2-iutrt.readthedocs.io/en/latest/windows.html#afficher-l-adresse-du-serveur-dns) de vos deux PC et [lancez un ping](https://doc2-iutrt.readthedocs.io/en/latest/windows.html#lancer-un-ping-vers-l-adresse-ip-8-8-8-8) vers cette adresse. 

*Notez cette information car vous en aurez besoin plus tard.*

Paramètre | Valeur
----- | -----
Serveur DNS de PC1 |
Serveur DNS de PC3 |
Serveur DNS de PC1 *voisin* |
Serveur DNS de PC3 *voisin* |

[Résolvez les noms de domaine](https://doc2-iutrt.readthedocs.io/en/latest/windows.html#resoudre-le-nom-de-domaine-www-perdu-com) suivants :

- ``www.perdu.com``
- ``www.google.com``
- ``www.purepeople.com``

Enfin, vérifiez que vous pouvez [lancer un ping](https://doc2-iutrt.readthedocs.io/en/latest/windows.html#lancer-un-ping-vers-l-adresse-ip-8-8-8-8) vers tous ces serveurs. 

## Synthèse 1

<p align="center">
	<img src="images/penseur.jpg" width=150>
</p>

Résumez en 4-6 lignes vos observations sur l'architecture de votre réseau. Appuyez-vous sur les adresses IP que vous venez de noter (architecture logique) ainsi que sur l'[architecture physique](#fig-connexion-internet)).
Appelez votre chargé de TP pour lui montrer la configuration IP de vos PC. Montrez également qu'ils peuvent se pinger.
