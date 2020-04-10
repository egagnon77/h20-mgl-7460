# Projet Individuel MGL-7460-90 (Hiver 2020)
## Analyse du projet ReactiveX/RxJs par Eric Gagnon
* [WebSite](https://rxjs.dev/)
* [Source code](https://github.com/ReactiveX/rxjs)

## Rapport intermédiaire
[Intermédiaire en PDF](https://github.com/egagnon77/h20-mgl-7460/blob/master/rapports/rapport_intermediaire.pdf)

## Rapport final
[Final en PDF](https://github.com/egagnon77/h20-mgl-7460/blob/master/rapports/rapport_final.pdf)

## Outils utilisé pour l'analyse

### Sonarqube
https://www.sonarqube.org/

#### Prérequis
* Récupérer le code source sur votre poste de travail.
* Avoir un serveur pour héberger l'analyse.
* L'outils [SonarScanner](https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/) pour lancer l'analyse.

#### Récupérer le code source
```bash
git clone https://github.com/ReactiveX/rxjs.git
```

#### Hébergement
Pour héberger l'analyse j'ai utilisé [SonarCloud](http://sonarcloud.io/).
C'est gratuit pour les projets publiques et aucune limitation.

#### Lancer l'analyse
J'ai utilisé le package NPM [Sonarqube Scanner](https://www.npmjs.com/package/sonarqube-scanner).

Installation:
```bash
npm install -D sonarqube-scanner
```

Lancement de l'analyse
```bash
npx sonar-scanner -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=yourlogin -Dsonar.organization=school-project-uqam -Dsonar.projectKey=r_x_j_s
```

#### Résultat de l'analyse
[Analyse Sonarqube](https://sonarcloud.io/dashboard?id=r_x_j_s)

### Codescene
https://codescene.io/

#### Prérequis
* Créer un fork du projet RxJs dans votre Github.
  * Le projet doit être public sur GitHub
* Avoir un compte Codescene lié à votre GitHub.
  * [documentation](https://codescene.io/docs/getting-started/index.html)

#### Générer l'analyse
* Ajouter un projet dans CodeScene.
* Choisir le votre repository RxJs public.

#### Configuration spéciale
Pour avoir une analyse qui représente le plus possible la réalité j'ai ajusté les configuration par l'ajout de l'équipe Core, des filtres et exclusions pour ignorer les fichiers de configuration et de tests, le mapping au système de Ticket de RxJs et l'ajout des composantes de l'architecture.

Dans la configuration du projet:
[documentation](https://codescene.io/docs/configuration/projects.html#)

* Teams
  * Création de l'équipe core et ajout de ses membres.
* Exclusions & Filter 
  * Exclusion Filter: *.json;*.yml;*.sh;*.md;*.txt;*.html;*.css;*.scss;*.xml;*spec.ts
  * Exclude Content: rxjs/spec/\*\*;rxjs/spec-dtslint/\*\*;rxjs/doc/\*\*;rxjs/integration/\*\*;rxjs/tools/\*\*;rxjs/docs_app/\*\*
* Ticket ID Mapping
  * Ticket ID Pattern: #(\d+) 
* Architectural Components
  * Component: Observable
    * Patterns:
      * rxjs/src/internal/observable/**
      * rxjs/src/internal/Observer.ts
      * rxjs/src/internal/Observable.ts
      * rxjs/src/internal/*Subject.ts
  * Component: Operators
    * Patterns:
      * rxjs/src/internal/operators/**
      * rxjs/src/internal/Operators.ts
  * Component: Scheduler
    * Patterns:
      * rxjs/src/internal/scheduled/**
      * rxjs/src/internal/scheduler/**
  * Component: Subscription
    * Patterns:
      * rxjs/src/internal/*Subscriber.ts
      * rxjs/src/internal/*Subscription.ts
      * rxjs/src/internal/Subscription.ts
      * rxjs/src/internal/Subscriber.ts
  * Component: Testing
    * Patterns:
      * rxjs/src/internal/testing/**

#### Limitation
Le compte gratuit ne permet pas de dépot de code privé et vous devez aussi être propriétaire du code (c'est pour cela le fork).

#### Resultat de l'analyse
[Analyse CodeScene](https://codescene.io/projects/7238/jobs/23304/results)