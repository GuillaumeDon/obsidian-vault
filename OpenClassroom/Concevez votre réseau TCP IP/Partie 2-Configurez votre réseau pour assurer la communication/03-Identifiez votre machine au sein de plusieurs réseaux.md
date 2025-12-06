### Définissez l’adresse IPv4 de votre machine

Reprenons notre analogie avec le courrier. Lorsque vous voulez envoyer un colis, vous devez écrire plusieurs informations pour qu'il arrive à bon port :

- les nom et prénom du destinataire ;
    
- l’adresse postale du destinataire.
    

Ces informations identifient le destinataire et elles sont obligatoires. Les nom et prénom sont utiles localement pour que le facteur dépose le colis dans la bonne boîte à lettres. L’adresse postale est utile à plus grande échelle, pour que le centre de tri postal sache dans quels pays, ville et rue acheminer le colis.

Lorsque vous envoyez un paquet sur Internet, c’est presque la même chose. Le paquet doit toujours contenir en en-tête :

- une adresse locale : l’adresse MAC ;
    
- une adresse globale : l’adresse IP (Internet Protocol).

==En informatique, un paquet contient toujours les adresses de la source et du destinataire du message. Pour le courrier postal, seule l’adresse du destinataire est obligatoire.

Il existe différentes versions d’IP. La plus utilisée est encore actuellement la version 4, abrégée en **IPv4**. 

Comme pour l’adresse MAC, l’adresse IPv4 a des caractéristiques bien précises :

- Elle peut être publique ou privée :
    
    - les adresses IP privées sont utilisées sur les LAN (réseaux domestiques, d’entreprise…) ;
        
    - les adresses IP publiques sont souvent réservées aux opérateurs de télécommunication sur les réseaux de type MAN/WAN (réseaux nationaux et internationaux).
        
- Elle est modifiable. C’est même à vous de la définir, contrairement à l’adresse MAC.
    
- Elle s’écrit sur 4 octets en décimal (pas d'hexadécimal, cette fois).
    

Voilà à quoi ressemble une adresse IPv4 :

[![Exemple d’adresse IPv4. L'adresse est composée de 4 parties séparées par un point.](https://user.oc-static.com/upload/2021/06/01/16225594627_P2C3-1.png)](https://user.oc-static.com/upload/2021/06/01/16225594627_P2C3-1.png)
Vous voyez qu’elle est composée de 4 parties (4 octets) séparées par un point. Chaque partie étant un octet soit 8 bits. Chaque partie peut prendre une valeur entre 0 et 255.

N’oubliez pas qu’une fois configurée dans la machine, cette adresse IP sera convertie en binaire car les machines ne parlent qu’en binaire. Or en binaire, avec 8 bits, on ne peut compter que de 0 à 255.

==Vous l’aurez compris, à cette étape du cours il devient essentiel de savoir convertir les nombres décimaux en binaire. 

==L’adresse IP permet d’identifier la localisation géographique des machines, ou au moins de savoir à quel réseau elles appartiennent, contrairement à l’adresse MAC. Grâce à elle, on peut souvent localiser les émetteurs et récepteurs des messages qui transitent dans un réseau.

### Définissez le plan d’adressage de votre réseau

Pour créer votre propre réseau, vous devrez choisir les adresses IP que vous allez affecter à vos machines. C’est ce qu’on appelle faire un **plan d’adressage**. Et pour avoir un plan d’adressage cohérent, vous ne devrez pas choisir vos adresses au hasard.

Si vous travaillez dans un seul et même réseau, vous devrez veiller à :

- ne pas attribuer une adresse IP déjà existante sur ce réseau ;
    
- attribuer des adresses IP qui soient toutes dans la même plage d’adresses réseau.

Une **plage d’adresses** est l’ensemble des adresses IP consécutives qui sont attribuables aux machines d’un même réseau. 

On peut faire le parallèle avec les codes postaux d’un département. Prenons le Puy-de-Dôme, identifié par le numéro départemental 63. Tous les codes postaux des communes situées dans ce département doivent être entre 63000 et 63999 : c’est la plage des codes postaux attribuables.

Mais alors, dans un réseau informatique, comment être sûr que 2 machines ont des adresses IP dans la même plage ?

La réponse tient en un mot : le **masque**.

Une adresse IP contient toujours :

- une partie qui identifie le réseau ;
    
- une partie qui identifie la machine.
    

Le masque est le **délimiteur** entre la partie réseau et la partie machine. C’est ce qui vous permet de vérifier que deux machines sont bien dans la même plage réseau.

Prenons un exemple pour illustrer cela :

[![Adresse IP avec masque. L'adresse est constituée de deux parties séparées par un slash. - La première partie est l'adresse IP - La deuxième partie est le masque](https://user.oc-static.com/upload/2021/06/21/16242656306385_P2C3-2.png)](https://user.oc-static.com/upload/2021/06/21/16242656306385_P2C3-2.png)

Adresse IP avec masque

Ici, le masque nous indique que les 8 premiers bits de cette adresse IP (172) sont ceux qui identifient le réseau, et donc que les 24 derniers (16.254.1) identifient la machine :

[![Délimitation du masque sur un IP](https://user.oc-static.com/upload/2021/06/01/16225596863201_P2C3-3.png)](https://user.oc-static.com/upload/2021/06/01/16225596863201_P2C3-3.png)

Délimitation du masque sur un IP

Par la même occasion, le masque nous permet d’en déduire l’**adresse réseau**. Cette adresse réseau s’obtient en prenant l’adresse IP et en remplaçant par des “0” les bits identifiant la machine. Cela donne ici : 

[![Adresse réseau](https://user.oc-static.com/upload/2021/06/01/16225597186708_P2C3-4.png)](https://user.oc-static.com/upload/2021/06/01/16225597186708_P2C3-4.png)

C’est utile car certains équipements que vous configurerez peuvent avoir besoin de cette adresse réseau. Vous devez donc être en mesure de la trouver.

Maintenant, pour savoir si 2 machines sont dans le même réseau IP, c’est-à-dire dans la même plage réseau, il suffit de comparer leurs adresses réseau :

- Si elles sont identiques, les machines sont dans le même réseau IP. 
    
- Si elles sont différentes, les machines sont dans un réseau IP différent.
    

Vous avez compris l’idée ? ![;)](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABMAAAATCAMAAAEyifZoAAAAbFBMVEX/wWn/tFr/2YT/6pj/+an/3Yn/0Xz/7p3/vWX/uF//xG3/////9qX/umH/+6z/5JH/1X//znf/7Jr/9KPmolD/4Y3/86KUlJSkd0L/y3RqSCD/tl3/x3DXl0v//a7//7Codjr/slgAAAD///8cVNK0AAAAJHRSTlP//////////////////////////////////////////////wBYLA0NAAAA5ElEQVQYV11PRXLFUAAi7vK1kjwB7n/HLjJdtDsYGASWIRGmYSMK2uE5loJ3ELBlQ7GCUaUNwnk7aJiFDFtV99plw/eY0ns6aaip1vu5kIK1HBJ7GbYt2TZsS7pQ7qoy2/AR09q0wVCdUpy+BuE5p1RrLAKe2zyX/cAAte25kBQcFokMhp1J5H/JtqVMMl+1l3o86rV+VE15C5dP+RFTSim+m/02HlmG8r2On99KsfvQeR7Mgp5bV8cU166cJhxkEJTbpnxtTXv2R0GyyIKVMY7qh4Ik2efrusLFOZzhz74Qwu++HxuXJSXJNKbZAAAAAElFTkSuQmCC ";)")

Prenons maintenant un cas concret pour illustrer cela.

Imaginez 2 machines dans un réseau point-à-point, c’est-à-dire reliées sans switch mais directement par un câble, avec la configuration IP suivante :

[![Configuration IP sur un réseau point-à-point : - A gauche, la machine A - A droite, la machine B](https://user.oc-static.com/upload/2021/06/01/16225597726865_P2C3-5.png)](https://user.oc-static.com/upload/2021/06/01/16225597726865_P2C3-5.png)

Configuration IP sur un réseau point-à-point

L’adressage des machines est le suivant :

- La machine A avec l’adresse : 192.168.10.1/24.
    
- La machine B avec l’adresse : 192.168.20.3/24.
    

Le masque nous permet de dire que :

- les 24 premiers bits sont l’identificateur du réseau ;
    
- les 8 derniers bits sont l'identificateur de la machine.
    

On peut donc en déduire que :

- la machine A est sur le réseau 192.168.10.0 ;
    
- la machine B est sur le réseau 192.168.20.0.
    

Les 2 machines étant sur 2 réseaux différents, elles ne peuvent pas communiquer.

Si on souhaite conserver le masque en /24, Les adresses IP des machines sont donc mal choisies. Il aurait plutôt fallu affecter à la machine B l’adresse 192.168.10.3/24, par exemple.

Si vous intervenez sur un réseau existant, vous n’aurez qu’à utiliser le masque de ce réseau. Si, au contraire, vous concevez un nouveau réseau, vous devrez définir vous-même son masque.

Vous définirez le masque de votre réseau en fonction du nombre de machines prévues. Plus un masque a une grande valeur, moins vous pourrez mettre de machines dans votre réseau.

Voyons cela sur un schéma :

[![Une adresse IP associée à différents masques](https://user.oc-static.com/upload/2021/06/01/16225598501633_P2C3-6.png)](https://user.oc-static.com/upload/2021/06/01/16225598501633_P2C3-6.png)

Une adresse IP associée à différents masques

Vous voyez qu’un masque en /8 laisse 24 bits pour identifier des machines. Avec 24 bits, on obtient plus de 16 millions (2^24) d’adresses possibles. À l’opposé, un masque en /24 ne laisse que 8 bits pour des adresses machines, et donc seulement 256 (2^8) adresses possibles.

Attention, Il faut aussi faire la différence entre le nombre d’adresses IP total et le nombre d’adresses IP attribuables. Par exemple, si on dispose de 8 bits pour les adresses machines, on peut créer au total 256 adresses IP, mais seulement 254 adresses IP attribuables.

Ah bon ? Mais pourquoi ?

Dans une plage réseau, la première et la dernière adresse ne sont jamais attribuables à une machine, car elles ont une utilité bien spécifique.

- La première est **l’adresse réseau** (c’est ce que nous avons vu plus haut quand nous avons parlé du masque).
    
- La dernière est **l’adresse de diffusion** ou de _broadcast_, en anglais. Elle sert à envoyer un message à toutes les machines d’un réseau en même temps. Elle ne peut donc pas être affectée à une machine précise.
    

Quand on souhaite connaître le nombre de machines que l’on peut avoir dans un réseau, il faut donc calculer le nombre d’adresses totales et retrancher 2.

Dans ces exemples, j’ai pris uniquement des masques dont les valeurs sont des multiples de 8 car ce sont les plus courants. Mais en théorie, vous pouvez tout à fait prendre des valeurs entre 1 et 31.

Dernière information importante concernant les masques : ils peuvent s’écrire de 2 manières.

Par exemple, voici le même masque écrit différemment :

- /24, c’est la notation que nous avons vue, qu’on appelle **notation CIDR** (Classless Inter-Domain Routing) ;
    
- 255.255.255.0, c’est l’ancienne notation qu’on trouve encore très souvent.
    

Pour comprendre le lien entre les 2, il faut passer par le binaire. Si on convertit notre masque 255.255.255.0 en binaire, on obtient 11111111.11111111.11111111.00000000. Ce masque binaire a ses 24 premiers bits à 1, voilà pourquoi ce masque peut s’écrire simplement : /24.

[![Conversion d’un masque réseau en binaire](https://user.oc-static.com/upload/2021/06/01/16225599585945_P2C3-7.png)](https://user.oc-static.com/upload/2021/06/01/16225599585945_P2C3-7.png)

Conversion d’un masque réseau en binaire

La notation CIDR a remplacé la notation standard pour plus de simplicité et de flexibilité.  
Initialement, pour créer un réseau, on n’avait que 3 tailles possibles :

- des réseaux de **254 machines** (masque 255.255.255.0),
    
- de **65 534 machines** (masque 255.255.0.0),
    
- ou de **16 777 214 machines** (masque 255.0.0.0).
    

Si on prévoyait un réseau avec 3 000 machines, on était obligé de prendre un réseau ayant pour masque 255.255.0.0 et acceptant jusqu’à 65 534 machines.

Le système CIDR a permis d’être plus flexible, en autorisant des masques personnalisés et non surdimensionnés pour les besoins du réseau.

### Attribuez des adresses IP aux machines de votre réseau

Vous voilà de retour dans votre mission pour le compte de l'auto-école Tinos. Votre binôme de travail vous indique qu’il faut changer les adresses IP actuellement définies sur les 3 machines de Tinos. Il vous précise que le serveur devra avoir comme adresse IP 192.168.0.1/24. C'est à vous de choisir correctement les adresses IP des 2 autres machines.

Pour l’instant, vous n’intervenez pas sur les machines de Cyclade.







Pour tester la communication entre 2 machines, vous savez déjà comment générer un paquet sous Packet Tracer. Il existe cependant une autre méthode applicable sur tous les systèmes : la commande **ping**. Cette commande est universelle et permet d’envoyer un message de test vers une autre machine pour vérifier qu’elle répond bien.

[![Schéma représentant le principe de fonctionnement du ping. - Un ordinateur à gauche envoie le message](https://user.oc-static.com/upload/2021/06/01/16225601907415_P2C3-8.png)](https://user.oc-static.com/upload/2021/06/01/16225601907415_P2C3-8.png)

Principe de fonctionnement du ping

Cette commande doit s’utiliser sur la machine qui va envoyer le message ping en précisant quelle est l’adresse IP de la machine destinataire.

Par exemple, si je souhaite vérifier que la communication fonctionne entre ma machine et un serveur Google ayant l’adresse IP 8.8.8.8, dans mon invite de commandes je dois entrer :

ping 8.8.8.8

Si j’obtiens une réponse, cela signifie que la communication fonctionne.

[![Test ping vers 8.8.8.8 : screenshot de l'invité de commande affichant la réponse du test.](https://user.oc-static.com/upload/2021/06/01/1622565225599_AC8B7747-A1EB-4053-8496-7922B52481E3_4_5005_c.jpeg)](https://user.oc-static.com/upload/2021/06/01/1622565225599_AC8B7747-A1EB-4053-8496-7922B52481E3_4_5005_c.jpeg)

Vérifiez le résultat de votre test ping vers 8.8.8.8

Vous pouvez aussi utiliser la commande ping sur les machines de votre réseau virtuel sous PacketTracer.

Pour cela :

1. Cliquez sur une des machines terminales de votre réseau virtuel.
    
2. Allez dans l’onglet “Desktop”.
    
3. Cliquez sur “Command Prompt”.
    

Vous obtenez un équivalent de l’invite de commandes Windows qui vous permet d’utiliser des commandes comme ping.

[![Invite de commande sous Packet Tracer](https://user.oc-static.com/upload/2021/05/25/16219653205122_image27.jpg)](https://user.oc-static.com/upload/2021/05/25/16219653205122_image27.jpg)

#### **À vous de jouer !**

1. Configurez l’adresse IP des 3 machines du réseau de l'auto-école Tinos pour qu’elles soient sur le même réseau IP. Rappel : le serveur doit avoir l’adresse IP 192.168.0.1/24.
    
2. Testez la communication entre ces machines.
    

#### **Corrigé**

L’IP fournie étant 192.168.0.1/24, la partie réseau est sur 24 bits, ce qui laisse 8 bits d’IP attribuables aux machines.

Vous pouviez donc choisir des adresses IP allant de 192.168.0.2/24 à 192.168.0.254/24

Et pourquoi pas 192.168.0.255 ?

Parce que 192.168.0.255 est l’adresse de broadcast, elle n’est donc pas attribuable, tout comme l’adresse 192.168.0.0 qui est l’adresse du réseau. N’oubliez pas : vous ne pouvez jamais attribuer la première et la dernière adresse d’une plage réseau.

Jusqu’à maintenant nous avons uniquement parlé d’un certain type d’adresses IP : les adresses IPv4. Malheureusement, vu l’ampleur d’Internet, il n’est plus possible d’affecter des adresses IPv4 uniques à chaque machine connectée. Ces adresses vont peu à peu être remplacées par des adresses **IPv6**, qui, de par leur structure (128 bits au lieu de 32 bits) permettront d’adresser toutes les machines connectées du monde.

Dans ce cours, nous nous limiterons cependant à IPv4 car ce type d’adresse continuera d’être utilisé dans les réseaux LAN. Les IPv6, elles, seront surtout nécessaires dans les réseaux WAN/MAN.

### Simulez une architecture grâce à Cisco Packet Tracer

De retour dans votre entreprise, vous devez terminer la simulation d’architecture réseau pour votre client, M. Falman. Vous avez déjà configuré les adresses IP des 3 machines sur le réseau du client.

[![Schéma du réseau actuel : les adresses IP des 3 machines de Tinos ont été configurées](https://user.oc-static.com/upload/2021/06/21/16242661511344_P2C3-9.png)](https://user.oc-static.com/upload/2021/06/21/16242661511344_P2C3-9.png)

Schéma du réseau actuel : les adresses IP des 3 machines de Tinos ont été configurées

Votre collègue est allé sur place pour faire un repérage. Il vous appelle pour vous indiquer les adresses des 2 postes du réseau de l’associé :

- 192.168.100.1/24
    
- 192.168.100.2/24
    

#### **À vous de jouer !**

1. Configurez ces adresses sur les 2 postes restants.
    
2. Testez un envoi de paquet entre les 2 PC du réseau associé.
    
3. Testez un envoi de paquet entre le PC1 et le Serveur0.

### En résumé

- L’adresse IP est nécessaire pour acheminer des messages entre des réseaux différents.
    
- Une adresse IPv4 est écrite sur 32 bits, dont une partie sert à identifier le réseau et l’autre partie à identifier la machine.
    
- L’adresse IP est toujours associée à un masque permettant de savoir où est la limite entre l’identifiant du réseau et l’identifiant de la machine.
    
- L’IPv6 va peu à peu prendre le relais de l’IPv4, car il permet de créer beaucoup plus d’adresses, suffisamment pour toutes les machines connectés du monde.
    
- Un plan d’adressage cohérent doit être élaboré lors de la création du réseau. Il permet de définir les adresses IP qui seront affectées aux machines, et leur nombre.
    

 _Vous savez désormais adresser des machines dans un réseau ! Découvrez comment établir l’itinéraire des messages dans le chapitre suivant !_