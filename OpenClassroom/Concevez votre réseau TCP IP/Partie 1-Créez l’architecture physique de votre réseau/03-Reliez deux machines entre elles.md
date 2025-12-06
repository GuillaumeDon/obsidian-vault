## Identifiez les émetteurs-récepteurs

Avant de créer un réseau sous Packet Tracer, vous devez identifier les éléments que vous devez mettre en réseau.

Commençons ici par présenter les équipements qui initient la communication : les machines. Ces dernières sont les interlocuteurs, émetteurs et récepteurs des messages.

J’emploie volontairement le mot _machine_, terme très générique car il comprend :

- les ordinateurs, tablettes, smartphones que vous utilisez au quotidien ;
    
- les serveurs sur lesquels vous stockez, hébergez, consultez des informations ;
    
- les téléphones fixes qui sont désormais des terminaux numériques au même titre qu’un ordinateur ;
    
- les imprimantes, photocopieuses ou autres matériels de numérisation ;
    
- les objets connectés : réfrigérateurs, fours, voitures.

**Leur point commun, c’est leur capacité à traduire un message humain (voix, image, vidéo, texte) en message numérique, ou langage binaire.**

## **Déterminez le bon support de communication**

#### **Identifiez les différents types de supports de communication**

Dans le monde des réseaux, il existe 3 types de supports de communication :

- le **câble en cuivre**, dont le plus utilisé est le **câble à paires torsadées** ;
    
- le **câble optique** ou **fibre optique** ;
    
- l’**air**, si on souhaite communiquer sans fil.

==Le câble en cuivre à paires torsadées peut également s’appeler “câble réseau”, “câble Ethernet” ou encore “câble RJ45”. Ces dénominations ne sont pas tout à fait correctes, mais les professionnels ont pris l’habitude de les utiliser dans la pratique. La plupart du temps, elles désignent bien le câble à paires torsadées.

#### **Prenez en compte différents paramètres pour choisir votre support de communication**

Vous choisirez votre support en fonction de plusieurs paramètres :

- le type d’équipement à raccorder : PC, serveur, téléphone, tablette… ;
    
- la distance qui sépare 2 équipements entre eux ;
    
- l’environnement extérieur : perturbation, humidité... ;
    
- l’usage : mobilité des usagers, débits.
    

Le tableau ci-dessous vous aidera à y voir plus clair.

![[Pasted image 20251018122902.png]]
Le support le plus couramment utilisé est le câble réseau en cuivre à paires torsadées. Il est compatible avec la majorité des équipements, offre de très bons débits et une très bonne sécurité. C’est un câble solide et peu coûteux. Il est idéal pour connecter des employés qui travaillent sur des postes fixes à leur bureau.

En revanche, il ne sera pas adapté si vos équipements sont séparés de plus de 100 m, ni si votre réseau est soumis à beaucoup de rayonnement électromagnétique. Dans ces cas-là, vous devrez privilégier la fibre (ou câble) optique. Du fait des contraintes liées à leur fragilité, les fibres optiques sont très rares dans les installations domestiques. Mais il est courant de voir des serveurs d’entreprise connectés par fibre optique, et sur les réseaux MAN et WAN, c’est le support de transmission privilégié.

Enfin, si vous souhaitez apporter à vos usagers une certaine mobilité en leur évitant d’utiliser des câbles, privilégiez les liaisons sans fil. Les réseaux des universités choisissent toujours ce type de liaison car les étudiants ont besoin de se connecter partout sur le campus. Attention cependant : les liaisons sans fil sont moins sécurisées que les liaisons filaires.

### **Raccordez vos machines au support choisi**
Maintenant que vous avez choisi votre type de support de communication, vous pouvez l’utiliser pour relier vos machines.

#### **Identifiez la carte réseau de votre machine**

Pour cela, vérifiez que vos machines sont équipées d’une **carte ou interface réseau**. C’est une carte électronique munie d’un port pour y connecter le support choisi précédemment.

![[Pasted image 20251018123412.png]]
Dans la majorité des cas, une carte réseau sera déjà présente sur la machine, car il s’agit d’un périphérique ou composant d’un ordinateur aujourd’hui indispensable, au même titre qu’une carte son ou une carte graphique. Si ce n’est pas le cas, il va falloir équiper votre machine.

Vous pouvez afficher la/les carte(s) réseau de votre ordinateur très facilement. Si vous êtes sous Windows 10 :

1. Ouvrez la fenêtre “Exécuter” avec le raccourci clavier Windows + R.
    
2. Entrez “ncpa.cpl” et validez.

![[Pasted image 20251018123533.png]]

#### **Le rôle de la carte réseau**

Le rôle de la carte réseau est de transformer les données binaires à envoyer, en électricité, lumière ou ondes électromagnétiques, afin qu’elles puissent voyager sur le support de transmission choisi.

#### **Les différents types de cartes réseau**

Chaque type de carte réseau est associé à un port et à un support de transmission, tout cela étant régi par des **normes**.

![[Pasted image 20251018123843.png]]

La norme régissant les réseaux LAN et MAN porte le joli nom de **IEEE 802**. Elle contient tout un ensemble de sous-normes pour des catégories de réseaux plus spécifiques.

![[Pasted image 20251018124027.png]]


Le problème majeur des communications sans fil est la **sécurité**. En Wi-Fi, les messages transitent dans l’air, ce qui veut dire que potentiellement n’importe qui pourra les lire. Pour éviter ce désagrément, des **mécanismes de chiffrement** ont été mis en place. Ces mécanismes font intervenir l’usage d’une clé de chiffrement type WPA (pour _Wi-Fi Protected Access_) lors de la connexion.


==Si vous optez pour les technologies sans fil, soyez vigilant ! La mobilité des usagers se fait toujours au détriment de la sécurité et de la fiabilité.

### **Créez un réseau simple entre 2 machines**

<mark style="background-color:green">Vous voilà de retour dans votre ESN pour vous pencher sur la mission Tinos auto-école. Le client, M. Falman, souhaite transférer des données entre son ordinateur fixe et son serveur de stockage. Il ne dispose pour l’instant que de ces deux machines dans son local. 

#### **Choisissez votre support de communication**

Vous n’avez qu’un seul support de communication à choisir puisqu’il n’y a qu’une seule liaison à réaliser : celle entre l’ordinateur du dirigeant et son serveur.

Vous savez aussi que :

- Le serveur et l’ordinateur sont des machines fixes, situées dans la même pièce et séparées de quelques mètres.
    
- La contrainte majeure est la sécurité des données.
    

C’est évidemment le **câble réseau en cuivre** qu’il faut privilégier ici. Les 2 machines devront donc être équipées d’une carte réseau cuivre. Heureusement, le client vous a assuré que c’était déjà le cas.


</mark>

correction :

![[Pasted image 20251018125212.png]]

### **En résumé**

- Pour raccorder entre elles 2 machines, vous pouvez utiliser des câbles réseau en cuivre à paires torsadées, ou câbles dits Ethernet, des fibres optiques, ou utiliser une liaison sans fil.
    
- Choisissez vos supports de transmission en fonction de l’environnement physique dans lequel sont les machines.
    
- La carte réseau présente sur chaque machine se raccorde au support de communication via un port, ou via une antenne pour les liaisons sans fil. Elle convertit le message avant de l’envoyer sur ce support.
    
- La conformité du matériel réseau est garantie par des normes :
    
    - la norme IEEE 802.3 ou “Ethernet” pour les réseaux câblés ;
        
    - la norme IEEE 802.11 pour les réseaux sans fil (WLAN).
        

- Si vous utilisez une liaison sans fil, c’est la norme de Wi-Fi (802.11) qui sera utilisée. 
    

_Vous avez raccordé les deux 2 machines de l’entreprise Tinos entre elles, bravo ! Rendez-vous au prochain chapitre pour ajouter un équipement d’interconnexion à votre réseau._