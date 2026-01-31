# 🏗️ OWASP: Application Design Flaws
#TryHackMe #OWASP #Architecture #Configuration #GRC

## 1. 🎯 The Scope
Ce module couvre 4 vulnérabilités structurelles critiques liées à la conception et à la configuration du système :

1.  **A02: Security Misconfigurations :** L'erreur humaine pure. Laisser les réglages par défaut, oublier de fermer un port, laisser des fichiers de debug accessibles.
2.  **A03: Software Supply Chain Failures :** La confiance aveugle. Utiliser des composants tiers (librairies, plugins) qui sont eux-mêmes vulnérables ou malveillants.
3.  **A04: Cryptographic Failures :** La fausse sécurité. Utiliser des algos obsolètes (MD5), stocker les mots de passe en clair, ou mal gérer les clés de chiffrement.
4.  **A06: Insecure Design :** L'erreur de logique. Le code est "propre", mais le fonctionnement prévu est dangereux (ex: "mot de passe oublié" qui pose des questions trop faciles).

## 2. 🛠️ Lab Setup
* **Action Requise :** Ce module contient des exercices pratiques.
* **Important :** Clique sur le bouton vert **Start Machine** en haut à droite de la tâche pour lancer la machine cible (Target Machine).
* Si tu utilises l'AttackBox, assure-toi qu'elle est démarrée aussi.

---

## 🌍 Vision GRC (Audit Focus)
* **Design Review :**
    * Contrairement au Pentest (qui arrive à la fin), ces failles se détectent idéalement lors de la phase de conception ("Security by Design").
    * Un auditeur posera la question : "Avez-vous fait une analyse de risques sur l'architecture avant de coder ?"


# ⚙️ A02: Security Misconfigurations
#TryHackMe #OWASP #Hardening #CloudSecurity #GRC

## 1. 🔍 The Anatomy of the Flaw
Contrairement aux bugs logiciels, cette faille survient quand le système est techniquement fonctionnel mais déployé de manière non sécurisée.
* **Définition :** Utilisation de valeurs par défaut, fonctionnalités inutiles activées, ou services exposés par erreur.
* **L'Impact (Why it matters) :** C'est souvent le point d'entrée le plus facile. Une seule API mal configurée ou un "bucket" de stockage ouvert peut compromettre tout le système (ex: fuite de données Uber 2017 via AWS S3).

## 2. 🚩 Common Attack Vectors (Patterns)
Voici les configurations dangereuses classiques que tu chasseras en audit :
* **Default Credentials :** Laisser `admin:admin` ou des mots de passe faibles.
* **Unnecessary Services :** Avoir des ports ouverts ou des endpoints exposés qui ne servent à rien.
* **Cloud Misconfigs :** Permissions S3/Azure Blob trop larges (Public Read/Write).
* **Verbose Error Messages (Stack Traces) :** *Point critique pour le challenge.*
    * Quand une application plante, elle ne doit dire que "Erreur interne".
    * Si elle affiche tout le code d'erreur (Stack Trace), elle révèle les versions logicielles, les chemins de fichiers, et parfois des clés API ou des données en mémoire.
* **Outdated Software :** Utiliser des frameworks ou conteneurs avec des CVE connues.
* **Unrestricted API Access :** Oublier l'authentification sur certaines routes d'API.

## 3. 🛡️ Remediation Strategy (Hardening)
La réponse universelle est le **Durcissement (Hardening)** :
1.  **Remove & Disable :** Supprimer tout service ou fonctionnalité inutile.
2.  **Patch Management :** Garder la stack logicielle à jour.
3.  **Hide Information :** Désactiver les messages d'erreur détaillés (Debug mode off).
4.  **Automated Audits :** Intégrer des scanners de config dans le pipeline CI/CD.

---

## 🌍 Vision GRC (Compliance Focus)
* **Audit de Configuration :**
    * Un auditeur ne regarde pas le code, il regarde le fichier `config`.
    * *Question :* "Avez-vous changé les mots de passe par défaut ?" "Le mode DEBUG est-il désactivé en production ?"
* **Cloud Security Posture Management (CSPM) :**
    * Outils automatisés obligatoires pour vérifier en continu que les buckets S3 ne sont pas publics.


# ⛓️ A03: Software Supply Chain Failures
#TryHackMe #OWASP #Dependencies #SolarWinds #SBOM

## 1. ⚙️ The Mechanism
Cette faille survient quand une application dépend de composants tiers (librairies, API, modèles IA) qui sont eux-mêmes compromis ou obsolètes.
* **Concept :** Tu cuisines un gâteau sain, mais la farine que tu as achetée contient du poison.
* **L'exemple SolarWinds (2021) :** Les attaquants ont inséré une backdoor dans une *mise à jour officielle* du logiciel Orion. Des milliers d'entreprises ont installé le virus en pensant faire une mise à jour de sécurité.
* **Le Cas AI :** Utiliser des modèles d'IA ou des datasets non vérifiés qui contiennent des biais cachés ou des backdoors ("Model Poisoning").

## 2. 🚩 Attack Vectors & Patterns
* **Unmaintained Libraries :** Utiliser un module qui n'est plus mis à jour depuis 3 ans.
* **Auto-Updates :** Laisser les dépendances se mettre à jour sans vérification de signature (si le dépôt NPM/PyPi est piraté, tu télécharges le virus).
* **Insecure CI/CD :** Si le pipeline de déploiement est modifiable, un attaquant peut injecter du code juste avant la compilation.
* **Lack of Monitoring :** Ne pas savoir quelles librairies on utilise (Pas de SBOM - Software Bill of Materials).

## 3. 🛡️ Remediation (Secure Supply Chain)
* **SBOM (Software Bill of Materials) :** Tenir un inventaire précis de tous les composants.
* **Lock Versions :** Ne jamais utiliser "latest". Fixer les versions précises (ex: `v1.2.4` et pas `v1.2.*`).
* **Sign & Verify :** Vérifier les signatures numériques des paquets.
* **Scan Dependencies :** Utiliser des outils (comme OWASP Dependency-Check ou Snyk) dans le CI/CD.


# 🔐 A04: Cryptographic Failures
#TryHackMe #OWASP #Encryption #HardcodedKeys #GRC

## 1. 📉 The Core Failures
Le problème n'est presque jamais les mathématiques (AES est solide), mais l'implémentation.
* **Weak Algorithms :** Utiliser des algos cassés ou obsolètes.
    * *MD5 / SHA-1 :* Vulnérables aux collisions (deux fichiers différents ont la même signature).
    * *DES / 3DES :* Clés trop courtes, cassables par brute-force moderne.
    * *ECB Mode :* Mode de chiffrement qui ne masque pas les motifs (on peut deviner l'image originale dans le bruit chiffré).
* **Hard-coded Secrets :** Le péché capital. Stocker les clés API, les mots de passe ou les clés de chiffrement directement dans le code source (git) ou les fichiers de config.
* **Lack of HTTPS :** Transmettre des données sensibles (login, crédit) en clair sur le réseau.

## 2. 🛡️ Remediation (Best Practices)
* **Algorithms :** Utiliser des standards modernes.
    * *Symétrique :* AES-256-GCM (GCM est important car il garantit aussi l'intégrité).
    * *Hashing (Mots de passe) :* Argon2, PBKDF2, scrypt (algos lents pour bloquer le brute-force).
* **Key Management :**
    * Ne jamais stocker de clés dans le code. Utiliser des coffres-forts (Vaults) ou des variables d'environnement injectées au runtime.
* **Certificate Management :** Valider les chaînes de certificats, éviter les certificats auto-signés en prod.

---

## 🌍 Vision GRC (Audit & Compliance)
* **PCI-DSS & GDPR :**
    * Le chiffrement des données "au repos" (sur le disque) et "en transit" (réseau) est une exigence légale stricte.
    * *Audit :* Scanner le code source à la recherche de strings à haute entropie (qui ressemblent à des clés) est une étape standard (outils comme `trufflehog` ou `git-secrets`).


# 🏗️ A06: Insecure Design
#TryHackMe #OWASP #BusinessLogic #ThreatModeling #GRC

## 1. 🧠 The Core Concept
Cette catégorie regroupe les failles où l'application fonctionne "comme prévu", mais où le plan initial était mauvais.
* **Différence clé :** Une "Implementation Flaw" est une erreur de codage. Une "Design Flaw" est une absence de contrôle de sécurité dans les spécifications.
* **La Cause :** Manque de **Threat Modeling** (modélisation des menaces) avant de coder. On a supposé que l'utilisateur serait gentil ou que l'application serait cachée.

## 2. 🚩 Common Patterns & AI Risks
* **Client-Side Trust :** Supposer que si le bouton "Admin" est caché en HTML, l'utilisateur ne peut pas trouver l'URL `/admin`. (Sécurité par l'obscurité).
* **Broken Business Logic :** Exemple : Un site e-commerce permet d'acheter un article à prix négatif et de se faire rembourser. Le code marche (il fait l'addition), mais la logique métier est fausse.
* **AI & Insecure Design :**
    * *Prompt Injection :* L'application injecte l'input utilisateur directement dans un modèle IA sans "guardrails".
    * *Blind Trust :* L'application exécute aveuglément du code ou des commandes SQL générés par une IA.

## 3. 🛡️ Remediation (Shift Left)
* **Threat Modeling :** Analyser les risques *avant* d'écrire une ligne de code.
* **Zero Trust :** Ne jamais faire confiance au client (navigateur, app mobile). Tout ce qui arrive au serveur doit être vérifié à nouveau.
* **Secure Design Patterns :** Utiliser des bibliothèques d'authentification éprouvées plutôt que de créer sa propre logique "maison".

---

## 🌍 Vision GRC (Audit Strategy)
* **Review des Spécs :** L'auditeur ne regarde pas le code ici, mais les diagrammes d'architecture.
* **Question clé :** "Avez-vous documenté les abus possibles de cette fonctionnalité ?" (Abuse Cases vs Use Cases).

# 🏛️ Module Summary: Application Design Flaws
#TryHackMe #OWASP #Review #SecurityByDesign

## 1. 🔑 The Root Cause
Toutes les failles vues ici (A02, A03, A04, A06) partagent une cause commune : **Weak Foundations** (Fondations fragiles).
On ne peut pas "patcher" une mauvaise architecture à la fin du projet. La sécurité doit être intégrée dès le dessin des plans.

## 2. 🛡️ Key Takeaways (The 4 Pillars)
1.  **A02 - Security Misconfigurations :**
    * *Leçon :* Ne jamais laisser les paramètres par défaut. Désactiver le mode Debug en prod.
    * *Audit :* Scanner les ports et les messages d'erreur.
2.  **A03 - Supply Chain Failures :**
    * *Leçon :* "Trust but Verify". Vos dépendances (librairies) sont votre talon d'Achille.
    * *Audit :* Utiliser un SBOM (Software Bill of Materials) et scanner les vulnérabilités connues (CVE).
3.  **A04 - Cryptographic Failures :**
    * *Leçon :* Ne jamais inventer sa crypto. Ne jamais stocker de clés dans le code (Hardcoding).
    * *Audit :* Chercher les clés API dans le code source et vérifier l'usage de HTTPS/TLS.
4.  **A06 - Insecure Design :**
    * *Leçon :* Ne jamais faire confiance au client (User-Agent, HTML caché).
    * *Audit :* Threat Modeling. Se demander "Comment puis-je abuser de cette logique ?".

## 3. 🚀 Philosophy: Shift Left
L'industrie bouge vers le **"Shift Left"** : tester la sécurité tôt (à gauche du cycle de développement), plutôt qu'à la fin (Pentest). C'est moins cher et plus efficace.