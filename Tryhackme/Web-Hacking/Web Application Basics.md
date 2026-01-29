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

# 🏗️ Web Architecture: Anatomy
#TryHackMe #WebFundamentals #FrontEnd #BackEnd #GRC

## 1. 🎨 The Front-End (Client-Side)
C'est ce qui s'exécute dans **ton** navigateur (Chrome, Firefox). C'est la partie visible de l'iceberg.
L'image utilise l'analogie du corps humain :
* **HTML (Structure) :** Le squelette 🦴. Il définit l'organisation de la page (titres, paragraphes, images). Sans lui, la page n'existe pas.
* **CSS (Style) :** La peau et les vêtements 👕. Il rend la page jolie (couleurs, polices, mise en page).
* **JavaScript (Interactivity) :** Les muscles 🦾. Il rend la page dynamique (boutons qui bougent, pop-ups, calculs immédiats).

## 2. ⚙️ The Back-End (Server-Side)
C'est ce qui s'exécute sur l'ordinateur de l'entreprise (le Serveur). C'est le cerveau et la mémoire.
* **Web Server :** L'infrastructure qui reçoit ta demande et te renvoie la page.
* **Database :** La mémoire 🧠. C'est là que sont stockés les mots de passe, les produits, les numéros de carte bleue.
* **WAF (Web Application Firewall) :** Le bouclier 🛡️. Un logiciel spécial placé devant le serveur pour bloquer les attaques courantes (comme les injections SQL) avant qu'elles ne touchent le code.

---

## 🌍 Vision GRC (The Trust Boundary)
* **Client-Side Validation is NOT Security:**
    * *Concept Clé :* Un développeur peut mettre une vérification en JavaScript : "Le champ Prix ne peut pas être négatif".
    * *L'Attaque :* Comme le JavaScript tourne chez toi, tu peux le modifier. Un hacker désactivera le JS pour envoyer "Prix = -10€".
    * *Règle d'Audit :* "Ne jamais faire confiance aux données venant du client." Toutes les vérifications doivent être refaites côté Serveur (Back-End).
* **WAF Compliance:**
    * Pour la norme **PCI-DSS** (paiement par carte), l'installation d'un **WAF** est souvent obligatoire pour protéger les données bancaires.