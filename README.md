# 🌤️ Agent Conversationnel Météo - TP BTS SIO SLAM

Agent conversationnel intelligent qui fournit des informations météorologiques en utilisant Mistral AI et l'API OpenWeatherMap, conforme aux recommandations CNIL.

## 🚀 Démarrage rapide (5 minutes)

### 1. Prérequis
- Python 3.8 ou supérieur
- Compte gratuit Mistral AI : https://console.mistral.ai/
- Compte gratuit OpenWeatherMap : https://openweathermap.org/api

### 2. Installation

```bash
# Cloner ou télécharger ce projet

# Créer un environnement virtuel
python -m venv venv

# Activer l'environnement virtuel
# Sur Windows :
venv\Scripts\activate
# Sur Mac/Linux :
source venv/bin/activate

# Installer les dépendances
pip install -r requirements.txt
```

### 3. Configuration des clés API

```bash
# Copier le fichier exemple
cp .env.example .env

# Éditer le fichier .env et ajouter vos clés API
# MISTRAL_API_KEY=votre_cle_mistral
# OPENWEATHER_API_KEY=votre_cle_openweather
```

#### Obtenir les clés API :

**Mistral AI** (5€ gratuits à l'inscription) :
1. Créer un compte sur https://console.mistral.ai/
2. Aller dans "API Keys"
3. Créer une nouvelle clé et la copier

**OpenWeatherMap** (1000 appels/jour gratuits) :
1. Créer un compte sur https://openweathermap.org/
2. Aller dans "API Keys"
3. Copier la clé par défaut

### 4. Lancer l'application

```bash
# Démarrer le serveur Flask
python app.py
```

Ouvrir votre navigateur : http://localhost:5000

## 📁 Structure du projet

```
tp_meteo_mistral/
├── .env                    # Clés API (à créer à partir de .env.example)
├── .env.example            # Modèle de configuration
├── .gitignore             # Fichiers à ignorer (inclut .env)
├── requirements.txt       # Dépendances Python
├── README.md              # Ce fichier
├── agent_meteo.py         # Logique de l'agent conversationnel
├── app.py                 # Application Flask
├── templates/
│   └── index.html         # Interface web
└── static/
    └── style.css          # Style CSS
```

## 🎯 Fonctionnalités

- ✅ **Agent conversationnel** intelligent avec Mistral AI
- ✅ **Données météo en temps réel** via OpenWeatherMap
- ✅ **Interface web moderne** et responsive
- ✅ **Conforme CNIL** : transparence, minimisation, pas de stockage
- ✅ **Traitement du langage naturel** pour extraire les villes
- ✅ **Réponses personnalisées** et contextuelles

## 💬 Exemples d'utilisation

```
Vous : Quel temps fait-il à Paris ?
Bot : À Paris, il fait actuellement 15°C avec un ciel dégagé. 
      Parfait pour une balade ! 🌤️

Vous : Météo Lyon
Bot : À Lyon, la température est de 18°C avec quelques nuages. 
      N'oubliez pas une petite veste ! ☁️

Vous : J'aimerais savoir le temps qu'il fait à Marseille
Bot : À Marseille, il fait 22°C avec un grand soleil ! 
      Idéal pour profiter de la plage ! ☀️
```

## 🛡️ Conformité CNIL

Cette application respecte les recommandations de la CNIL pour les agents conversationnels :

- **Transparence** : L'utilisateur est informé qu'il interagit avec un robot
- **Minimisation** : Seul le nom de la ville est collecté
- **Pas de stockage** : Aucune conversation n'est enregistrée
- **Sécurité** : Les clés API sont stockées dans .env (non versionné)
- **Information** : Une bannière explique le fonctionnement

## 🔧 Test du code

```bash
# Tester l'agent conversationnel directement
python agent_meteo.py
```

## 📚 Ressources

- [Documentation CNIL - Agents conversationnels](https://www.cnil.fr/fr/intelligence-artificielle/lintelligence-artificielle-qui-parle-les-agents-conversationnels)
- [Documentation Mistral AI](https://docs.mistral.ai/)
- [Documentation OpenWeatherMap](https://openweathermap.org/api)

## ⚠️ Dépannage

**Erreur "Clés API manquantes"** :
- Vérifiez que le fichier `.env` existe (copié depuis `.env.example`)
- Vérifiez que vos clés sont correctement ajoutées dans `.env`

**Erreur "Ville non trouvée"** :
- Vérifiez l'orthographe du nom de la ville
- Essayez en anglais pour les villes internationales

**Erreur Mistral AI** :
- Vérifiez votre crédit gratuit sur console.mistral.ai
- Vérifiez que votre clé API est valide

## 📝 Licence

Ce projet est à but éducatif dans le cadre du BTS SIO SLAM.

---

**Bon développement ! 🚀**
