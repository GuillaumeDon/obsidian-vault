
Nous avons déjà présenté les équipements terminaux et les différents supports de communication qui les relient. Reste à voir le cœur du réseau : les **équipements d’interconnexion**.

Vous avez sans doute remarqué sur le schéma ci-dessus qu’il y en a 2 types :

- ceux qui permettent d’interconnecter les PC, imprimantes, serveurs… Ce sont les **switchs** ;
    
- ceux qui permettent de lier l’ensemble : les **routeurs**.
### **Identifiez les particularités du switch**

Le switch est le premier équipement d’interconnexion que vous rencontrerez dans un réseau, car il est au plus près des machines.

Le switch est également appelé **commutateur** en français, mais le terme switch est largement plus démocratisé.

Il va avoir le même rôle qu’un rond-point sur un réseau routier, ou plus précisément qu'un aiguillage sur un réseau ferré. En plus d’être une intersection entre plusieurs directions, il est capable d’orienter les messages dans la bonne direction. C’est vraiment l'élément de base pour relier plusieurs machines.

![[Pasted image 20251018132919.png]]

Tous les switchs ne se valent pas en termes de caractéristiques, et ils se différencient principalement par :

- **le nombre de ports** allant de 4 à 96, permettant d’y connecter autant de machines ;
    
- **le type de port** : port RJ45 pour les câbles réseau standard, ou interface optique (type SFP+) pour la fibre optique. Ce sont les plus courants ;
    
- **le débit possible** sur chaque port : de 10 Mbp à 100 Gbp ;
    
- **les fonctionnalités** telles que l’interface de configuration, la compatibilité ou les modes de communication.


![[Pasted image 20251018133153.png]]

Le switch est le grand frère du **hub**, ou **concentrateur**, en français. Un hub est un switch non intelligent, c’est-à-dire qu’il n’est pas capable de déterminer vers quelle direction (sur quel port), il doit envoyer un message. Il envoie alors le message sur tous ses ports en partant du principe que de cette manière, le message arrivera bien à destination.

Cela pose des problèmes de sécurité et d’encombrement inutile du réseau, voilà pourquoi les hubs sont devenus très rares et ne conviennent pas à des réseaux d’entreprise. Les switchs et les hubs sont le cœur des réseaux locaux. En revanche, pour communiquer vers des réseaux nationaux ou internationaux, vous devrez utiliser un nouvel équipement : **le routeur**.

### **Identifiez les particularités du routeur**

Le routeur est indispensable pour communiquer entre 2 réseaux. Il faut le voir comme le pont entre ces 2 réseaux, comme une passerelle entre deux mondes. On l’appelle d’ailleurs justement la “passerelle”. Pour reprendre l’analogie avec les réseaux routiers, on peut le voir comme une frontière, ou plus précisément un poste de douane entre 2 pays.


![[Pasted image 20251018133528.png]]

Le routeur a 3 fonctions :

- il sépare 2 réseaux aux règles parfois différentes ;
    
- il décide quel message a le droit de passer ou non ;
    
- si besoin, il aiguille les messages dans la bonne direction, comme le switch.
    

Comme pour le switch, vous choisirez votre routeur en fonction du nombre de ports dont il dispose, du type de ports, de son débit et de ses fonctionnalités.
Contrairement au switch, il ne dispose que de très peu de ports (souvent 2 ou 3).

==Si vous disposez d’une connexion Internet, vous avez sans doute déjà un routeur chez vous. Hé oui, pour faire la passerelle entre votre réseau domestique et Internet, il vous faut obligatoirement un routeur : votre **box Internet**.

Les box Internet sont des routeurs un peu particuliers qui intègrent aussi un switch, un décodeur TV, un serveur de stockage, et sans doute plein d’autres choses. Mais leur rôle initial est de permettre à vos messages de traverser les réseaux, et donc de vous fournir un accès à Internet.

### **Créez 2 réseaux connectés entre eux**

<mark style="background-color:green">Maintenant, vous allez pouvoir finaliser le projet de votre client, qui, je vous le rappelle, souhaitait que son PC et celui de son collaborateur soient tous les 2 raccordés au serveur de stockage.

Mais avant cela, je vous conseille de visionner la vidéo ci-dessous pour savoir comment ajouter les équipements d’interconnexion à votre réseau. </mark>

==Lorsque l’on souhaite raccorder des équipement terminaux à des switchs, il faut utiliser des câbles droits, sinon les équipements n’arriveront pas à communiquer.

corrigé : 
![[Pasted image 20251018140851.png]]


#### **Reliez deux réseaux entre eux**

<mark style="background-color:green">Un an plus tard, Tinos auto-école vous sollicite une nouvelle fois pour une mission de conseil. L’espace de travail que l’entreprise loue est partagé entre plusieurs entreprises. Or, Cyclade, l’une des entreprises voisines, collabore régulièrement avec Tinos. Les deux entreprises ont besoin d'échanger des fichiers de plusieurs téraoctets.

Le client veut donc une architecture réseau qui réponde à ses besoins.

- Ajoutez un réseau externe composé des 2 PC de l’entreprise Cyclade.
    
- Interconnectez ces 2 réseaux.

</mark >

Dans ce scénario, seul le serveur de Tinos est utilisé par les deux entreprises. Cyclade ne dispose pas de son propre serveur. 

Corrigé : 
![[Pasted image 20251018141249.png]]

### **En résumé**

- Pour raccorder plus de 2 machines entre elles, vous devez nécessairement intégrer des équipements d’interconnexion à votre réseau initial.
    
- Il existe 2 types d’équipement d’interconnexion : les switchs et les routeurs.
    
- Les switchs s’utilisent au sein d’un réseau local pour raccorder tous les équipements terminaux entre eux. 
    
- Un seul switch peut interconnecter plusieurs dizaines de machines, tel un rond-point au carrefour de plusieurs destinations.
    
- Pour raccorder un réseau local avec un autre réseau, vous devez intégrer un routeur. Il joue le rôle de passerelle entre différents réseaux. 
    

_Vous avez créé l'architecture physique de votre réseau : bravo ! ![:D](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABMAAAATCAMAAAEyifZoAAAAYFBMVEX/wWn/+an/6pj/tl3/3Yn/x3D/7p3/2YT/tFr/1X//0Xz/5JH/znf/9KP/+6z/xG3/7Jr/vWX/9qX/umH/uF//4Y3/y3T//7D//a7Xl0v/sliodjrmolD///8AAAD///8Zo1IxAAAAIHRSTlP/////////////////////////////////////////AFxcG+0AAADcSURBVBhXXU9HbgRBEGLybF7H7krw/1/6MFpLdp0QIKAgCmwOuSChL+AJeu8boawCJEpgHyGM7QJiqUpBvlOQOK5fJ0rQs4dZLC5wHjMz3QnxI6vyjYIkkZIESSQPFOu4hQRNvd3nswkc2PrMTyLfWxtOj92Ql8zMdAPPVVXlhOyjqtwEKdwR/5IlkeHucdQe6nQb7sNtnLerHT7GrTfSupHXxxQUGM+hR2utr9s1lsmDYF7Wobd+X7dvYHI3gnGes16XvgchBh75S73F8Tpt98zM/Fzszz4ze+37AYEhIfY+Uk6xAAAAAElFTkSuQmCC ":D") Prochaine étape : configurer la communication au sein de votre réseau. Mais avant, je vous propose de tester vos connaissances avec un quiz !_