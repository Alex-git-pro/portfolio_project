
# Coachly – Documentation Technique (Stage 4)

---

## 1. Planification des Sprints

### Objectif Sprint 1

Livrer une version fonctionnelle de Coachly permettant à un utilisateur de remplir un formulaire, de générer un plan personnalisé, et de le voir s’afficher.

###  Durée

Sprint 1 : 7 à 10 jours

### Priorisation (MoSCoW)

| Priorité     | Tâches                                                                 | Responsable  |
|--------------|------------------------------------------------------------------------|--------------|
| **Must Have** | Implémenter le formulaire utilisateur (âge, poids, objectifs)         | Développeur  |
|              | Créer l’API `/generate_plan` avec logique simple                      | Développeur  |
|              | Afficher le plan dans l’interface utilisateur                          | Développeur  |
|              | Mettre en place Git + branches (`main`, `dev`, `feature/*`)            | SCM          |
|              | Tester le flux principal manuellement                                  | QA           |
| **Should Have** | Ajout de validation dans le formulaire                              | Développeur  |
|              | Responsive design de base                                              | Développeur  |
| **Could Have** | Animation de chargement (loader)                                     | Développeur  |
| **Won’t Have** | Authentification ou sauvegarde de plan utilisateur                   | ❌            |

---

## 2. Exécution des tâches

- Développement des composants UI avec Next.js et Tailwind
- Implémentation de l’API Node.js `/generate_plan`
- Utilisation de données mockées ou logique simplifiée (rule-based)
- Création de branches Git :
  - `feature/user-form`
  - `feature/api-generate-plan`
  - `feature/result-display`
- Pull requests avec revue manuelle sur GitHub

---

## 3. Suivi et ajustements

### Outil : Trello (structure suggérée)

- **Colonnes** : Backlog / À faire / En cours / À tester / Fait
- Mise à jour quotidienne des cartes
- Blocages notés et priorisés
- Réévaluation des tâches en fonction de l’avancement

### Indicateurs de suivi

- % de tâches complétées vs planifiées
- Nombre de bugs relevés et corrigés
- Temps passé par composant

---

## 4. Sprint Review & Rétrospective

### Sprint Review

- Présentation live ou enregistrement du MVP
- Démonstration du parcours complet utilisateur :
  - Remplissage du formulaire
  - Réponse de l’API
  - Affichage dynamique du plan

### Rétrospective

**Ce qui a bien fonctionné :**
- Bonne structuration en composants réutilisables
- Déploiement rapide sur Vercel

**Ce qui a été difficile :**
- Ajustement du design responsive
- Premiers tests API avec Postman

**À améliorer :**
- Ajouter plus de tests automatisés
- Mieux découper les tâches dès le début

---

## 5. Intégration finale & QA

### Intégration

- Tests manuels sur le parcours utilisateur complet
- Vérification des erreurs côté serveur et client
- Intégration front/back validée en local et en ligne

### Plan de test QA

| Test Case                                  | Méthode          | Attendu                          | Statut |
|-------------------------------------------|------------------|----------------------------------|--------|
| Soumission d’un formulaire complet         | Manuel (UI)      | Plan affiché sans erreur         | ✅     |
| Soumission avec champ manquant             | Manuel (UI)      | Message d’erreur s’affiche       | ✅     |
| API `/generate_plan` valide                | Postman          | 200 OK + JSON structuré          | ✅     |
| API `/generate_plan` avec mauvais input    | Postman          | 400 Bad Request + message erreur | ✅     |
| Affichage responsive sur mobile            | Navigateur Dev   | UI lisible et fluide             | ✅     |

---
