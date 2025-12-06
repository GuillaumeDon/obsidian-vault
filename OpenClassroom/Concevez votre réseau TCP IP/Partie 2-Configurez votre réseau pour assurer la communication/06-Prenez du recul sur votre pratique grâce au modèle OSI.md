
### Découvrez le modèle OSI

L’objectif d’un réseau, nous l’avons dit dès le début du cours, c’est de permettre aux machines de communiquer entre elles. Or, dans un réseau quel qu’il soit, tous les interlocuteurs (ou machines) sont différents.

Les **règles d’uniformisation** sont nécessaires pour permettre les communications.

Il existe 2 catégories de règles dans les réseaux informatiques :

- les règles matérielles qu’on appelle plutôt des normes ;
    
- les règles logicielles ou **protocoles**.
    

Nous avons déjà vu plusieurs de ces règles d’uniformisation, comme :

- l’utilisation de RJ45 comme connecteur pour les réseaux cuivre ;
    
- la nécessité d’une adresse IP sur les machines d’un réseau.
    

Mais il en existe bien d’autres !

Le **modèle OSI** propose de classer chacune de ces règles à différents niveaux, sur un total de 7 niveaux qu’on appelle aussi des _couches_. Chacune de ces couches porte un nom relatif à sa fonction.

[![Schéma illustrant le modèle OSI et le rôle des 7 couches du modèle.](https://user.oc-static.com/upload/2021/06/01/16225670098336_P2C5-1.png)](https://user.oc-static.com/upload/2021/06/01/16225670098336_P2C5-1.png)

Le modèle OSI classe les différentes règles de communication d'un réseau en 7 couches

Faisons encore une fois l’analogie avec l’envoi d’un courrier postal.

Comme vous êtes un petit-fils ou une petite-fille génial(e), vous décidez d’écrire une lettre pour souhaiter un bon anniversaire à votre grand-mère adorée. Entre cet instant et le moment où Mamie va découvrir ce que vous lui avez écrit dans la lettre, une multitude de règles vont entrer en jeu.

Il y a évidemment les règles dont on a déjà parlé, comme le fait de devoir inscrire le nom du destinataire sur l’enveloppe. Mais si on prend vraiment du recul, elles sont bien plus nombreuses. Vous ne voyez pas ? Laissez-moi vous donner quelques exemples :

- Si vous décidez d’écrire une lettre à la main en français, vous allez respecter les règles grammaticales du français.
    
- Vous allez mettre cette lettre dans une enveloppe, et inscrire à un emplacement bien défini le nom et l’adresse de votre grand-mère. 
    
- La lettre sera ensuite postée dans un type de boîte à lettres bien précis correspondant au transporteur que vous voulez utiliser, le plus souvent La Poste.
    
- Une fois la lettre remise au transporteur, celui-ci va trier le courrier par région, puis le regrouper par destination avant de le mettre dans des véhicules répondant à un cahier des charges de fabrication, véhicules qui permettront de faire la distribution.
    

Quand je vous disais qu’il fallait prendre du recul…

Chacune des règles que je viens de citer participe d’une manière ou d’une autre à l’objectif de souhaiter un joyeux anniversaire à votre grand-mère, mais elles ne sont pas utiles pour tous les acteurs du processus.

Le facteur se moque que vous ayez écrit votre lettre en français, en hébreu ou en latin, ça ne l'empêchera pas de faire son travail. Par contre, il aura besoin de l’adresse de destination sur l’enveloppe.

De la même manière avec le modèle OSI, chaque acteur ou “élément” du réseau aura besoin des règles d’une couche bien spécifique. Les règles des autres couches ne l'intéresseront pas, et souvent il ne les comprendra même pas.

On peut alors associer chaque élément à une couche :

[![Schéma représentant les 7 couches du modèle OSI et les éléments du réseau associés. Le routeur, le switch, la carte réseau les répéteurs, câbles et hub sont associés aux couches 1 à 3. Le pare-feu et l'ordinateur sont associés aux couches 4](https://user.oc-static.com/upload/2021/06/01/16225671036921_P2C5-2.png)](https://user.oc-static.com/upload/2021/06/01/16225671036921_P2C5-2.png)

Les 7 couches du modèle OSI et les éléments du réseau associés

Ce modèle étant très détaillé, il permet de bien comprendre les étapes de création et d’acheminement d’un message. Cependant,  un autre modèle plus simple avec moins de couches a aussi été proposé : le modèle TCP/IP.

### Le modèle TCP/IP

Le modèle TCP/IP ne comporte que 4 couches. Il est beaucoup moins complexe et plus applicable à la réalité que le modèle OSI.

[![Comparaison des modèles OSI et TCP/IP. A gauche le modèle OSI, à droite le modèle TCP/IP.](https://user.oc-static.com/upload/2021/06/01/16225672656323_P2C5-3.png)](https://user.oc-static.com/upload/2021/06/01/16225672656323_P2C5-3.png)

Comparaison des modèles OSI et TCP/IP

Ce modèle porte le nom des 2 protocoles les plus importants qui le constituent.

#### **Le protocole IP**

Il est situé dans la couche Internet dont l’équivalent est la couche 3 du modèle OSI : la couche Réseau. Vous connaissez déjà l’IP pour son système d'adressage.

#### **Le protocole TCP** (Transmission Control Protocol, pour "protocole de contrôle de transmission")

Il se situe dans la couche Transport, dont l’équivalent est la couche 4 du modèle OSI qui porte le même nom. Son rôle est d’établir des règles permettant de transporter un message de la source à la destination, en s’assurant que rien n’ait été perdu en route.

Parmi ces règles, on trouve le fait de devoir numéroter chaque paquet. Lorsqu’un message est trop long pour être envoyé en un seul paquet, il est découpé en plusieurs parties mises dans différents paquets qu’il faut numéroter.

Toutes les règles ou consignes nécessaires pour communiquer un message sur un réseau doivent être envoyées dans le paquet contenant le message en question. Le paquet est alors constitué du message à envoyer, sur lequel viennent s’ajouter toutes les consignes nécessaires, classées par couches. C’est ce qu’on appelle le mécanisme d’**encapsulation**.

Voilà à quoi ressemble schématiquement un message encapsulé suivant le modèle TCP/IP :

[![Représentation d'un paquet à envoyer, constitué des 5 consignes encapsulées.  Les 4 premiers éléments forment l'en-tête. Le dernier élément forme les données.](https://user.oc-static.com/upload/2021/06/01/16225673456417_P2C5-4.png)](https://user.oc-static.com/upload/2021/06/01/16225673456417_P2C5-4.png)

Encapsulation d'un message suivant le modèle TCP/IP

Chaque “élément intermédiaire” du réseau, que ce soit le routeur, le switch ou l’application destinataire, piochera alors dans ce paquet les consignes qui lui sont destinées.

### Faites le lien avec vos pratiques

Le modèle TCP/IP traduit plus fidèlement la réalité des communications sur les réseaux IP. Cependant, il reste moins détaillé que le modèle OSI.

Ainsi, dans la pratique, on continue à associer les équipements réseaux avec leur couche du modèle historique, le modèle OSI.

Si vous entendez parler par exemple d’un “équipement L3”, ou “équipement de niveau 3”, cela fait référence à un équipement associé à la couche "Réseau”, capable de comprendre des informations comme des adresses IP. Le routeur est un équipement de niveau 3.

### **À vous de jouer !**

Maintenant que vous connaissez les différentes couches du modèle OSI, identifiez sur l’architecture réseau à quelle couche du modèle OSI est associé chacun des équipements qui le composent.

![](https://user.oc-static.com/upload/2021/05/26/16220220459178_image12.png)

#### **Corrigé**

Vous pouvez consulter le [corrigé](https://s3.eu-west-1.amazonaws.com/course.oc-static.com/courses/6944606/P2C6+-+corrige%CC%81.pdf) pour vérifier votre travail.

Il y a énormément de protocoles de niveau 7, parmi lesquels le plus connu est sans doute HTTP. Ce protocole permet l’échange et l'ouverture de pages web. C’est lui qui a fait le succès d’Internet !

### En résumé

- Le modèle OSI permet de classer, sur plusieurs niveaux, les règles ou protocoles qui rendent possibles les communications sur un réseau.
    
- Ce modèle est composé de 7 couches portant toutes un nom indiquant leur fonction. Dans l’ordre, on trouve les couches : Physique, Liaison de données, Réseau, Transport, Session, Présentation, Application.
    
- Chaque protocole et chaque élément du réseau sont associés à une couche précise. Le protocole IP, ainsi que les routeurs qui manipulent et comprennent les adresses IP, sont associés à la couche 3, la couche Réseau.
    
- Le modèle TCP/IP est un modèle similaire en 4 couches.
    
- Lorsqu’un message est généré, il est assemblé avec l’ensemble des règles qui permettent son acheminement. Ce processus d’assemblage s’appelle l’encapsulation.
    

_Vous savez maintenant créer et configurer un réseau pour qu’il soit fonctionnel et utilisable du point de vue d’un technicien._ _Dans la prochaine partie, nous allons voir comment optimiser ce réseau pour faciliter l'accès des utilisateurs finaux. Mais avant, passons au quiz !_