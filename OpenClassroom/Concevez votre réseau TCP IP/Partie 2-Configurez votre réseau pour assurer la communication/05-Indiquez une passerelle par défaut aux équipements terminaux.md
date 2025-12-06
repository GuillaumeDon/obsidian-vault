Nous venons de voir que c’est le routeur, grâce à sa table de routage qui se charge de relayer les paquets d’un réseau vers un autre. Jusque là, nous n’en avons pas eu besoin car nous simulions uniquement des communications au sein d’un même réseau IP. Dans ce contexte, le routeur n’a donc aucune utilité.

Par contre, dès qu’une machine veut envoyer un paquet vers d’autres réseaux, il faut lui préciser l’adresse IP du routeur ou passerelle qui va relayer le paquet  vers son réseau de destination. Si on reprend le réseau précédent, il ne reste donc plus qu’à indiquer aux 3 PC quelle sera leur passerelle par défaut.

[![Réseau de 3 PC avec un routeur configurés](https://user.oc-static.com/upload/2021/06/21/16242681205991_P2C4-3.png)](https://user.oc-static.com/upload/2021/06/21/16242681205991_P2C4-3.png)

Réseau de 3 PC avec un routeur configurés

|         |                     |                       |
| ------- | ------------------- | --------------------- |
| Machine | Interface de sortie | Passerelle par défaut |
| PC0     | 192.168.30.1        | 192.168.30.254        |
| PC1     | 192.168.10.1        | 192.168.10.254        |
| PC2     | 192.168.20.1        | 192.168.20.254        |
==Veillez toujours à indiquer la passerelle par défaut à vos équipements terminaux. Cela peut paraître assez futile lorsque vos PCs n’ont qu’une seule interface réseau car il n’y qu’une seule “porte de sortie possible” pour les paquets. Mais souvenez-vous que même votre propre PC peut avoir plusieurs interfaces réseau. Préciser une passerelle par défaut devient alors indispensable pour indiquer quelle interface réseau de sortie utiliser par défaut pour envoyer un paquet.

### Configurez vos équipements avec Cisco Packet Tracer

Ça y est ! Vous avez enfin toutes les clés en main pour mener à bien votre mission auprès de l'auto-école Tinos.

Voilà l’architecture là où vous l’avez laissée :

[![Réseau Tinos et Cyclade avec toutes les machines adressées](https://user.oc-static.com/upload/2021/06/21/16242685272027_P2C3-10.png)](https://user.oc-static.com/upload/2021/06/21/16242685272027_P2C3-10.png)

Réseau Tinos et Cyclade avec toutes les machines adressées

A cette étape, vous avez :

- créé l’architecture du réseau avec tous les équipements et câbles nécessaires
    
- attribué une adresse IP à tous les équipement terminaux
    

La prochaine étape ? Configurer les PC de l’entreprise Cyclade pour qu’ils puissent accéder au serveur de l'auto-école Tinos.

#### **À** **vous de jouer !**

Reprenez votre architecture et réalisez les étapes suivantes :

1. Activez les interfaces réseau du routeurs
    
2. Assignez-leur une adresse IP
    
3. Renseignez la passerelle par défaut sur tous vos équipements terminaux
    
4. Testez la communication entre les 2 machines de Cyclade et le serveur de l'auto-école Tinos. Vous pouvez utiliser le ping ou la simulation de paquets


==Dans cet exercice, vous avez affecté des adresses IP à tous les équipements sauf aux switches. C’est tout à fait normal, car le switch ne comprend pas les adresses IP, il ne comprend que les adresses MAC. 

Chaque équipement réseau fonctionne sur un niveau de compréhension bien différent. Ces niveaux de compréhension ou “couches” sont tous représentés dans ce qu’on appelle le **modèle OSI** et c’est l’objet du prochain chapitre.

Un message qui transite sur le réseau contient beaucoup d’informations qui vont permettre son acheminement. Chaque équipement du réseau comprend certains types d’informations contenues dans ce message.

### En résumé

- Pour qu’une machine envoie des paquets vers un réseau externe, il faut lui indiquer l’adresse IP de sa passerelle par défaut, c’est-à-dire l’adresse IP du routeur qui va relayer les paquets.
    
- Sous Packet Tracer, il suffit de renseigner le champ “Default Gateway” (Passerelle par défaut) dans la configuration de la machine.
    
- Tous les paquets envoyés par cette machine et à destination d’un réseau externe seront alors envoyés à la passerelle qui se chargera de les router correctement.
    

_Pour y voir plus clair, une classification de ces différents types d’information existe et c’est ce que nous allons voir dans le prochain chapitre._