# Analyse Quantitative & Gestion des Risques (VaR / CVaR)

## 📋 Description du Projet

Ce projet a pour objectif de modéliser et d'analyser les risques financiers d'un portefeuille multi-actifs (Actions, Obligations, Matières Premières). Il implémente une architecture modulaire pour calculer deux mesures phares du risque bancaire :

- **VaR (Value at Risk) :** La perte maximale potentielle à un seuil de confiance donné.
- **CVaR (Conditional Value at Risk) :** La perte moyenne anticipée en cas de dépassement de la VaR (aussi appelée Expected Shortfall).

L'outil permet de comparer les approches théoriques (Loi Normale) face à la réalité des marchés (Queues épaisses / Fat Tails) et de simuler des scénarios de crise (Stress Testing).

**Note :** Ce projet est actuellement en cours de développement et d'optimisation.

## 🚀 Fonctionnalités Clés

- **Acquisition de Données :** Téléchargement automatique des cours historiques via l'API `yfinance`.
- **Gestion de Portefeuille :** Calcul des rendements logarithmiques, matrices de covariance et pondération personnalisée.
- **3 Moteurs de Calcul de Risque :**
    - **Méthode Paramétrique (Variance-Covariance) :** Basée sur l'hypothèse de normalité.
    - **Méthode Historique :** Basée sur les distributions empiriques passées (capture les "Queues Épaisses").
    - **Simulation de Monte Carlo :** Génération de milliers de scénarios aléatoires.
- **Stress Testing :** Simulation de crises via injection de multiplicateurs de volatilité (Scénarios "Black Swan").
- **Visualisation Avancée :**
    - Comparaison des distributions (Normale vs Crise).
    - Rolling VaR : Analyse dynamique du risque sur fenêtre glissante (Backtesting).

## 📂 Structure du Projet

L'architecture suit les standards "Clean Code" pour la Data Science :

```
Risk-Var-CVAR/
│
├── main.py                # 🏁 Script principal (Orchestrateur)
├── requirements.txt       # 📦 Liste des dépendances
├── README.md              # 📄 Documentation
│
├── src/                   # 🧠 Cœur du réacteur (Modules réutilisables)
│   ├── data_loader.py     # Chargement et nettoyage des données
│   ├── risk_factors.py    # Calculs statistiques (Volatilité, Covariance)
│   ├── var_modules.py     # Algorithmes de VaR et CVaR
│   └── stress_scenarios.py# Définition des paramètres de crise
│
└── notebooks/             # 🧪 Laboratoire d'analyse (Jupyter)
    ├── 01_data_exploration.ipynb  # Analyse des corrélations
    ├── 02_var_calculation.ipynb   # Comparaison des modèles
    ├── 03_stress_testing.ipynb    # Simulation Monte Carlo
    └── 04_results_analysis.ipynb  # Synthèse et Tableaux
```

## 🛠️ Installation et Utilisation

### 1. Pré-requis

Assurez-vous d'avoir Python installé. Clonez ce dépôt et installez les dépendances :

```bash
git clone https://github.com/votre-username/Risk-Var-CVAR.git
cd Risk-Var-CVAR
pip install -r requirements.txt
```

### 2. Lancer le Programme Principal

Pour exécuter l'analyse complète et voir les résultats dans le terminal :

```bash
python main.py
```

### 3. Explorer les Notebooks

Pour visualiser les graphiques et modifier les paramètres (poids du portefeuille, horizon temporel) de manière interactive :

```bash
jupyter notebook notebooks/
```

## 📊 Aperçu des Résultats

### Comparaison des Distributions (Stress Test)

Le graphique ci-dessous (généré par le projet) montre comment une crise majeure aplatit la courbe des rendements, augmentant drastiquement la probabilité de pertes extrêmes.

*(Insérer ici l'image de l'histogramme Bleu/Rouge)*

### Analyse Dynamique (Rolling VaR)

Suivi de l'évolution du risque historique jour après jour, permettant d'identifier les périodes de haute volatilité (ex: Covid-19 en 2020).

*(Insérer ici l'image de la VaR Roulante)*

## 🧮 Méthodologie

Le projet compare principalement :

- **VaR Paramétrique 95% :**

$$VaR = \mu - \sigma \cdot Z_{95\%}$$

Rapide mais sous-estime souvent le risque.

- **CVaR (Expected Shortfall) :**

$$CVaR_{\alpha} = E[X | X \leq VaR_{\alpha}]$$

Mesure plus robuste qui quantifie la moyenne des pertes dans le "worst-case scenario".

## 🚧 Roadmap / À Faire

- [x] Implémentation des modules de calcul de base.
- [x] Ajout du module de Stress Testing (Monte Carlo).
- [x] Visualisation Rolling VaR (Backtesting).
- [ ] Ajout d'une interface graphique (Streamlit ou Dash).
- [ ] Intégration de nouveaux actifs (Cryptomonnaies).
- [ ] Optimisation automatique des poids du portefeuille (Frontière efficiente).



Étudiant en Finance / Data Science

Projet réalisé dans le cadre du cours "Gestion des Risques Financiers".

## Disclaimer

Ce projet est à but éducatif et ne constitue pas un conseil en investissement.
