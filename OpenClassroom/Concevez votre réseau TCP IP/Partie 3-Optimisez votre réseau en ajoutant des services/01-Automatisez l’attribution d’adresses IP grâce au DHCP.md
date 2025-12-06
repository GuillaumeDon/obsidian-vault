### Identifiez les avantages du serveur DHCP

Dans la partie précédente, nous avons appris qu’une adresse IP sert à identifier globalement une machine pour qu’elle puisse communiquer à travers les réseaux. Chaque machine doit obligatoirement avoir une adresse IP, qu’il vous faut configurer au préalable.

Mais pourtant je peux très bien aller sur Internet sans configurer mon adresse IP ! Elle n’est pas obligatoire dans ce cas-là ?

Eh bien si ! L’adresse IP est aussi nécessaire pour aller sur Internet ! Mais il existe un système d’attribution automatique, le **DHCP**, qui configure automatiquement l’adresse IP d’une machine. Ainsi, vous n’avez pas besoin de le faire !

DHCP (Dynamic Host Configuration Protocol) signifie “protocole de configuration automatique des hôtes”. Ce mécanisme est très utilisé dans les réseaux LAN car il simplifie l’accès au réseau pour les utilisateurs. Il permet de configurer plusieurs éléments sur les machines :

- leur adresse IP et leur masque ;
    
- l’adresse IP de la passerelle par défaut ;
    
- l’adresse IP du **serveur DNS**.
    

Le serveur DNS est utilisé principalement pour faciliter l’identification des machines qui hébergent des sites Internet ou autres services réseau. Nous reviendrons là-dessus dans le chapitre suivant.

Le DHCP permet également de centraliser la distribution des adresses IP, ce qui présente deux avantages :

-  éviter les doublons ;
    
- connaître la liste des adresses IP déjà attribuées.
    

### Appréhendez le DHCP dans une architecture simple

#### La configuration client-serveur

Comme la plupart des protocoles, le DHCP fonctionne en mode client-serveur. Il a donc besoin :

- d’une machine jouant le rôle de serveur ;
    
- d’une ou plusieurs machines jouant le rôle de client(s).
    

Un serveur est un ordinateur configuré pour répondre automatiquement à des requêtes spécifiques. Le serveur DHCP, par exemple, répond aux requêtes de type DHCP. Tout poste utilisateur peut donc devenir un serveur DHCP, web ou mail, s’il a été configuré dans ce sens.

Le serveur et le(s) client(s) sont configurés de manières différentes.

Le serveur doit être configuré pour :

- répondre aux requêtes des clients qui demandent une adresse IP ;
    
- leur attribuer une adresse pour une durée définie ;
    
- choisir l’adresse dans une plage d’adresses qu’on lui aura spécifiée. 
    

Les clients doivent être configurés pour :

- demander automatiquement une adresse IP dès qu’ils sont connectés physiquement à un réseau.
    

#### Les échanges entre clients et serveur

Une fois les machines configurées, voilà comment se déroulent les échanges entre client et serveur :

[![Principe d'échanges entre client et serveur DHCP en 4 étapes : découverte, offre, requête et acquittement](https://user.oc-static.com/upload/2021/06/03/16227097553456_P3C1-1.png)](https://user.oc-static.com/upload/2021/06/03/16227097553456_P3C1-1.png)

Principe d'échanges entre client et serveur DHCP en 4 étapes : découverte, offre, requête et acquittement

[_Source_](https://i2.wp.com/www.atomit.fr/wp-content/uploads/2017/10/AWS-Networking.png?resize=511%2C170&ssl=1)

Le processus se déroule généralement en 4 étapes, qui correspondent à l’échange de 4 messages :

**1. DHCP Discover (Découverte)** : Y a-t-il quelqu’un pour m’attribuer une adresse IP ?

Un client vient de se connecter au réseau. Il émet une requête à tout le réseau pour savoir si un serveur DHCP peut lui attribuer une adresse.

À ce stade, le seul moyen d’identification qu’a le client est son adresse MAC. La requête est donc envoyée à tout le réseau, avec comme adresse source, l’adresse MAC du client.

**2. DHCP Offer (Offre)** : Voilà une adresse IP !

Le serveur DHCP reçoit le message et répond au client en lui fournissant une adresse IP.

Ce message contenant l’adresse IP est envoyé à destination de l’adresse MAC du client.

**3. DHCP Request (Requête)** : OK, je prends cette adresse IP, peux-tu le noter ?

Le client accepte l’offre et demande au serveur de lui envoyer en confirmation un message contenant tous les paramètres de configuration, et d’enregistrer l’IP allouée.

**4. DHCP Ack (Acquittement)** : C’est enregistré !

Le serveur envoie le message de confirmation et met à jour sa **table d’allocation d’IP**.

### Appréhendez la table d’allocation d’adresses IP

Dans la table d’allocation d’adresses IP, chaque adresse IP est associée à :

- l’adresse MAC de la machine qui a récupéré cette IP ;
    
- une date de fin de bail. 
    

Une date de fin de bail ? À quoi ça sert ?

Une adresse IP est toujours allouée pour un temps défini par le serveur DHCP. Cela évite que les adresses IP soient affectées indéfiniment à des machines qui ne sont plus dans le réseau. Juste avant que le bail n’arrive à échéance, le client demande le renouvellement du bail auprès du serveur DHCP. S’il n’obtient pas de réponse, il doit libérer l’adresse.

On pourrait représenter la table d’allocation de cette manière :

|   |   |   |
|---|---|---|
|Adresse IP|Adresse MAC|Fin de bail|
|192.168.0.1/24|E3:34:12:35:FE:2A|09/09/99 à 9h09|
|192.168.0.2/24|D3:54:20:00:FF:23|15/09/99 à 8h00|

#### Vérifiez votre serveur DHCP grâce à l’invite de commandes

Si vous êtes connecté à Internet depuis votre ordinateur ou votre smartphone, un serveur vous a sans doute attribué une adresse IP. Vous pouvez d’ailleurs le vérifier sous Windows en ouvrant une invite de commandes et en tapant :

ipconfig /all

[![Résultat de la commande ipconfig /all](https://user.oc-static.com/upload/2021/05/26/16220345633608_image1.png)](https://user.oc-static.com/upload/2021/05/26/16220345633608_image1.png)

Résultat de la commande ipconfig /all

On retrouve sur l’image ci-dessus :

- l’adresse IP qui a été attribuée par le serveur DHCP ;
    
- la date d’expiration du bail ;
    
- l’adresse IP du serveur DHCP.
    

### Configurez le service DHCP sous Packet Tracer

Pour ajouter le service DHCP sur un réseau, vous avez besoin de 2 éléments :

- un serveur DHCP correctement configuré pour attribuer les IP ;
    
- un ou plusieurs clients configurés pour demander une adresse IP.
    

Voici une architecture de réseau simple munie d’un serveur et de 2 clients. Je vous propose de la configurer ensemble.

[![Réseau DHCP avec 2 clients et un serveur](https://user.oc-static.com/upload/2021/06/21/16242724852262_P3C1-2.png)](https://user.oc-static.com/upload/2021/06/21/16242724852262_P3C1-2.png)

Réseau DHCP avec 2 clients et un serveur

#### Configurez le serveur

Pour configurer le serveur, choisissez d’abord l’adresse IP du réseau que vous allez utiliser. Prenons ici le réseau 1.0.0.0/8.

Suivez ensuite les différentes étapes de configuration :

- Configurez une adresse IP sur le serveur. On prendra par exemple 1.0.0.1.
    
- Activez le service DHCP.
    
- Configurez la plage d’adresses IP à attribuer aux machines. On appelle souvent cette plage un _pool d’adresses_.
    

Dans un réseau avec serveur DHCP, la seule adresse IP à configurer manuellement est celle du serveur DHCP lui-même.

#### Configurez le client

Pour configurer le client, il suffit de sélectionner une option pour récupérer automatiquement une adresse IP.


### Ajoutez un serveur DHCP à un réseau existant

Monsieur Falman, de l’auto-école Tinos, vous contacte pour une nouvelle mission. L’entreprise Cyclade avec laquelle il travaille s’agrandit, et son directeur aimerait que les nouveaux postes utilisateurs, des ordinateurs portables, puissent se connecter automatiquement au réseau.

Ses employés font des allers-retours réguliers pour démarcher des collectivités. Ils ont donc besoin de récupérer une adresse IP automatiquement quand ils se branchent au réseau. 2 nouveaux employés équipés de PC portables sont arrivés, mais les embauches vont continuer.

[![Réseau de l'auto-école Tinos et de Cyclade](https://user.oc-static.com/upload/2021/06/21/16242700635298_P3C1-3.png)](https://user.oc-static.com/upload/2021/06/21/16242700635298_P3C1-3.png)

Réseau de l'auto-école Tinos et de Cyclade

### À vous de jouer !

Vous allez mettre en place un service **DHCP** dans l’architecture de Cyclade.

1. **Ajout du serveur DHCP**
    
    - Ajoutez un serveur DHCP à l’architecture.
        
    - Adressez-le avec l’IP **192.168.100.250/24**.
        
2. **Ajout de postes clients**
    
    - Ajoutez **2 PC portables** (clients mobiles) au réseau.
        
3. **Configuration du serveur DHCP**
    
    - Le réseau utilisé est **192.168.100.0/24**.
        
    - Attention : deux postes fixes possèdent déjà une adresse statique dans ce réseau (**192.168.100.1** et **192.168.100.2**) et ne doivent pas être modifiés.
        
    - Configurez le serveur DHCP pour qu’il attribue automatiquement des adresses IP **dans la plage 192.168.100.100 à 192.168.100.200**.
        
4. **Configuration des clients mobiles**
    
    - Configurez les deux PC portables pour qu’ils obtiennent une adresse IP automatiquement (DHCP).
        
5. **Vérification**
    
    - Assurez-vous que les deux clients mobiles ont bien reçu une adresse IP **dans la plage spécifiée**.
        
    - Testez la connectivité entre les machines.
- Vous avez peut-être remarqué que, dans la fenêtre de configuration du serveur DHCP, vous pouvez indiquer :

- la plage d’adresses IP à attribuer aux clients 
    
- la passerelle par défaut
    
- le serveur **DNS**
    

Nous avons laissé le champ “serveur DNS” libre car nous n’en avons pas sur notre réseau. Mais je vous propose de vous pencher sur ce sujet dans le prochain chapitre !

### En résumé

- L’adresse IP est indispensable à toute machine et doit être configurée au préalable.
    
- Le protocole DHCP permet de distribuer automatiquement des adresses IP de la manière suivante : un client réclame une adresse IP sur le réseau, le serveur répond en envoyant au client une adresse IP valide.
    
- Pour configurer cette fonctionnalité, vous devez :
    
    - préciser au serveur la plage d’adresses IP qu’il peut distribuer ;
        
    - indiquer au client que sa configuration IP se fait automatiquement.
        

_Vous savez maintenant automatiser l'attribution d'adresses IP grâce au serveur DHCP. découvrez dans le dernier chapitre de ce cours comment faciliter l'identification de vos machines !_