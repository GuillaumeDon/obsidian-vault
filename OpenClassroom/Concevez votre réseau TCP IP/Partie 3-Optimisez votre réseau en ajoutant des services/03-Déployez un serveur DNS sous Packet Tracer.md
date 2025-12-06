
### Déployez un serveur DNS sous Packet Tracer

Je vais à présent vous montrer comment configurer le service DNS sur un réseau LAN composé de 2 PC et d’un serveur DNS, reliés par un switch :

[![Architecture LAN avec 2 PC et un serveur DNS](https://user.oc-static.com/upload/2021/06/21/16242711199124_P3C2-2.png)](https://user.oc-static.com/upload/2021/06/21/16242711199124_P3C2-2.png)

Architecture LAN avec 2 PC et un serveur DNS

#### Configurez le serveur

Pour configurer le serveur, il faut :

- activer la fonction DNS ;
    
- remplir la table de correspondance Nom-IP avec 3 entrées :
    

|   |   |
|---|---|
|Nom|Adresse IP|
|pc1|192.168.0.1|
|pc2|192.168.0.2|
|serveur_dns|192.168.0.250|

Lorsque vous configurez des noms de DNS, respectez la règle d’or suivante : ne mettez pas de caractères spéciaux, de majuscules ou d’espaces dans le nom de vos machines. Cela vous évitera bien des problèmes ! Vous pouvez consulter la [norme officielle en anglais](https://www.ietf.org/rfc/rfc1035.txt) pour en savoir plus !

#### Configurez les clients

Pour configurer les clients, il suffit de renseigner l’adresse IP du serveur DNS.

### Ajoutez un serveur DNS à un réseau existant

L’entreprise Cyclade est maintenant dotée d’un serveur DHCP. Le gérant envisage de créer un site web interne dans le but de faire l’inventaire des pièces de vélo disponibles. Vous lui proposez d’ajouter la fonctionnalité DNS. De cette manière, il sera beaucoup plus simple pour les employés d’accéder au site via un nom plutôt que via une IP.

#### À vous de jouer !

Configurez et testez le service DNS du réseau :

- Activez la fonctionnalité DNS au serveur DHCP déjà présent.
    
- Ajoutez dans la table DNS les machines :
    
    - 192.168.100.1 associée au nom pc1 ;
        
    - 192.168.100.2 associée au nom pc2 ;
        
    - 192.168.100.250 associée au nom serveur1.
        
- Sur ces 3 machines, renseignez l’adresse IP du serveur DNS.
    
- Testez un ping entre pc1 et pc2 en utilisant le nom de la machine à la place de son IP.
    
- Ajoutez un nouveau serveur à votre réseau pour simuler le serveur web.
    
- Vérifiez que les PC peuvent accéder au serveur avec leur navigateur web. L’adresse IP de ce serveur doit être 192.168.100.249/24.
    

Sous Packet Tracer, le navigateur web d’un ordinateur se trouve dans l’onglet “Desktop” sous le nom “Web Browser :

![](https://user.oc-static.com/upload/2021/05/26/1622036962175_image4.jpg)


Félicitations, vous venez de créer un véritable réseau d’entreprise fonctionnel !

Vous n'êtes plus obligés de mémoriser les adresses IP de vos machines, leurs noms suffisent pour communiquer avec elles.

### En résumé

- Pour déployer un DNS sous Packet Tracer, vous devez configurer le serveur et les clients
    
- Pour configurer le serveur, activez la fonction DNS et remplissez la table de correspondance Nom-IP
    
- Pour configurer les clients, renseignez l’adresse IP du serveur DNS
    

_Nous arrivons au terme du cours sur la création de votre premier réseau. Il y aurait encore beaucoup de notions à aborder, comme les règles pour améliorer la sécurité, isoler le trafic au niveau des switch, et bien d’autres. Le monde des réseaux évolue rapidement. Je vous invite ainsi à vous documenter régulièrement pour devenir un expert dans votre domaine._