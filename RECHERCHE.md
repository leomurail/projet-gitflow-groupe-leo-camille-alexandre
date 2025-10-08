# **1 – Recherche et compréhension**

[https://grafikart.fr/tutoriels/git-flow-742](https://grafikart.fr/tutoriels/git-flow-742)

### [https://www.abtasty.com/fr/blog/gestion-de-branches-git/\#:\~:text=Consid%C3%A9r%C3%A9%20comme%20assez%20compliqu%C3%A9%20et,%C3%A0%20partir%20de%20celle%2Dci.](https://www.abtasty.com/fr/blog/gestion-de-branches-git/#:~:text=Consid%C3%A9r%C3%A9%20comme%20assez%20compliqu%C3%A9%20et,%C3%A0%20partir%20de%20celle%2Dci)

Git Flow a été proposé en 2010 par Vincent Driessen, développeur néerlandais, dans un article devenu une référence du développement collaboratif sur Git. Son objectif : organiser clairement le cycle de vie du code (développement, test, production) grâce à une structure de branches rigoureuse.

### **✅ Avantages de Git Flow**

1. **Protection du code de production**

   * La branche principale (master/main) reste toujours stable et prête pour la mise en production.

   * Les nouvelles fonctionnalités, corrections ou tests se font sur des branches séparées.

2. **Développement parallèle**

   * Plusieurs développeurs peuvent travailler en même temps sans risquer de casser le code principal.

   * Cela facilite la collaboration dans une équipe, même sur des parties différentes du projet.

3. **Organisation claire du travail**

   * Chaque type de branche a un but précis :

     * `feature` pour les nouvelles fonctionnalités,

     * `release` pour préparer une version,

     * `hotfix` pour corriger rapidement un bug en production.

   * Cela donne un cadre clair et structuré au travail de développement.

4. **Gestion de plusieurs versions**

   * Git Flow est pratique pour maintenir plusieurs versions du projet (ex : une version en production et une en développement).

---

### **⚠️ Limites de Git Flow**

1. **Complexité du modèle**

   * Le nombre de branches et d’étapes peut vite devenir difficile à suivre, surtout pour une petite équipe ou des étudiants.

   * Il faut savoir bien fusionner les branches dans le bon ordre (feature → develop → release → main), sinon on se perd facilement.

2. **Risque d’erreurs lors des fusions**

   * Quand plusieurs développeurs travaillent en même temps, les conflits peuvent se multiplier.

   * Si un test échoue, il est parfois compliqué de savoir d’où vient le problème.

3. **Lenteur du processus**

   * À cause de toutes les étapes de création et de fusion des branches, Git Flow peut ralentir le développement.

   * Il n’est pas adapté aux équipes qui veulent faire de l’intégration continue (CI) ou du déploiement continu (CD), car ces méthodes demandent des livraisons rapides et fréquentes.

4. **Moins adapté aux petits projets**

   * Pour un projet étudiant ou une petite équipe, Git Flow peut être trop lourd à gérer.

   * Dans ce cas, un modèle plus simple comme **GitHub Flow** est souvent plus efficace.

### 🔹 Objectifs

* WorkFlow qui permet de simplifier l’organisation des branches  
* Structurer le travail d’une équipe sur un même projet.

* Faciliter la **gestion des versions** (release, correctifs, hotfix…).

* Éviter les conflits entre les branches de développement et de production.

* Permettre plusieurs cycles de développement **en parallèle**.

### 

### 🔹 Le **Versionnement sémantique (SemVer)**

Principe

Le versionnement sémantique est une convention normalisée pour numéroter les versions logicielles sous la forme :

MAJOR.MINOR.PATCH

| Partie | Signification | Exemple |
| :---: | :---: | :---: |
| MAJOR | Changements **incompatibles** avec les versions précédentes | 1.x \-\> 2.0 |
| MINOR | Nouvelles fonctionnalités **compatibles** avec les versions précédentes | 2.3 \-\> 2.4 |
| PATCH | Correction de bugs ou améliorations mineures | 2.4.0 \-\> 2.4.1 |

### **🔹 Rôle du changelog et de la documentation**

* Le **CHANGELOG.md** liste les changements entre chaque version :

  * Nouveautés (`Added`)

  * Modifications (`Changed`)

  * Corrections (`Fixed`)

  * Suppressions (`Removed`)

Exemple :

![][image1]

### 

### 

### **🔹** Lien entre **Issues**, **Milestones** et **Releases** (GitHub)

| Élément | Description | Exemple |
| :---- | :---- | :---- |
| Issue | Représente une tâche un bug ou une amélioration à faire | \#12 “Ajouter le formulaire de contact” |
| Milestone | Regroupe plusieurs issues dans un objectif commun (souvent une version) | Milestone “v1.0”, contenant les issues \#12, \#13, \#14 |
| Release | Version publiée du code correspondant à une milestone terminée | Release “v1.0.0” basée sur le tag Git V1.0.0 |

Commande git flow

| Command | Purpose | Example |
| :---- | :---- | :---- |
| git flow init | Initializes a repository for the Gitflow workflow by creating the main and develop branches and asking for naming conventions. | git flow init |
| git flow feature start | Starts a new feature branch, branching off from develop, and switches to it. | git flow feature start new-login |
| git flow feature finish | Merges the completed feature branch into develop and deletes the feature branch. | git flow feature finish new-login |
| git flow release start | Starts a new release branch, branching off from develop, for final bug fixes and prep. | git flow release start 1.4.0 |
| git flow release finish | Merges the release branch into main (and tags it with the version), merges it back into develop, and deletes the release branch. | git flow release finish 1.4.0 |
| git flow hotfix start | Starts a hotfix branch, branching off from main, to fix critical bugs in production. | git flow hotfix start 1.4.1 |
| git flow hotfix finish | Merges the hotfix branch into both main (and tags it) and develop, and deletes the hotfix branch. | git flow hotfix finish 1.4.1 |

[image1]: <data:image/png;base64,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>