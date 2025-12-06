### Envoyez des messages

Dans le chapitre précédent, vous avez appris à identifier vos machines grâce à l’adresse MAC. Il vous faut désormais les faire communiquer. Communiquer, c’est échanger des messages. Ces messages s’appellent des **paquets** dans le monde des réseaux. 

Pour vérifier que la communication fonctionne entre deux machines, vous allez donc générer un paquet sur la première machine, et l’envoyer sur la deuxième.

### Simulez une communication sur votre réseau avec Packet Tracer

<mark style="background-color:lightgreen">Vous revoilà dans votre entreprise de conseil en réseaux d’entreprise. Après avoir longuement réfléchi à votre proposition précédente, votre client, M. Falman, accepte votre devis et vous demande de réaliser l’architecture que vous lui aviez proposé.

Pour rappel, voilà à quoi ressemblait l'architecture complète, avec les machines de votre client à gauche et celles de son associé, l’entreprise Cyclade, à droite :</mark>

![[Pasted image 20251018183756.png]]

<mark style="background-color:lightgreen">Pour cette mission, votre manager vous propose de travailler en binôme avec un collègue plus expérimenté. Ce dernier a déjà réalisé de nombreux projets sur le terrain. Il vous propose de vous occuper de la partie configuration réseau, tandis que lui s’occupera de l’achat et de l’installation du matériel.

Pour préparer au mieux cette intervention, vous décidez de tout simuler avec Packet Tracer. Vous aviez déjà réalisé toute l’architecture pour établir un devis au client. Il ne vous reste plus qu’à tester la communication entre les machines.

Le client vous précise qu’il souhaite conserver ses adresses IP actuelles :

- 1.1.1.1 pour le serveur ;
    
- 1.1.1.2 pour le PC fixe ;
    
- 1.1.1.3 pour le PC portable.
</mark>

==À cette étape, les adresses IP ne sont pas nécessaires pour l’acheminement des paquets, car le switch comprend uniquement les adresses MAC. Mais pour générer un paquet et donc tester la communication, les machines doivent obligatoirement avoir une adresse IP. Nous verrons dans le chapitre suivant de quoi il s’agit exactement.

Pour le moment, vous ne pouvez faire communiquer des machines que dans un réseau local.

Pour que vos machines aient accès à Internet ou simplement à un autre réseau, il faut que les paquets puissent traverser les réseaux. Et pour cela, l’adresse MAC ne suffit pas. Il va vous falloir un autre type d’adresse qu’on a un peu évoqué et utilisé : **l’adresse IP**.

### En résumé

- Les communications au sein d’un réseau local se font grâce à l’adresse MAC. 
    
- Le switch, lorsqu’il reçoit un paquet, est capable de déterminer, grâce à l’adresse MAC, sur lequel de ses ports transmettre le paquet.
    
- Pour générer un paquet, on a cependant besoin d’affecter une adresse IP aux machines.
    

_Vous avez configuré des communications dans un réseau local : bravo ! Rendez-vous dans le chapitre suivant pour en savoir plus sur l’adresse IP._