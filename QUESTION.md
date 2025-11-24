# **QUESTION**

## **1. Sécurité et RGPD**

### **Q1.1 : Pourquoi est-il important de stocker les clés API dans un fichier `.env` et pas directement dans le code ?**

- **Pour éviter d'exposer publiquement des clés sensibles** si le code est partagé (GitHub, envoi du projet, etc.).
- **Pour séparer le code de la configuration**, ce qui facilite la maintenance et le changement de clés.
- **Pour limiter les risques de piratage** : une clé exposée peut permettre d’utiliser votre compte API, générer des coûts ou accéder à des données.
- Le fichier **`.env`** n’est généralement pas versionné, ce qui protège l'information.

### **Q1.2 : Quelles données personnelles sont collectées par notre agent ? Est-ce conforme au principe de minimisation du RGPD ?**

Selon le TP typique (extraction de ville, questions météo…), l’agent peut collecter :

- **Le texte fourni par l’utilisateur**, qui peut contenir une donnée personnelle si l’utilisateur la mentionne.
- **La ville demandée**, qui n’est pas forcément une donnée personnelle sauf si elle identifie une personne.

→ **Oui**, cela respecte le principe de minimisation, car :

- **seules les données strictement nécessaires** au fonctionnement (ex. : ville → météo) sont demandées,
- **aucune donnée sensible ou excessive** n’est requise.

### **Q1.3 : Que se passerait-il si on stockait l'historique des conversations ? Quelles obligations RGPD s’appliqueraient ?**

Stocker les conversations implique :

- **Collecte potentielle de données personnelles voire sensibles.**
- Le service devient **responsable de traitement**, ce qui implique plusieurs obligations :
	- **Informer les utilisateurs** (article 13 RGPD),
	- **Avoir une base légale** (ex. : consentement ou intérêt légitime),
	- **Appliquer un principe de minimisation** (ne garder que ce qui est utile),
	- **Définir une durée de conservation limitée**,
	- **Mettre en place des mesures de sécurité**,
	- **Fournir un droit d’accès / rectification / suppression**.

## **2. Conception conforme CNIL**

### **Q2.1 : Citez 3 recommandations de la CNIL que nous avons appliquées dans ce TP.**

Quelques exemples :

- **Informer l’utilisateur qu’il parle à une IA.**
- **Limiter les données collectées** (principe de minimisation).
- **Ne pas conserver les conversations.**
- **Sécuriser les clés et les accès** (via `.env`).

### **Q2.2 : Comment l'utilisateur est-il informé qu'il parle à un robot ? Pourquoi est-ce important ?**

L’interface ou le premier message indique clairement qu’il s’agit d’un agent conversationnel.

Cela évite :

- **la confusion avec un humain**,
- **le risque de manipulation**,
- **une violation des recommandations CNIL** et du droit à l'information (RGPD art. 12).

### **Q2.3 : Proposez une amélioration pour ajouter une “supervision humaine”.**

Exemples possibles :

- **Un bouton “contacter un humain”.**
- **Une remontée vers un opérateur** en cas de message ambigu ou critique (santé, sécurité…).
- **Possibilité pour un humain de relire et valider les réponses** dans certains cas.
- **Mise en place d’un système d’escalade** : si l’IA ne comprend pas → humain prend le relais.

## **3. Technique**

### **Q3.1 : Expliquez le rôle de Mistral AI dans notre application.**

**Mistral** est le fournisseur du modèle de langage utilisé pour :

- **comprendre les phrases de l’utilisateur**,
- **extraire des entités** (ex. : villes),
- **reformuler et générer des réponses**.

Il sert d’**intelligence conversationnelle** de l’agent.

### **Q3.2 : Pourquoi utilise-t-on `response_format={"type": "json_object"}` dans la fonction `extraire_ville()` ?**

- **Pour obliger le modèle à renvoyer une structure JSON propre et exploitable.**
- **Cela évite les erreurs de parsing, les variations naturelles du langage et les réponses ambiguës.**

Exemple souhaité :

```json
{"ville": "Paris"}
```

### **Q3.3 : Comment pourrait-on gérer plusieurs langues dans l’agent conversationnel ?**

Plusieurs stratégies possibles :

- **Détection automatique de langue** (via un modèle ou l’API Mistral → instruction : "detect language only").
- **Prompts multilingues** indiquant au modèle de répondre dans la langue détectée.
- **Traduction interne** : traduire → traiter → retraduire.
- **Déployer un modèle différent par langue** (moins courant).
- **Ajouter des fichiers de ressources multilingues** pour les réponses statiques.
