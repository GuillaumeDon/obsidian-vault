### Associez un nom à une adresse IP

Les machines sont identifiées grâce à leurs adresses IP. Mais lorsque vous naviguez sur Internet, vous ne manipulez aucune adresse IP, alors qu’elles sont indispensables.

Par exemple, pour aller sur le moteur de recherche Qwant ou sur Wikipedia, vous ne renseignez aucune adresse IP. Vous utilisez à la place une URL (Uniform Resource Locator), c’est-à-dire une adresse web qui contient un nom renvoyant à la machine qui héberge le site web.

Pourquoi ?

Parce qu’un nom est beaucoup plus facile à mémoriser qu’une adresse IP. Eh oui, avouez que ça ne serait pas pratique si vous deviez retenir l’adresse IP de la machine qui héberge le site Qwant à chaque fois que vous voulez faire une recherche !

Cependant, même si vous identifiez une machine par son nom, c’est toujours l’adresse IP qui, au final, sera utilisée par les machines pour communiquer. Même avec un serveur DNS sur le réseau, vous devrez toujours configurer les adresses IP de vos machines.

Vous pouvez d’ailleurs faire le test suivant pour vérifier que les adresses IP sont toujours utilisées. Ouvrez une invite de commandes et entrez la commande :

ping www.qwant.com

Vous obtiendrez ce type de résultat :

[![Requête ping vers Qwant et association Nom-IP](https://user.oc-static.com/upload/2021/05/26/16220358407216_image11.png)](https://user.oc-static.com/upload/2021/05/26/16220358407216_image11.png)

Requête ping vers Qwant et association Nom-IP

Comme vous pouvez le voir, la requête ping fonctionne aussi lorsque l’on remplace l’adresse IP par un nom. Si j’envoie un ping vers un nom existant, celui-ci est automatiquement traduit par une adresse IP : ici 194.187.168.100. Cette adresse IP n’est autre que l’adresse de la machine qui héberge le moteur de recherche Qwant.

À la place d’écrire qwant.com dans la barre d’adresse de votre navigateur web, vous pourriez tout à fait y inscrire son adresse IP. La page s’afficherait dans tous les cas.

OK, mais comment la traduction entre nom et adresse IP se fait-elle ?

Pour envoyer un message vers une autre machine, connaître le nom de la machine destinataire ne suffit pas. La machine source doit obligatoirement indiquer l’adresse IP de la machine de destination sur le paquet à envoyer. Pour obtenir cette adresse IP à partir d’un nom, elle va demander à une machine tierce : le **serveur DNS**.

### Associez plusieurs noms à une machine

DNS (Domain Name System) signifie “Système de Noms de Domaine”. Ce service permet de faire la correspondance entre des noms et des adresses IP. On peut le voir comme une sorte d’annuaire. Ce service repose sur un protocole également appelé DNS.

Il existe 2 types de nommage pour une machine :

- le **nom de domaine** ;
    
- le **nom d’hôte**, couramment appelé “hostname”.
    

Le **nom d’hôte** est utilisé pour identifier une machine.

Le **nom de domaine** sert plutôt à identifier un service sur une machine, c’est-à-dire une fonctionnalité, comme un site web ou le stockage de fichiers, par exemple.

Le serveur DNS permet d’associer une adresse IP à un **nom d’hôte** ou à un **nom de domaine**, ou aux deux en même temps. Une même machine peut également être associée à plusieurs **noms d’hôte** ou **noms de domaine** :

[![Un ordinateur identifié par plusieurs noms](https://user.oc-static.com/upload/2021/06/21/162427090087_P3C2-1.png)](https://user.oc-static.com/upload/2021/06/21/162427090087_P3C2-1.png)

Un ordinateur identifié par plusieurs noms

Dans l’exemple juste au-dessus, l’ordinateur dont l’adresse IP est 212.27.3.1 est identifié par 3 noms différents :

- 1 nom d’hôte : pc1 ;
    
- 2 noms de domaine : www.nomdedomaine.fr et www.nomdedomaine.com.
    

Pour que les messages à destination de ces 3 noms arrivent bien à destination de l’ordinateur ou du service, il faut configurer un serveur DNS qui va associer l’adresse IP de l’ordinateur à ces 3 noms à la manière d’un annuaire :

[![Correspondance Nom-IP](https://user.oc-static.com/upload/2021/06/21/1624272148975_P3C2-2_1.png)](https://user.oc-static.com/upload/2021/06/21/1624272148975_P3C2-2_1.png)

Correspondance Nom-IP

Chacune des entrées dans l'annuaire DNS s’appelle un “Record”, ou _enregistrement_.

Mais quel est l'intérêt de donner plusieurs noms à une même machine ?

C’est utile surtout lorsqu’une même machine héberge plusieurs services réseau, comme plusieurs sites web. En général, une machine n’aura qu’un seul nom d’hôte, mais pourra avoir plusieurs noms de domaine. Le premier nom de domaine pointera vers le site web 1, et le deuxième nom de domaine vers le site web 2.

Grâce aux DNS, l’utilisateur n’a donc pas besoin de savoir sur quelle machine est hébergé un service, il doit juste connaître le nom de domaine associé à ce service.

### Appréhendez le DNS dans une architecture simple

#### La configuration client-serveur

Tout comme le protocole DHCP, le DNS fonctionne sur le mode client-serveur : les clients émettent une requête vers un serveur qui leur répond en leur indiquant une correspondance Nom-IP. Pour ajouter cette fonctionnalité à un réseau, il faut donc configurer les clients et le serveur.

Le serveur devra être configuré pour :

- répondre aux requêtes des clients qui demandent une correspondance Nom-IP ;
    
- associer des noms avec des IP.
    

Les clients, eux, auront juste besoin de connaître l’adresse IP du serveur DNS.

#### Les échanges entre clients et serveur

Une fois la configuration effectuée, regardons comment fonctionne une petite architecture avec un serveur DNS. Dans cet exemple, voyons les étapes de communication lorsque PC0 veut envoyer un ping à PC1 sans spécifier l’adresse IP de PC1 :

[![Schéma représentant les principes de communication entre clients et serveur DNS : 1. La commande](https://user.oc-static.com/upload/2021/06/21/16242710994853_P3C2-3.png)](https://user.oc-static.com/upload/2021/06/21/16242710994853_P3C2-3.png)

Principes de communication entre clients et serveur DNS

1. La commande “ping PC1” est exécutée sur PC0.
    
2. PC0 ne connaît pas l’adresse IP du nom “PC1”, il envoie une requête au serveur DNS pour lui demander une correspondance.
    
3. Le serveur DNS regarde dans sa table DNS s’il a une entrée correspondant au nom “PC1”, et envoie une réponse contenant l’adresse IP 192.168.0.2 associée.
    
4. PC0 récupère l’adresse IP de PC1, et peut générer le paquet ping avec comme adresse de destination 192.168.0.2.
    

Dans des architectures plus abouties, le serveur DNS est souvent connecté à un autre serveur DNS, lui-même connecté à un autre serveur et ainsi de suite sur plusieurs niveaux. De cette manière, si le premier serveur DNS ne connaît pas un nom ou une URL, les autres serveurs DNS le connaîtront peut-être.

#### Vérifiez votre serveur DNS grâce à l’invite de commandes

Vous pouvez vérifier sur votre propre machine quel serveur DNS elle utilise. Allez dans l’invite de commandes Windows et entrez :

ipconfig /all

[![Serveur DNS utilisé sur un réseau domestique connecté à Internet](https://user.oc-static.com/upload/2021/05/26/16220364597424_image2.png)](https://user.oc-static.com/upload/2021/05/26/16220364597424_image2.png)

Serveur DNS utilisé sur un réseau domestique connecté à Internet

Lorsque que vous êtes chez vous, dans la majorité des cas, vous n’avez pas besoin de préciser quel serveur DNS vous souhaitez utiliser. Un serveur DNS par défaut est automatiquement attribué à votre machine en même temps qu’une adresse IP.

Mais d’où vient l’adresse IP de ce serveur DNS ?

Elle vient du **serveur DHCP**. Souvenez-vous ! le serveur DHCP permet d'affecter une adresse IP aux machines, mais aussi de leur fournir quelques informations de configuration comme :

- l’adresse IP de la passerelle par défaut à utiliser sur le réseau ;
    
- l’adresse IP d’un serveur DNS fonctionnel. 
    

Vous avez peut-être remarqué sur la capture d’écran qu’une même machine joue le rôle de serveur DNS, serveur DHCP et passerelle par défaut. Cette configuration est très courante avec les box ADSL ou fibre, qui jouent tous ces rôles à la fois.

### En résumé

- Le service DNS permet de faire la correspondance entre des noms de machine et des adresses IPs. De cette manière, les utilisateurs peuvent se passer des adresses IP quand ils naviguent sur internet.
    
- Pour ajouter la fonctionnalité DNS à un réseau, il vous faut un serveur DNS contenant la liste de tous les noms de machines du réseau et leurs adresses IP associées. Ce serveur joue le rôle d’un annuaire de correspondance entre un Nom et une adresse IP
    
- Lorsqu’une machine d’un réseau souhaite communiquer avec une autre machine dont elle ne connaît que le nom, elle demande automatiquement au serveur DNS de lui fournir l’adresse IP associée à ce nom. Elle peut ensuite envoyer son message en utilisant l’adresse IP fournie
    

_Vous connaissez maintenant les avantages d'un serveur DNS. Découvrez comment le configurer sur Packet Tracer dans le dernier chapitre de ce cours !_