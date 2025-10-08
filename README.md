## 💻 Projet Fictif : "EventPulse"

**Description :** EventPulse est une **application web et mobile de gestion d'événements**. Elle permet aux utilisateurs de créer, promouvoir et vendre des billets pour leurs événements (concerts, conférences, ateliers, etc.), et aux participants de les découvrir et d'acheter des places.

**Contexte d'utilisation de Git Flow :** Ce projet gère des **versions stables critiques** (billetterie, paiements) qui doivent être absolument isolées du développement en cours. Git Flow est choisi pour sa capacité à gérer des cycles de livraison planifiés et des correctifs d'urgence sans perturber la *feature factory*.

---

## 🚀 Version Actuelle

| Statut | Branche | Explication |
| :--- | :--- | :--- |
| **Production** (Stable) | `main` | **v2.0.1** (Dernière version stable, incluant le dernier *hotfix* critique). |
| **Développement** (Intégration) | `develop` | **v2.1.0-alpha** (Travail en cours pour la prochaine version majeure : ajouts de filtres de recherche et d'un système de notifications). |

---

## 🗺️ Schéma Conceptuel du Workflow Git Flow

Le modèle Git Flow est basé sur la coexistence de deux branches permanentes (`main` et `develop`) et de branches temporaires pour les tâches spécifiques.

### Flux de Travail Simplifié

1. Les développeurs travaillent sur des branches **`feature/*`** créées à partir de `develop`.
2. Une fois une fonctionnalité terminée, elle est fusionnée dans **`develop`** (intégration).
3. Pour préparer une livraison, une branche **`release/vX.Y`** est créée à partir de `develop` pour les tests et les derniers ajustements.
4. Une fois la `release` validée, elle est fusionnée simultanément dans **`main`** (déploiement en production) et dans **`develop`** (pour propager les ajustements de la version).
5. En cas de bug critique en production, une branche **`hotfix/*`** est créée directement à partir de **`main`** et fusionnée dans **`main`** et **`develop`**.

---

## 🎨 Légende Détaillée des Branches

### Branches Principales (Longue Durée)

| Nom de la Branche | Rôle / Objectif | Explication dans EventPulse |
| :--- | :--- | :--- |
| **`main`** ou **`master`** | **Production & Stabilité.** Contient uniquement le code qui est en service et stable. Chaque *commit* sur cette branche est une version déployée. | L'état de l'application que voient les utilisateurs finaux (la billetterie fonctionne et est sécurisée). |
| **`develop`** | **Intégration & Développement.** C'est la branche par défaut pour le travail quotidien. Elle rassemble toutes les fonctionnalités en cours de développement avant le prochain cycle de livraison. | L'état actuel de l'application, en cours de test interne (QA/Staging), mais pas encore stable pour la production. |

### Branches de Support (Courte Durée)

| Type de Branche | Nommage Typique | Base de Création | Cible de Fusion | Rôle Spécifique |
| :--- | :--- | :--- | :--- | :--- |
| **Feature** | `feature/ajouter-chat-live` | **`develop`** | **`develop`** | Développement d'une nouvelle fonctionnalité majeure. Isoler le code jusqu'à ce qu'il soit complet et prêt pour l'intégration. |
| **Release** | `release/v2.1.0` | **`develop`** | **`main`** **et** **`develop`** | Préparation du lancement d'une nouvelle version. Permet les tests finaux, la documentation, et les corrections liées à la version. |
<<<<<<< Updated upstream
| **Hotfix** | `hotfix/corriger-paiement-paypal` | **`main`** | **`main`** **et** **`develop`** | Correction rapide d'un bug critique ou d'une faille de sécurité en production. Doit être déployé immédiatement sans attendre le cycle de `release`. |

=======
| **Hotfix** | `hotfix/corriger-paiement-paypal` | **`main`** | **`main`** **et** **`develop`** | Correction rapide d'un bug critique ou d'une faille de sécurité en production. Doit être déployé immédiatement sans attendre le cycle de `release`. |
>>>>>>> Stashed changes
