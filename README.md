# finbiz.cloud — le site public

Ce dépôt ne contient **que du HTML généré**. Aucune source, aucune donnée brute, aucun secret.

Il est produit à partir des paquets du dépôt `scraper` par un générateur qui vit dans un dépôt
privé. Une modification faite directement ici serait écrasée à la prochaine génération.

## Ce que le site contient

- ce qu'est FinBiz, en une page
- comment les dépôts s'articulent, et lequel ouvrir
- les interfaces : ce que chaque système reçoit, rend et garantit
- comment exécuter la pile depuis un clone vide
- le répertoire des organisations, en lecture seule

## La règle du site

Un service n'apparaît que s'il est accompagné d'un extrait d'au moins huit mots, présent mot
pour mot sur une page de l'organisation qui le fournit, et du lien vers cette page. La
génération **refuse d'écrire** si un service manque à cette règle : ce n'est pas une consigne,
c'est un contrôle.

## Vérification

`.gitleaks-baseline.json` enregistre la seule détection connue, une chaîne longue contenue
dans une citation publique. Le contrôle signale toute détection *nouvelle*.

    gitleaks detect --source . --no-git --baseline-path .gitleaks-baseline.json
