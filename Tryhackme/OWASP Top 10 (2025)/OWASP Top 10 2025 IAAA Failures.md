
# 🌐 OWASP Top 10: IAAA Failures
#TryHackMe #OWASP #GRC #IAAA #AccessControl

## 1. 🎯 The Scope
Ce module connecte trois vulnérabilités majeures du classement OWASP 2025 au concept de gestion d'identité (IAAA) :
1.  **A01: Broken Access Control** (Problème d'Autorisation).
2.  **A07: Authentication Failures** (Problème d'Identification/Authentification).
3.  **A09: Logging & Alerting Failures** (Problème d'Imputabilité/Accountability).

## 2. 🔑 The Core Concept: IAAA
L'acronyme qui régit toute la sécurité des accès :
* **I**dentity (Qui es-tu ?)
* **A**uthentication (Prouve-le.)
* **A**uthorisation (As-tu le droit d'entrer ici ?)
* **A**ccountability (Je note que tu es entré.)

---

## 🌍 Vision GRC (The Big Picture)
* **Why it matters:** Ces trois catégories représentent souvent 50% des failles critiques trouvées lors d'un audit web.
* **Auditor Mindset:** Si le modèle IAAA est défaillant à n'importe quelle étape, c'est toute la chaîne de confiance qui s'effondre. Un bon mot de passe (Authentication) ne sert à rien si les logs sont désactivés (Accountability) et qu'on ne peut pas tracer le piratage.



# 🏛️ Task  IAAA Model (The Security Chain)
#TryHackMe #OWASP #IAAA #GRC #Fundamentals

## 1. ⚙️ The 4 Layers (Definitions)
La sécurité n'est pas un bloc monolithique, c'est une séquence. On ne peut pas sauter une étape.

1.  **Identity (Identification) :** *“Qui es-tu ?”*
    * C'est la revendication. L'utilisateur présente son étiquette unique (ex: `user ID`, `email`).
    * *Analogie :* Tu dis "Je suis Alice" à l'accueil.
2.  **Authentication (Authentification) :** *“Prouve-le.”*
    * C'est la vérification de la preuve (ex: `passwords`, `OTP`, `passkeys`).
    * *Analogie :* Tu montres ta carte d'identité pour prouver que tu es bien Alice.
3.  **Authorisation (Autorisation) :** *“As-tu le droit ?”*
    * C'est la permission. Qu'est-ce que cette identité vérifiée a le droit de faire ou de voir ? (ex: Admin vs User).
    * *Analogie :* Le garde vérifie si ton nom est sur la liste VIP pour entrer dans le carré or.
4.  **Accountability (Imputabilité / Traçabilité) :** *“Je note tout.”*
    * C'est l'enregistrement. Tracer qui a fait quoi, où et quand (`recording and alerting`).
    * *Analogie :* La caméra de surveillance et le registre des entrées.

## 2. 🔗 The Golden Rule
* **"It isn't possible to skip a level"**.
* Si l'Authentification échoue, on ne doit jamais tester l'Autorisation.
* Si l'Accountability manque, on ne peut pas prouver une intrusion.

---

## 🌍 Vision GRC (Audit Focus)
* **Identification vs Authentication :**
    * En réunion, ne confonds jamais ces deux termes. L'identification est publique (ton email), l'authentification est secrète (ton mot de passe).
* **Accountability & Compliance :**
    * C'est souvent le parent pauvre. Un auditeur vérifiera toujours les **Logs**. Sans logs (A09), une entreprise n'est pas conforme au RGPD (obligation de notifier une fuite de données sous 72h... encore faut-il savoir qu'elle a eu lieu !).

# 🔓 A01: Broken Access Control
#TryHackMe #OWASP #IDOR #PrivEsc #GRC

## 1. ⚙️ The Concept
Le serveur ne vérifie pas correctement si l'utilisateur *authentifié* a le droit d'accéder à la ressource demandée.
* **Le Scénario IDOR :**
    * L'application utilise un identifiant simple dans l'URL pour afficher tes données : `monsite.com/account?id=7`.
    * **L'attaque :** Tu changes manuellement le `7` en `6` dans la barre d'adresse.
    * **La Faille :** Si le site t'affiche les données du compte n°6 sans vérifier que tu es bien le propriétaire, c'est gagné.

## 2. 🪜 Types of Privilege Escalation
Il est crucial de distinguer les deux mouvements décrits dans le cours :
* **Horizontal Privilege Escalation :**
    * Tu restes au même niveau de droits (utilisateur lambda), mais tu accèdes aux données d'un *autre* utilisateur lambda.
    * *Exemple :* Alice lit les emails de Bob.
* **Vertical Privilege Escalation :**
    * Tu montes en grade. Tu passes d'utilisateur lambda à Administrateur.
    * *Exemple :* Alice accède au panneau de configuration du serveur.


### How to Fix This Vulnerability

- •Implement proper authentication and authorization checks
- •Verify that the authenticated user has permission to access the requested resource
- •Use indirect references or encrypted tokens instead of predictable IDs
- •Log and monitor access attempts to sensitive resources
---

## 🌍 Vision GRC (The #1 Risk)
* **Pourquoi c'est N°1 ?** Contrairement à des failles techniques (comme l'injection SQL) qui peuvent être détectées par des scanners automatiques, les problèmes d'Access Control sont souvent logiques. Un robot a du mal à savoir si "Alice a le droit de voir le dossier 12". Seul un humain (ou un test unitaire bien écrit) peut le valider.
* **Audit Question:** "Comment garantissez-vous qu'un utilisateur ne peut pas itérer sur les ID clients pour aspirer la base de données ?" (La réponse attendue est souvent l'utilisation d'UUIDs aléatoires impossibles à deviner, au lieu de 1, 2, 3).


# 🆔 A07: Authentication Failures
#TryHackMe #OWASP #LogicFlaw #GRC #AccountTakeover

## 1. ⚙️ The Concept
Cette catégorie regroupe tout ce qui permet à un attaquant de se faire passer pour quelqu'un d'autre.
* **Classiques :** Mots de passe faibles ("123456"), absence de blocage après 5 essais (Brute-force).
* **Le Cas ici (Logic Flaw) :**
    * Certaines bases de données ne font pas la différence entre majuscules et minuscules (Case Insensitive) ou ignorent les espaces.
    * **L'attaque :** L'utilisateur `admin` existe déjà. Tu ne peux pas le recréer.
    * **Le Bypass :** Si tu t'inscris sous le nom ` aDmIN ` (ou avec un espace devant), l'application "pense" que c'est un nouvel utilisateur et t'inscrit. Mais au moment du login, la base de données confond ton nouveau compte avec le vrai compte `admin` et te connecte avec ses droits !

## 2. 🛡️ Remediation
* **Multi-Factor Authentication (MFA) :** C'est la réponse universelle de l'auditeur. Même si le mot de passe est volé ou contourné, l'attaquant n'a pas le code SMS/App.
* **Input Validation :** Normaliser les entrées (tout mettre en minuscule, supprimer les espaces) *avant* de vérifier si l'utilisateur existe.

---

## 🌍 Vision GRC (Audit Focus)
* **Policy Review :**
    * L'auditeur vérifiera la "Politique de Mots de Passe" (Complexité, Rotation).
    * Mais surtout : "Avez-vous du MFA sur les comptes à privilèges (Admin) ?" Si la réponse est non, c'est une **Non-Conformité Majeure** dans la plupart des standards modernes.

## 🧠 Rappel Mémoire
"L'authentification, c'est la porte d'entrée. Si la serrure est cassée (Logic Flaw) ou si la clé est sous le paillasson (Weak Password), tout le monde rentre."

# 📜 A09: Logging & Alerting Failures
#TryHackMe #OWASP #Logs #Accountability #Forensics

## 1. ⚙️ The Concept
Cette vulnérabilité survient quand une application ne note pas (ou mal) les événements de sécurité critiques.
* **Ce qui doit être loggé :** Échecs d'authentification, accès aux données sensibles, changements de privilèges, erreurs systèmes.
* **Le Risque :** Si un attaquant fait du brute-force pendant 3 jours et que personne n'est alerté, ou s'il vole la base de données sans laisser de trace dans les logs, l'attaque est "invisible". On ne peut ni la détecter en temps réel, ni enquêter après coup.

## 2. 🕵️ Forensic Analysis (La méthode)
Pour enquêter sur des logs, on cherche des **motifs (Patterns)** :
* **Brute-Force :** Une avalanche de "Login Failed" (Erreur 401/403) venant de la même IP en peu de temps.
* **Account Takeover :** Après 50 échecs, soudain un "Login Success" (Code 200) pour cette même IP malveillante. C'est le moment précis où le mot de passe a craqué.
* **Post-Exploitation :** Que fait cette IP juste après s'être connectée ? (ex: accès à `/admin`, `/delete-user`).

---

## 🌍 Vision GRC (Compliance & GDPR)
* **RGPD (GDPR) Art. 33 :** En cas de violation de données, l'entreprise doit notifier la CNIL sous 72h.
    * *Problème :* Si tes logs sont vides (A09), tu ne sauras même pas que tu as été piraté. Tu seras donc en défaut de notification = Amende potentielle de 2% à 4% du CA mondial.
* **Audit Trail :** Un auditeur vérifie la "rétention des logs". Sont-ils gardés 6 mois ? 1 an ? Sont-ils stockés sur un serveur sécurisé (pour que le hacker ne puisse pas les effacer en sortant) ?

# 🛡️ IAAA Security Checklist (Summary)
#TryHackMe #OWASP #Remediation #GRC

## 1. 📋 Summary of Controls
Pour sécuriser le modèle IAAA, voici les contrôles techniques indispensables :

* **A01 (Access Control) :**
    * *Règle :* "Enforce server-side checks on **every** request."
    * *Traduction :* Ne jamais faire confiance au navigateur du client. Chaque fois qu'une donnée est demandée, le serveur doit revérifier : "Est-ce que cet utilisateur a le droit de voir ça ?"
* **A07 (Authentication) :**
    * *Règle :* "Rate-limit/lock out brute force."
    * *Traduction :* Bloquer le compte après 5 tentatives échouées. Utiliser des indexes uniques pour éviter les doublons de noms (le coup du ` aDmIN `).
* **A09 (Logging) :**
    * *Règle :* "Centralize logs off-host with retention."
    * *Traduction :* Envoyer les logs sur un serveur dédié (SIEM) pour qu'un attaquant ne puisse pas les effacer localement après son intrusion.

## 2. 🌍 Vision GRC (Audit Conclusion)
* **La phrase magique :** "L'implémentation IAAA doit être sécurisée de bout en bout."
* Si tu audites une application, tu vérifieras ces 3 points précis. Si l'un manque, c'est une non-conformité majeure.

## 🧠 Rappel Mémoire
"Vérifie **chaque** requête (A01), **Bloque** les brutes (A07), **Sauvegarde** les preuves ailleurs (A09)."