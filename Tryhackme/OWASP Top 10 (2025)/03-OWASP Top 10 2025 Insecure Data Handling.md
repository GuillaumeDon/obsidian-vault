
# 🗑️ OWASP: Insecure Data Handling
#TryHackMe #OWASP #Injection #Integrity #GRC

## 🎯 The Scope
Ce module couvre 3 vulnérabilités critiques liées au traitement des données utilisateurs :

1.  **A04: Cryptographic Failures :** (Le Retour).
    * *Nuance :* Si le module précédent traitait du "Design" (clés hardcodées), ici on va se concentrer sur la **manipulation** (comment les données sensibles transitent et sont stockées).
2.  **A05: Injection :** (La Star).
    * L'application accepte des données sans les nettoyer, permettant à l'attaquant d'envoyer des commandes au système (SQL, OS Command).
3.  **A08: Software or Data Integrity Failures :**
    * L'application fait confiance à des mises à jour ou des objets sérialisés sans vérifier leur intégrité (signature), permettant l'exécution de code malveillant.



# 🔐 A04: Cryptographic Failures (Implementation)
#TryHackMe #OWASP #WeakAlgo #Hashing #GRC

## 1. 📉 The Implementation Flaws
Ici, l'erreur n'est pas l'oubli du chiffrement, mais l'utilisation d'une protection **faible** ou **mal implémentée**.

* **Weak Algorithms (Legacy):** Utiliser des algos que les ordinateurs modernes cassent en quelques secondes.
    * *Exemples à bannir :* MD5, SHA-1 (hachage avec collisions), DES (clé trop courte), RC4.
* **"Rolling Your Own Crypto" :** Le piège de l'ego.
    * Un développeur tente d'inventer son propre algorithme de chiffrement. C'est toujours une catastrophe mathématique. En crypto, on utilise **uniquement** des standards éprouvés (NIST).
* **Insufficient Entropy :** Utiliser une clé générée aléatoirement, mais avec un générateur prédictible (ex: `Random(Time)`).

## 2. 🛡️ Prevention (Standardize)
* **Data at Rest (Stockage) :**
    * *Mots de passe :* Ne jamais chiffrer (car c'est réversible), il faut **Hacher** avec du "Salt".
    * *Algos recommandés :* **Argon2**, **bcrypt**, **scrypt**. Ils sont volontairement lents pour empêcher le brute-force.
* **Data in Transit (Réseau) :**
    * Forcer **TLS 1.2** ou **1.3**. Bannir SSL et TLS 1.0/1.1.
* **Libraries :** Utiliser des librairies reconnues (ex: Libsodium, Bouncy Castle) plutôt que d'écrire les fonctions mathématiques soi-même.

---

## 🌍 Vision GRC (Audit)
* **Inventaire Crypto :** L'auditeur demandera la liste de tous les algos utilisés. La présence de "MD5" dans un rapport est souvent une non-conformité majeure (High/Critical).


# 💉 A05: Injection
#TryHackMe #OWASP #SSTI #RCE #InputValidation

## 1. 💉 The Concept
L'injection survient quand des données fournies par l'utilisateur (toi) sont envoyées à un interpréteur (Base de données, Shell, Moteur de Template) sans être nettoyées.
* **Le Résultat :** L'interpréteur confond tes données avec des instructions. Au lieu d'afficher "Toto", il exécute la commande `Supprimer tout`.

## 2. 🚩 Types d'Injection
* **SQL Injection (SQLi) :** Manipuler la base de données (vol de mots de passe).
* **Command Injection (OS) :** Exécuter des commandes système (comme `ls`, `cat`) sur le serveur.
* **SSTI (Server-Side Template Injection) :** *Le sujet du jour.*
    * Les moteurs de template (Jinja2, Twig) servent à générer des pages HTML dynamiques (ex: "Bonjour {{user}}").
    * Si tu injectes du code dans `{{...}}`, le serveur peut l'éxecuter.

## 3. 🛡️ Prevention
* **Parameterized Queries :** Ne jamais concaténer des chaînes de caractères pour construire une requête.
* **Input Validation :** Utiliser des "allow-lists" (n'accepter que les caractères alphanumériques).
* **Escaping :** Neutraliser les caractères spéciaux (`<`, `>`, `'`, `"`) avant de les traiter.

# 📦 A08: Software or Data Integrity Failures
#TryHackMe #OWASP #Deserialization #Pickle #Integrity

## 1. 🧩 The Concept: Deserialization
* **Serialization :** Convertir un objet complexe (en mémoire) en une suite de caractères (pour le stocker ou l'envoyer). Exemple : Transformer un objet "User" en JSON ou en binaire.
* **Deserialization :** L'inverse. Reconstruire l'objet à partir des données.
* **La Faille :** Si l'application désérialise des données provenant d'une source non fiable (toi) sans vérification, elle peut être forcée d'exécuter du code malveillant inclus dans l'objet.

## 2. 🐍 The Python Case: Pickle
En Python, le module standard pour sérialiser est **`pickle`**.
* **Danger :** `pickle` permet de définir ce qui se passe quand l'objet est reconstruit (via la méthode `__reduce__`).
* **L'Exploit :** Un attaquant peut créer un objet "Piégé" qui, au moment d'être lu par le serveur (`pickle.loads`), exécute une commande système (comme `os.system` ou `os.popen`).

## 3. 🛡️ Remediation
* **Don't use Pickle :** Ne jamais utiliser `pickle` pour échanger des données avec l'extérieur. Utiliser `JSON` (qui est sûr car ce n'est que du texte).
* **Signatures :** Si la sérialisation est obligatoire, signer numériquement les données (HMAC) pour garantir qu'elles n'ont pas été modifiées.