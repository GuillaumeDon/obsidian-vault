
# **Concevez votre réseau TCP/IP**

# Partie 1

## Créez l’architecture physique de votre réseau

**Contexte** : Tout au long de ce cours, vous serez mis dans un vrai contexte professionnel en vous glissant dans la peau d'un nouvel arrivant dans une entreprise spécialisée en conception de réseaux informatiques. Vous suivrez l’évolution du réseau de l'auto-école Tinos, qui vous demandera régulièrement conseil.

Vous partirez d’un **réseau simple**, pour aboutir en fin de cours à une vraie **architecture de petite entreprise**. En ajoutant petit à petit des briques essentielles d’un réseau, vous allez acquérir les compétences de base pour créer un réseau informatique.

## Découvrez l’organisation d’un réseau

### **Appréhendez la notion de réseau**

Il existe différents types de réseaux informatiques :

**Les LAN (Local Area Network)**

Les LAN sont des réseaux à échelle locale, tels que les réseaux domestiques de votre domicile, ou les réseaux à l’échelle d’une entreprise.

**Les MAN (Metropolitan Area Network)**

Les MAN sont déployés à l’échelle d’une ville. Il peut s’agir, par exemple, de réseaux universitaires qui connectent différentes facultés d’une même ville. Ils sont eux-mêmes constitués de LAN qui, ensemble, forment un MAN.

**Les WAN (Wide Area Network)**

Les WAN sont des réseaux à échelle mondiale, dont le plus connu est Internet. Ce dernier est lui-même composé de MAN et de LAN.

==En tant que technicien, j'interviendrai très souvent sur des LAN (sauf si je travaille pour une grosse compagnie de téléphone)==

### **Identifiez les éléments physiques d’un réseau**


![[Pasted image 20251018111756.png]]

Ceci est ce qu'on appel un **schéma logique**. Il va représenter : 

- l'architecture du réseau ;
- certains aspects de sa configuration logicielle.

==En tant que technicien informatique, vous devez donc être en mesure de lire ce type de schéma pour comprendre, créer et configurer votre réseau.==

Ceci est un réseau de type LAN.
- Aux extrémités du réseau, en bleu, se trouvent les **équipements terminaux** : PC, téléphones, serveurs, imprimantes. Ces éléments peuvent avoir besoin de s’échanger des données.
    
- Au centre du réseau, en vert, se trouvent les **équipements d’interconnexion** : switchs et routeurs. Ils sont au cœur du réseau car ils relient plusieurs équipements entre eux.
    
- Les traits entre les différents éléments représentent les **supports de communication**. Ce sont des câbles qui permettent de relier 2 équipements entre eux.

### **Distinguez schéma logique et schéma physique**

En fonction de la mission que vous devez réaliser, vous pourrez rencontrer 2 types de schémas :

- Le schéma logique pour concevoir, modéliser et configurer votre réseau.
    
- Le schéma physique pour déployer le réseau, installer et câbler le matériel.
    

Le schéma physique apporte d’autres types d’informations :

- la localisation physique des équipements (ville/bâtiment/salle) ;
    
- le nombre de câbles utilisés pour relier les éléments ;
    
- le nombre exact de machines sur le réseau ;
    
- une vue plus détaillée des équipements d’interconnexion.
    

Il se présente également de manière différente.
![[Pasted image 20251018112714.png]]

==Parfois, vous trouverez des informations propres à un schéma physique dans un schéma logique, et inversement. Je vous conseille de consulter les deux, s’ils existent. L’important est de ne pas surcharger un schéma d’informations, au risque de le rendre incompréhensible.

### **Découvrez votre première mission**

<mark style="background-color:green">Vous venez d’arriver au sein d’une **ESN** (entreprise de services du numérique) spécialisée dans la conception de réseaux. Votre manager vous demande d’intervenir pour **Tinos**, une toute nouvelle auto-école.

Pour le moment, l’entreprise est constituée d’une seule personne : le dirigeant, M. Falman.

Votre mission est de connecter son PC à un serveur de stockage situé dans les locaux de l’entreprise : une pièce de 20 m² prêtée par la collectivité pour soutenir le lancement de l’activité.

Le dirigeant souhaite avant tout avoir un réseau sécurisé. Il a beaucoup insisté sur ce point.

Pour mener à bien cette première mission, vous décidez de réaliser en premier lieu le schéma de ce réseau. Votre manager vous propose d’utiliser un **outil de simulation**. </mark>


### **En résumé**

- Les réseaux permettent l’échange de données entre différents équipements informatiques.
    
- Il existe différents types de réseaux en fonction de leur taille : du réseau privé domestique ou en entreprise (un LAN) jusqu’au réseau Internet (un WAN).
    
- La structure physique d’un réseau est toujours composée d’équipements terminaux (les PC, serveurs, imprimantes...), d’équipements d’interconnexion, et de supports de communication pour relier les différents éléments.
    
- Pour appréhender les architectures réseau complexes, vous devez les schématiser.
    
- Il existe deux grands types de schémas réseau : le schéma logique pour comprendre l’architecture générale d’un réseau, et le schéma physique pour mener les opérations d’installation et de câblage.