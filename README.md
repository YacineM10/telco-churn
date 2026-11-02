# Prédiction du churn client — Telco

Identifier les clients d'un opérateur télécom qui risquent de partir, et comprendre pourquoi.

## Contexte

26,5 % des clients ont quitté l'opérateur. L'objectif : repérer les clients
à risque pour cibler des actions de rétention (offres, contrats plus longs).

## Principaux résultats

**Profil du client à risque** : client récent, en contrat mensuel, abonné à la fibre,
sans options de sécurité ou de support, payant par chèque électronique.

| Modèle | Precision | Recall | ROC-AUC |
|---|---|---|---|
| Régression logistique | 0,50 | 0,78 | 0,84 |
| Random Forest | 0,53 | 0,80 | 0,84 |
| XGBoost | 0,52 | 0,77 | 0,84 |

Les trois modèles sont équivalents. **La régression logistique est retenue** :
aussi performante, et plus facile à expliquer au métier.

## Démarche

1. **Exploration** (`01_exploration.ipynb`) : nettoyage, analyse de la cible,
   lien entre chaque variable et le churn
2. **Modélisation** (`02_modelisation.ipynb`) : Pipeline scikit-learn,
   gestion du déséquilibre des classes, correction du surapprentissage,
   comparaison des modèles, interprétation des coefficients

Choix clés :
- **Recall privilégié** : rater un client qui part coûte plus cher qu'une offre envoyée pour rien
- **Accuracy écartée** : trompeuse avec des classes déséquilibrées

## Lancer le projet

```bash
pip install -r requirements.txt
```

Télécharger le dataset sur [Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
et le placer dans `data/`.

## Stack

Python · pandas · scikit-learn · XGBoost · seaborn