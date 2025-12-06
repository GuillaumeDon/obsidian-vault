

Vous vous souvenez de l’équipement qu’on appelle aussi la passerelle, et qui fait la jonction entre 2 réseaux ? C’est le fameux routeur. C’est lui qui doit router les paquets, autrement dit, les acheminer vers le bon réseau.

### Identifiez les étapes pour établir l’itinéraire des messages

Pour router correctement les paquets, le routeur dispose d’une **table de routage** dans sa mémoire interne.

La table de routage est un tableau qui indique au routeur vers quel réseau envoyer un paquet, en fonction de son adresse IP de destination.

Pour que la table de routage fonctionne, il faut :

- Activer les interfaces réseau du routeur. 
    

Eh oui ! Même si le routeur est sous tension la plupart du temps, il faut activer individuellement les interfaces. Quand on parle d’interface, on fait référence à un port physique, ici le port RJ45.

- Configurer une adresse IP à chacune des interfaces activées.
    
- Vérifier et éventuellement modifier la table de routage.
    

D’accord, mais quelle adresse IP dois-je configurer sur le routeur, étant donné qu’il est le “pont” entre plusieurs réseaux ? On ne peut quand même pas lui affecter plusieurs adresses IP ?

Eh bien si, justement ! Le routeur a autant d’adresses IP que de réseaux auxquels il est connecté. Ainsi, chaque port physique ou interface doit être configuré avec une adresse IP dans le bon réseau.Voyons tout de suite un exemple concret pour y voir plus clair !

### Configurez le routage d’une architecture simple

Imaginez que l’on cherche à configurer une adresse IP sur les interfaces réseau des routeurs et sur les PC de cette architecture.

[![Architecture avec 1 routeur et 3 réseaux](https://user.oc-static.com/upload/2021/06/21/16242672544971_P2C4-1.png)](https://user.oc-static.com/upload/2021/06/21/16242672544971_P2C4-1.png)

Architecture avec 1 routeur et 3 réseaux

Pour cela, il faut dans un premier temps déterminer :

- le nombre de réseaux présents sur l’architecture ;
    
- le nombre d’interfaces à configurer.
#### Déterminez le nombre de réseaux et d’interfaces

Pour le nombre de réseaux, c’est très simple : on sait qu’un routeur délimite les réseaux, on peut donc facilement en déduire qu’ici il y en a 3. Pour les interfaces réseau, nous savons qu’il y a une interface à chaque extrémité d’un câble, donc 6 au total.

[![Schéma avec 3 réseaux et 6 interfaces](https://user.oc-static.com/upload/2021/06/21/16242672780372_P2C4-2.png)](https://user.oc-static.com/upload/2021/06/21/16242672780372_P2C4-2.png)
#### Définissez les adresses IP manquantes sur le routeur

Les interfaces des 3 PC ont déjà une adresse IP, il nous reste à définir les adresses IP manquantes sur le routeur :

- Une des interfaces du routeur est dans le même réseau que le PC0. Il suffit de lui donner une adresse entre 192.168.30.2 et 192.168.30.254. Prenons 192.168.30.254/24.
    
- Une des interfaces du routeur est dans le même réseau que le PC1. Dans la même logique, on va lui attribuer l’IP 192.168.10.254/24.
    
- Quant à la dernière interface, affectons-lui l’adresse 192.168.20.254/24.
    

[![Schéma réseau complet avec adresses IP](https://user.oc-static.com/upload/2021/06/21/16242676099817_P2C4-3.png)](https://user.oc-static.com/upload/2021/06/21/16242676099817_P2C4-3.png)

Schéma réseau complet avec adresses IP

==Par convention, on a tendance à affecter au routeur une adresse en fin de plage IP. Par exemple, sur le réseau 192.168.100.0/24, on gardera souvent l’adresse IP 192.168.100.254 pour le routeur. Cela fonctionnera quand même si vous ne le faites pas, mais autant respecter les conventions pour faciliter la compréhension de votre schéma.

#### Générez une table de routage

Venons-en maintenant à la table de routage. Vous n’avez pas besoin de la créer car le routeur est capable de la générer tout seul. Voilà à quoi elle va ressembler :

|   |   |   |   |
|---|---|---|---|
|Réseau de destination|Réseau directement connecté|Interface de sortie|Prochain saut|
|192.168.10.0/24|Oui|192.168.10.254||
|192.168.20.0/24|Oui|192.168.20.254||
|192.168.30.0/24|Oui|192.168.30.254||

Pas de panique, je vous explique tout de suite de quoi est constituée cette table !

Elle comporte 3 lignes, c’est-à-dire 3 routes vers 3 réseaux différents.

Imaginons qu’un paquet à destination de l’adresse 192.168.20.1 arrive sur le routeur. Celui-ci regarde dans sa table de routage s’il existe un réseau de destination correspondant à l’adresse IP indiquée sur le paquet. Ici c’est le cas, il s’agit du réseau 192.168.20.0/24.

La table de routage lui précise qu’il est directement connecté à ce réseau et que pour acheminer un paquet vers ce réseau, il doit router le paquet sur son interface portant l’IP 192.168.20.254.

Voilà comment le routeur va réussir à acheminer les paquets vers le bon réseau.

D’accord, mais à quoi sert la colonne “Prochain saut ?”

La colonne “prochain saut” servira dans le cas d’architectures plus complexes, comme par exemple celle-ci :

[![Architecture composée de 2 routeurs et de 3 réseaux.](https://user.oc-static.com/upload/2021/06/21/16242676564484_P2C4-4.png)](https://user.oc-static.com/upload/2021/06/21/16242676564484_P2C4-4.png)

Architecture composée de 2 routeurs et de 3 réseaux.

Cette architecture est composée de 2 routeurs et de 3 réseaux. Si on regarde la table de routage du Router0, voilà à quoi elle ressemble :

|   |   |   |   |
|---|---|---|---|
|Réseau de destination|Réseau directement connecté|Interface de sortie|Prochain saut|
|192.168.10.0/24|Oui|192.168.10.254||
|10.0.0.0/30|Oui|10.0.0.1||
|192.168.20.0/24|Non|10.0.0.1|10.0.0.2|

Cette table contient 3 routes vers les 3 réseaux de notre architecture.

Cette fois, si un paquet à destination de 192.168.20.1 arrive sur le Router0, celui-ci voit que le réseau associé est 192.168.20.0/24. Le routeur n’est pas directement connecté à ce réseau, et pour l’atteindre il sait qu’il va devoir faire passer le paquet par un autre routeur dont l’adresse est 10.0.0.2. Dans une table de routage, cet autre routeur est souvent identifié comme “prochain saut” ou “passerelle”.

Mmm. Je crois que je suis un peu perdu avec toutes ces colonnes...

Pas de panique ! Si vous préférez une analogie, on pourrait considérer le prochain saut comme le prochain poste-frontière d’un itinéraire. Si vous souhaitez aller de la France jusqu’au Portugal en passant par la route, votre prochain poste-frontière sera celui à l’entrée de l’Espagne.

Dans une table de routage, les routes vers les réseaux directement connectés sont toujours générées automatiquement. En revanche, pour les routes vers les réseaux distants, cela dépendra de la configuration de vos routeurs. Certains mécanismes permettent aux routeurs d’apprendre les routes automatiquement.

S’il ne sont pas mis en place sur votre architecture, il faudra ajouter les routes manuellement. Pour cela, il faut se plonger dans la documentation de configuration de vos équipements, et apprendre à utiliser l’interface en ligne de commandes.

### En résumé

- Lorsqu’un paquet est envoyé d’un réseau IP vers un autre, il passe obligatoirement par un routeur. Ce dernier est la “passerelle par défaut” ; 
    
- Chaque interface réseau du routeur doit être activée et avoir une adresse IP 
    
- La table de routage enregistrée dans un routeur permet à celui-ci d’envoyer un paquet vers le bon réseau. Elle liste tous les réseaux connus du routeur et la route à prendre pour les atteindre ;
    
- Quand un routeur reçoit un paquet, il regarde l’adresse IP de destination inscrite dans le paquet et la compare avec les réseaux connus dans sa table de routage. Il sait alors vers où envoyer ce paquet.
    

 _Vous savez maintenant comment configurer le routage sur une architecture simple 🥳 Il ne vous reste plus qu'à indiquer une passerelle à vos machines ! Suivez-moi dans le prochain chapitre pour découvrir comment faire._