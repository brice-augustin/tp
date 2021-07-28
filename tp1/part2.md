# Découverte de l'administration système et réseau

Dans cette partie, vous allez vérifier que vos quatre ordinateurs (l'hôte sous ``Windows 10`` et les trois VM) peuvent communiquer ensemble. 

## Adresse IP

Avant d'établir une communication, il faut déjà déterminer l'[adresse IP](https://fr.wikipedia.org/wiki/Adresse_IP) de chaque ordinateur, qu'il soit physique ou virtuel. 

Déterminez l'adresse IP des quatre ordinateurs ([Windows](https://doc2-iutrt.readthedocs.io/en/latest/windows.html#determiner-l-adresse-ip-de-la-carte-reseau-ethernet-4), [Linux](https://doc2-iutrt.readthedocs.io/en/latest/linux.html#determiner-l-adresse-ip)) qui constituent votre réseau. Notez vos résultats dans un tableau :

Nom | Type | Adresse IP
--------------------- | ----| ----------
``PC Exemple`` | Physique | ``172.16.110.42/24``
``Hôte - Windows 10`` | Physique |
``VM1 - Windows Server 2016`` | Virtuel |
``VM2 - Debian Stretch (#1)`` | Virtuel |
``VM3 - Debian Stretch (#2)`` | Virtuel |

Vous remarquerez que les quatre adresses IP commencent toutes par ``172.16.110``. Par convention, à l'IUT le troisième nombre (ici ``110``) correspond au numéro de la salle de TP. Le quatrième identifie chaque équipement de manière unique, dans la salle. 

## Ping

Pour vérifier que deux ordinateurs A et B peuvent communiquer, on utilise la méthode du ping. Depuis A, on envoie une requête vers B. Si ce dernier répond, c'est que la communication entre A et B est possible. 

Commencez par [lancer un ping](https://doc2-iutrt.readthedocs.io/en/latest/windows.html#lancer-un-ping-vers-l-adresse-ip-8-8-8-8) de ``Windows Server 2016`` (VM1) vers ``Debian Stretch`` (VM2), et [inversement](https://doc2-iutrt.readthedocs.io/en/latest/linux.html#lancer-un-ping-vers-l-adresse-ip-8-8-8-8).

Notez le résultat des deux pings dans un tableau :

De | Vers | OK/NOK
--- | --- | ---
``VM1`` | ``VM2`` |
``VM2`` | ``VM1`` |

Vérifiez ensuite que vos quatre ordinateurs (physique et virtuels) peuvent communiquer ensemble.

Enfin, choisissez deux collègues dans la salle et vérifiez que vous pouvez communiquer avec leurs ordinateurs. 
