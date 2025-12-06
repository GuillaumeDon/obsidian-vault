
#### Appréhendez les principes de la communication

Pour communiquer correctement, quelle que soit la situation, il est indispensable de connaître :

- La source du message : **qui parle ?**
    
- Le/les destinataires du message : **à qui ?**
    
- Le contenu du message : **pour dire quoi ?**
    

Les machines ont besoin des mêmes informations pour assurer la communication informatique au sein d’un réseau. Et pour identifier la source et la destination d’un message, on utilise différents mécanismes dont **l’adresse MAC**.

### Identifiez l’adresse MAC de votre machine

C’est l’adresse MAC qui sert à identifier les émetteurs et récepteurs des messages.

==Pour être plus exact, l’adresse MAC identifie non pas la machine, mais la carte réseau, car c’est elle qui envoie et reçoit les messages. Si une machine a plusieurs cartes réseaux, elle aura donc plusieurs adresses MAC.

Voici quelques caractéristiques importantes de cette adresse MAC :

- Elle est non modifiable car associée à une carte réseau dès sa fabrication en usine. Certains outils logiciels existent malgré tout pour la modifier, mais il s’agit de cas de figure très spécifiques qui ne nous concernent pas ici.
    
- Elle est unique dans le monde.
    
- Elle s’écrit en **hexadécimal**, un système numérique qui utilise 16 caractères (à la place de 10 en système décimal).
    
- Elle est composée de 6 **octets**.

==Les adresses MAC sont définies par les fabricants de carte réseaux, ce ne sera donc pas à vous de les configurer sur votre réseau. En revanche, vous pourrez avoir besoin de vérifier les adresses MAC associées à vos machines.


<mark style="background-color:lightblue">En informatique, les machines utilisent le système binaire. Elles ne comprennent donc que les valeurs “0” et “1”. Ce type de valeur s’appelle un **bit**. Tous les messages qui transitent sur le réseau ne sont que de longues suites de bits. Un groupe de 8 bits à la suite s’appelle un octet. 

L’adresse MAC écrite sur 6 octets pourrait donc aussi s’écrire sous la forme de 48 bits (6x8=48).</mark>

Dans notre cas, on souhaite récupérer les informations de configuration des cartes réseau, grâce à la commande suivante :

<mark style="background-color:lightgreen">ipconfig /all</mark>

En exécutant cette commande, on peut voir s’afficher beaucoup de cartes réseaux. C’est normal ! Un ordinateur est souvent équipé de beaucoup de cartes réseau : une pour le Wi-Fi, une pour le Bluetooth, une pour Ethernet, et même des cartes réseaux virtuelles !

![[Pasted image 20251018174040.png]]

Une adresse MAC est composée de 2 parties :

- La première moitié (les 3 premiers octets) identifie le fabricant de la carte réseau.
    
- La deuxième moitié identifie la carte réseau elle-même.

![[Pasted image 20251018174004.png]]


### En résumé

- Pour communiquer, les machines ont besoin de règles. La règle la plus importante à instaurer est d’identifier chaque équipement avec une adresse.
    
- Chaque message qui transite sur le réseau porte l’adresse de la source et du destinataire du message.
    
- L’adresse MAC est un identifiant unique. Cela signifie que deux équipements dans le monde ne pourront jamais avoir la même adresse MAC.
    
- Une adresse MAC est associée à chaque carte réseau d’une machine. Une même machine peut donc avoir plusieurs adresses MAC.
    
- L’adresse MAC s’écrit sur 6 octets et n’est pas à définir par le technicien : elle est inscrite dans le matériel à sa sortie d’usine.
    

_Vous savez désormais identifier votre machine dans un réseau local. Passez au chapitre suivant pour découvrir comment initier la communication !_