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