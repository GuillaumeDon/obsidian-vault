Learn the basics of web applications: HTTP, URLs, request methods, response codes, and headers.

# 🌐 Web Application Basics (Introduction)
#TryHackMe #WebHacking #HTTP #Fundamentals #GRC

## 1. 🎯 The Learning Objectives
Ce module couvre les éléments vitaux qui permettent au web de fonctionner. Voici ce que nous allons déconstruire :
* **Web Application Architecture :** Comprendre comment une app tourne dans un navigateur.
* **URL Anatomy :** Casser une URL en morceaux (Protocole, Domaine, Chemin, Paramètres).
* **HTTP Cycle :** Comprendre le dialogue "Requête" (Client) vs "Réponse" (Serveur).
* **HTTP Methods :** Les verbes d'action (GET pour demander, POST pour envoyer).
* **Response Codes :** Le langage des serveurs (200 OK, 404 Not Found, 500 Error).
* **Headers :** Les métadonnées de sécurité.

## 2. 🛡️ Why it matters for GRC?
* **Audit de Conformité :**
    * Un auditeur vérifie souvent les "En-têtes de sécurité" (Security Headers). Savoir ce qu'ils sont et pourquoi ils sont importants est une compétence clé.
* **Incident Response :**
    * Lire des logs web (comme vu dans le module précédent) demande de comprendre les codes HTTP. Savoir qu'un code **200** sur une page `/admin` est suspect par rapport à un code **403** (Interdit).

## 🧠 Rappel Mémoire
"Le Web n'est qu'un échange de lettres (Requêtes/Réponses) écrites dans une langue précise (HTTP)."

# 🪐 Web Architecture: The Planet Analogy
#TryHackMe #WebFundamentals #Structure #Style #Interactive

## 1. 🎨 The Front-End (Visible Planet)
Le cours compare l'application web à une **planète** pour expliquer ses couches visibles :

* **HTML (Structure) :** C'est la forme de la planète.
    * Il définit la structure brute. Sans lui, rien n'existe.
* **CSS (Looking / Style) :** C'est la végétation, les océans, l'atmosphère.
    * Il rend la planète (le site) agréable à regarder. Sans lui, c'est juste un rocher brut.
* **JavaScript (Interactivity) :** C'est la vie, le mouvement, la rotation.
    * Il permet l'interaction. Sans lui, la planète est statique (figée).

## 2. ⚙️ The Back-End (Infrastructure)
C'est ce qui soutient la planète dans l'espace :

* **Web Server :** L'infrastructure qui fait tourner l'application.
* **Database :** Le stockage des ressources (minerais, données).
* **WAF (Web Application Firewall) :** Le bouclier atmosphérique 🛡️.
    * Il protège l'application contre le trafic malveillant. C'est un composant indispensable pour la sécurité.

---
## 🌍 Vision GRC
* **WAF & Conformité :**
    * Le **WAF** est explicitement cité comme "indispensable to ensuring the security". Dans un audit, l'absence de WAF sur une application critique est souvent une "Non-Conformité".


# 🔗 URL Anatomy (Decoding Addresses)
#TryHackMe #URL #Typosquatting #GRC

## 1. 🧬 The Components
Une URL est une adresse précise. Voici ses organes vitaux :

* **Scheme (Protocole) :** Le langage utilisé.
    * `HTTP` (Non sécurisé, Port 80).
    * `HTTPS` (Sécurisé/Chiffré, Port 443).
* **User :** (Rare aujourd'hui) Login intégré dans l'URL (`user:password@site.com`). Risqué car les identifiants sont en clair.
* **Host/Domain :** Le nom du serveur (ex: `tryhackme.com`).
* **Port :** La porte d'entrée (souvent invisible car implicite).
* **Path :** Le chemin vers le fichier (ex: `/view-room`).
* **Query String :** Les paramètres après le `?`.
    * *Utilité :* Passer des infos comme des termes de recherche.
    * *Risque :* Zone critique pour les injections SQL.
* **Fragment :** L'ancre après le `#`. Sert à scroller à un endroit précis de la page. C'est purement "Client-Side".

## 2. 🌍 Vision GRC (Threat Focus)
* **Typosquatting :**
    * Le cours mentionne explicitement cette attaque dans la section *Host/Domain*.
    * *Concept :* Acheter `goggle.com` au lieu de `google.com` pour piéger les utilisateurs qui font une faute de frappe.
    * *Audit :* Les entreprises doivent surveiller et acheter les domaines proches du leur pour éviter ce phishing.


# 📨 HTTP Messages (Request vs Response)
#TryHackMe #HTTP #Packets #Structure #GRC

## 1. 🗣️ The Dialogue Types
Le web n'est qu'une discussion constante entre deux acteurs :

* **HTTP Requests (La Question) :**
    * Envoyées par **l'Utilisateur** (Client) pour déclencher une action.
    * *Exemple :* "Je veux voir la page d'accueil."
* **HTTP Responses (La Réponse) :**
    * Envoyées par le **Serveur** après avoir traité la demande.
    * *Exemple :* "Ok, voici le code HTML de la page."

## 2. 🦴 Anatomy of a Message
Chaque message (qu'il soit Requête ou Réponse) suit strictement la même structure en 4 parties :

1.  **Start Line :** La première ligne. Elle dit "Bonjour, je veux ça" (Requête) ou "Bonjour, voici le résultat" (Réponse).
2.  **Headers :** Les métadonnées. Des paires "Clé: Valeur" qui donnent des infos techniques (langue, type de navigateur, cookies).
3.  **Empty Line :** ⚠️ **Crucial.** C'est une ligne vide qui sert de séparateur. Elle dit "Fin des en-têtes, le contenu commence maintenant".
4.  **Body :** Le corps du message. C'est la donnée réelle (le code HTML de la page pour une réponse, ou tes identifiants de login pour une requête).

---

## 🌍 Vision GRC (Deep Inspection)
* **Data Leakage :**
    * Un auditeur vérifie souvent le **Body** des réponses HTTP. Parfois, un serveur mal configuré renvoie des données sensibles (erreurs SQL, versions de logiciel) dans le corps du message, même si la page affichée à l'écran semble normale.
* **WAF Bypass :**
    * Certaines attaques jouent sur l'**Empty Line** ou des Headers mal formés pour tromper les pare-feux. Comprendre cette structure est vital pour l'analyse forensique.


# 🗣️ HTTP Requests: Methods & Versions (Detailed)
#TryHackMe #HTTP #Verbs #RFC #GRC

## 1. 📝 The Request Line
C'est la première ligne d'une requête HTTP. Elle définit l'intention du client.
Elle se décompose strictement en 3 parties :
1.  **HTTP Method :** Le verbe d'action (ex: `GET`).
2.  **Path :** L'emplacement de la ressource sur le serveur (ex: `/user/login.html`). Si aucune ressource n'est précisée, c'est souvent la racine `/`.
3.  **HTTP Version :** La version du protocole utilisée (ex: `HTTP/1.1`).

## 2. ⚡ The 9 HTTP Methods (Verbs)
Voici la liste exhaustive des méthodes standard et leur usage précis :

### 🔹 Les Fondamentaux
* **GET :** "Récupérer".
    * Utilisé pour demander une ressource.
    * *Sécurité :* Ne doit jamais modifier les données sur le serveur (lecture seule).
* **POST :** "Envoyer".
    * Utilisé pour soumettre des données (formulaires, logins, uploads) pour traitement par le serveur.
    * *Note :* Crée souvent une nouvelle ressource ou déclenche une action.

### 🔹 La Gestion de Ressources
* **PUT :** "Remplacer / Créer".
    * Met à jour une ressource existante en remplaçant son contenu complet. Si elle n'existe pas, il la crée.
* **PATCH :** "Modifier partiellement".
    * Applique des modifications partielles à une ressource (ex: changer juste l'email d'un utilisateur, pas tout son profil).
* **DELETE :** "Supprimer".
    * Retire la ressource spécifiée du serveur.

### 🔹 Les Utilitaires & Techniques
* **HEAD :** "En-têtes seulement".
    * Identique à GET, mais le serveur renvoie uniquement les en-têtes (Headers), pas le corps (Body).
    * *Usage :* Vérifier si une page existe ou sa date de modif sans télécharger le gros fichier.
* **OPTIONS :** "Disponibilité".
    * Demande au serveur quelles méthodes (GET, POST, etc.) sont autorisées pour une URL donnée.
    * *Usage :* Reconnaissance technique (CORS).
* **TRACE :** "Écho".
    * Le serveur renvoie au client la requête exacte qu'il a reçue.
    * *Usage :* Debugging (voir si des proxys modifient la requête en route).
* **CONNECT :** "Tunnel".
    * Transforme la connexion en tunnel transparent (souvent pour le SSL/HTTPS via un proxy).

## 3. 🚀 HTTP Versions Evolution
L'évolution dicte la performance et la sécurité :
* **HTTP/1.0 :** Ancienne version. Chaque fichier (image, css) demande une nouvelle connexion TCP (lent).
* **HTTP/1.1 :** Le standard actuel.
    * Introduit les connexions persistantes ("Keep-Alive") : on garde le tuyau ouvert pour charger plusieurs fichiers.
* **HTTP/2 :** La version moderne (2015).
    * **Multiplexing :** Le gros changement. On envoie plusieurs requêtes *en même temps* sur une seule connexion TCP.
    * **Binary :** Plus efficace à parser pour les machines que le texte.

---

## 🌍 Vision GRC (Audit & Risques)
* **Unnecessary Methods :**
    * Un serveur web bien configuré ne doit exposer que le strict nécessaire (souvent GET, POST, HEAD).
    * *Risque Critique :* Laisser `PUT` ou `DELETE` ouverts publiquement permet à n'importe qui de défigurer le site.
    * *Risque TRACE :* Peut être utilisé pour voler des cookies HttpOnly (attaque Cross-Site Tracing - XST).
* **Conformité :**
    * L'utilisation de **HTTP/2** ou **HTTP/3** est recommandée pour la performance (SEO) mais aussi pour certaines améliorations de sécurité (chiffrement souvent forcé).