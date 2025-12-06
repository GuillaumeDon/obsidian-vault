
### **En résumé**

- Les réseaux permettent l’échange de données entre différents équipements informatiques.
    
- Il existe différents types de réseaux en fonction de leur taille : du réseau privé domestique ou en entreprise (un LAN) jusqu’au réseau Internet (un WAN).
    
- La structure physique d’un réseau est toujours composée d’équipements terminaux (les PC, serveurs, imprimantes...), d’équipements d’interconnexion, et de supports de communication pour relier les différents éléments.
    
- Pour appréhender les architectures réseau complexes, vous devez les schématiser.
    
- Il existe deux grands types de schémas réseau : le schéma logique pour comprendre l’architecture générale d’un réseau, et le schéma physique pour mener les opérations d’installation et de câblage.
### **En résumé**

- Vous pouvez créer une maquette virtuelle de votre réseau grâce à un outil de simulation.
    
- Packet Tracer est un outil de simulation très répandu et développé par Cisco Systems, le leader dans la fabrication d’équipements réseaux. Il existe cependant d’autres outils de simulation.
    
- Packet Tracer vous permettra aussi de simuler des communications au sein de votre réseau virtuel, une fois que l’aurez créé.
    
- Vous pouvez télécharger gratuitement Packet Tracer en vous rendant sur [ce site.](https://www.netacad.com/courses/packet-tracer/introduction-packet-tracer)


### **En résumé**

- Pour raccorder entre elles 2 machines, vous pouvez utiliser des câbles réseau en cuivre à paires torsadées, ou câbles dits Ethernet, des fibres optiques, ou utiliser une liaison sans fil.
    
- Choisissez vos supports de transmission en fonction de l’environnement physique dans lequel sont les machines.
    
- La carte réseau présente sur chaque machine se raccorde au support de communication via un port, ou via une antenne pour les liaisons sans fil. Elle convertit le message avant de l’envoyer sur ce support.
    
- La conformité du matériel réseau est garantie par des normes :
    
    - la norme IEEE 802.3 ou “Ethernet” pour les réseaux câblés ;
        
    - la norme IEEE 802.11 pour les réseaux sans fil (WLAN).
        

- Si vous utilisez une liaison sans fil, c’est la norme de Wi-Fi (802.11) qui sera utilisée. 
    

### **En résumé**

- Pour raccorder plus de 2 machines entre elles, vous devez nécessairement intégrer des équipements d’interconnexion à votre réseau initial.
    
- Il existe 2 types d’équipement d’interconnexion : les switchs et les routeurs.
    
- Les switchs s’utilisent au sein d’un réseau local pour raccorder tous les équipements terminaux entre eux. 
    
- Un seul switch peut interconnecter plusieurs dizaines de machines, tel un rond-point au carrefour de plusieurs destinations.
    
- Pour raccorder un réseau local avec un autre réseau, vous devez intégrer un routeur. Il joue le rôle de passerelle entre différents réseaux. 


### En résumé

- Pour communiquer, les machines ont besoin de règles. La règle la plus importante à instaurer est d’identifier chaque équipement avec une adresse.
    
- Chaque message qui transite sur le réseau porte l’adresse de la source et du destinataire du message.
    
- L’adresse MAC est un identifiant unique. Cela signifie que deux équipements dans le monde ne pourront jamais avoir la même adresse MAC.
    
- Une adresse MAC est associée à chaque carte réseau d’une machine. Une même machine peut donc avoir plusieurs adresses MAC.
    
- L’adresse MAC s’écrit sur 6 octets et n’est pas à définir par le technicien : elle est inscrite dans le matériel à sa sortie d’usine.
    

### En résumé

- Les communications au sein d’un réseau local se font grâce à l’adresse MAC. 
    
- Le switch, lorsqu’il reçoit un paquet, est capable de déterminer, grâce à l’adresse MAC, sur lequel de ses ports transmettre le paquet.
    
- Pour générer un paquet, on a cependant besoin d’affecter une adresse IP aux machines.

### En résumé

- L’adresse IP est nécessaire pour acheminer des messages entre des réseaux différents.
    
- Une adresse IPv4 est écrite sur 32 bits, dont une partie sert à identifier le réseau et l’autre partie à identifier la machine.
    
- L’adresse IP est toujours associée à un masque permettant de savoir où est la limite entre l’identifiant du réseau et l’identifiant de la machine.
    
- L’IPv6 va peu à peu prendre le relais de l’IPv4, car il permet de créer beaucoup plus d’adresses, suffisamment pour toutes les machines connectés du monde.
    
- Un plan d’adressage cohérent doit être élaboré lors de la création du réseau. Il permet de définir les adresses IP qui seront affectées aux machines, et leur nombre.
    

### En résumé

- Lorsqu’un paquet est envoyé d’un réseau IP vers un autre, il passe obligatoirement par un routeur. Ce dernier est la “passerelle par défaut” ; 
    
- Chaque interface réseau du routeur doit être activée et avoir une adresse IP 
    
- La table de routage enregistrée dans un routeur permet à celui-ci d’envoyer un paquet vers le bon réseau. Elle liste tous les réseaux connus du routeur et la route à prendre pour les atteindre ;
    
- Quand un routeur reçoit un paquet, il regarde l’adresse IP de destination inscrite dans le paquet et la compare avec les réseaux connus dans sa table de routage. Il sait alors vers où envoyer ce paquet.

### En résumé

- Pour qu’une machine envoie des paquets vers un réseau externe, il faut lui indiquer l’adresse IP de sa passerelle par défaut, c’est-à-dire l’adresse IP du routeur qui va relayer les paquets.
    
- Sous Packet Tracer, il suffit de renseigner le champ “Default Gateway” (Passerelle par défaut) dans la configuration de la machine.
    
- Tous les paquets envoyés par cette machine et à destination d’un réseau externe seront alors envoyés à la passerelle qui se chargera de les router correctement.
### En résumé

- Le modèle OSI permet de classer, sur plusieurs niveaux, les règles ou protocoles qui rendent possibles les communications sur un réseau.
    
- Ce modèle est composé de 7 couches portant toutes un nom indiquant leur fonction. Dans l’ordre, on trouve les couches : Physique, Liaison de données, Réseau, Transport, Session, Présentation, Application.
    
- Chaque protocole et chaque élément du réseau sont associés à une couche précise. Le protocole IP, ainsi que les routeurs qui manipulent et comprennent les adresses IP, sont associés à la couche 3, la couche Réseau.
    
- Le modèle TCP/IP est un modèle similaire en 4 couches.
    
- Lorsqu’un message est généré, il est assemblé avec l’ensemble des règles qui permettent son acheminement. Ce processus d’assemblage s’appelle l’encapsulation.

### En résumé

- L’adresse IP est indispensable à toute machine et doit être configurée au préalable.
    
- Le protocole DHCP permet de distribuer automatiquement des adresses IP de la manière suivante : un client réclame une adresse IP sur le réseau, le serveur répond en envoyant au client une adresse IP valide.
    
- Pour configurer cette fonctionnalité, vous devez :
    
    - préciser au serveur la plage d’adresses IP qu’il peut distribuer ;
        
    - indiquer au client que sa configuration IP se fait automatiquement.

### En résumé

- Le service DNS permet de faire la correspondance entre des noms de machine et des adresses IPs. De cette manière, les utilisateurs peuvent se passer des adresses IP quand ils naviguent sur internet.
    
- Pour ajouter la fonctionnalité DNS à un réseau, il vous faut un serveur DNS contenant la liste de tous les noms de machines du réseau et leurs adresses IP associées. Ce serveur joue le rôle d’un annuaire de correspondance entre un Nom et une adresse IP
    
- Lorsqu’une machine d’un réseau souhaite communiquer avec une autre machine dont elle ne connaît que le nom, elle demande automatiquement au serveur DNS de lui fournir l’adresse IP associée à ce nom. Elle peut ensuite envoyer son message en utilisant l’adresse IP fournie
### En résumé

- Pour déployer un DNS sous Packet Tracer, vous devez configurer le serveur et les clients
    
- Pour configurer le serveur, activez la fonction DNS et remplissez la table de correspondance Nom-IP
    
- Pour configurer les clients, renseignez l’adresse IP du serveur DNS
    

_Nous arrivons au terme du cours sur la création de votre premier réseau. Il y aurait encore beaucoup de notions à aborder, comme les règles pour améliorer la sécurité, isoler le trafic au niveau des switch, et bien d’autres. Le monde des réseaux évolue rapidement. Je vous invite ainsi à vous documenter régulièrement pour devenir un expert dans votre domaine._