# Documentation Technique – Projet Coachly (Stage 3)

## Sommaire

1. [User Stories & Mockups](#-étape-1--user-stories--mockups)
2. [Architecture du système](#-étape-2--architecture-du-système)
3. [Composants, Classes et Design de Données](#-étape-3--composants-classes-et-structure-de-données)
4. [Diagrammes de Séquence](#-étape-4--diagrammes-de-séquence)
5. [Spécifications des APIs](#-étape-5--apis-internes-et-externes)
6. [Stratégies SCM & QA](#-étape-6--gestion-de-code--tests)
7. [Justifications Techniques](#-étape-7--justifications-techniques)

---

## Étape 1 – User Stories & Mockups

### User Stories (MoSCoW)

#### Must Have
- En tant qu’utilisateur, je veux entrer mes données personnelles (âge, poids, objectif), afin d’obtenir un programme adapté.
- En tant qu’utilisateur, je veux recevoir un programme de sport personnalisé, pour m’entraîner efficacement chez moi.
- En tant qu’utilisateur, je veux obtenir un plan nutritionnel simple, pour suivre une alimentation alignée avec mes objectifs.

#### Should Have
- En tant qu’utilisateur, je veux indiquer mes préférences alimentaires (végétarien, sans gluten), afin que le programme respecte mes choix.

#### Could Have
- En tant qu’utilisateur, je veux pouvoir partager mon programme avec un ami, pour rester motivé ensemble.

#### Won’t Have
- En tant qu’utilisateur, je veux pouvoir sauvegarder mon historique de progrès, afin de suivre mon évolution (hors MVP).

### Mockups (à créer)
- Formulaire de saisie des données utilisateur
- Affichage du programme généré (sport + nutrition)
- Écran d’accueil (optionnel)

---

## Étape 2 – Architecture du système

### Composants

- **Frontend** : HTML/CSS/JS ou React
- **Backend** : Flask (Python)
- **Logique métier** : Génération de programmes
- **API externe (optionnelle)** : OpenAI
- **Base de données** : Aucune dans le MVP

### Flux

[ Utilisateur ]
│
▼
[ Frontend HTML/CSS/JS ]
│ POST /generate
▼
[ Backend Flask (Python) ]
│
├──> [ FitnessPlanGenerator ]
├──> [ NutritionPlanGenerator ]
▼
[ JSON résultat structuré ]
│
▼
[ Frontend - Affichage Programme ]


---

## Étape 3 – Composants, Classes et Structure de Données

### Composants Backend

| Composant                | Rôle                                                                 |
|--------------------------|----------------------------------------------------------------------|
| `UserProfile`            | Données utilisateur                                                  |
| `FitnessPlanGenerator`   | Génère un programme de sport                                         |
| `NutritionPlanGenerator` | Génère un plan nutritionnel                                          |
| `ProgramFormatter`       | Retourne un JSON propre à afficher                                   |

### Exemple JSON

```json
{
  "user_profile": {
    "age": 25,
    "weight": 70,
    "goal": "perte de poids",
    "preferences": ["végétarien"]
  },
  "fitness_plan": [...],
  "nutrition_plan": [...]
}

class UserProfile: ...
class FitnessPlanGenerator: ...
class NutritionPlanGenerator: ...
class ProgramFormatter: ...


```


## Étape 4  – Diagrammes de Séquence


Utilisateur → Frontend : saisie des données
Frontend → Backend : POST /generate
Backend → Generators : traitement
Generators → Backend : plans générés
Backend → Frontend : JSON
Frontend → Utilisateur : Affichage du programme


---

## Étape 5 – APIs internes et externes

API interne
Méthode	Endpoint	Input (JSON)	Output (JSON)
POST	/generate	age, poids, objectif, préférences	plan sportif + plan nutritionnel

API externe (optionnelle)
OpenAI API : génération de suggestions sport/nutrition

Format : texte brut ou JSON structuré

Raison : enrichir la personnalisation sans base de données

## Étape 6 – Gestion de code & Tests