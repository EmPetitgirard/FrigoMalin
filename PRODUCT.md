# FrigoMalin

## En bref

FrigoMalin est l’application anti-gaspillage du foyer. Elle aide chacun à savoir ce qu’il a dans son réfrigérateur et ses placards, à repérer les aliments à consommer bientôt et à mieux préparer les repas et les courses.

FrigoMalin est une application web progressive (PWA), installable et conçue pour rester utilisable hors ligne. Elle fonctionne entièrement dans le navigateur : aucun backend ni Docker ne sont nécessaires. Les données du foyer sont stockées localement sur l’appareil.

## Pour qui ?

Pour tous les foyers qui veulent réduire les aliments oubliés, éviter les achats en double et organiser plus facilement les repas du quotidien.

## Le problème

Les aliments se perdent facilement dans le réfrigérateur ou les placards. Les dates sont oubliées, les stocks sont difficiles à mémoriser et les courses peuvent déjà contenir des produits disponibles à la maison. FrigoMalin rassemble ces informations pour aider à agir au bon moment.

## Expérience principale

1. Ajouter les produits de la maison à l’inventaire, notamment par scan de code-barres avec les informations produit d’Open Food Facts.
2. Renseigner et suivre les dates DLC et DDM afin d’identifier les aliments à utiliser en priorité.
3. Ouvrir « Que cuisiner ? » pour trouver des idées à partir des produits disponibles, en mettant en avant ceux qui expirent bientôt.
4. Préparer une liste de courses qui signale les produits déjà présents afin de limiter les doublons.
5. Suivre les quantités et économies estimées grâce au tableau « kg et € sauvés ».

## Fonctionnalités

- Inventaire du réfrigérateur et des placards.
- Scan de codes-barres et récupération d’informations produit auprès d’Open Food Facts.
- Suivi des dates DLC et DDM.
- Suggestions de repas à partir des aliments à disposition et de leurs dates.
- Liste de courses anti-doublon, rapprochée de l’inventaire.
- Tableau de bord des kilogrammes et euros estimés comme sauvés.
- Installation comme PWA et utilisation hors ligne, avec les données conservées localement sur l’appareil.

## Principes produit

- **Utile au quotidien** : faciliter l’inventaire, le choix des repas et les courses sans ajouter de complexité.
- **Priorité aux aliments à sauver** : rendre visibles les produits à consommer en premier.
- **Compréhensible** : distinguer les dates DLC et DDM et présenter les économies comme des estimations.
- **Local et autonome** : fonctionner dans le navigateur, sans backend, et rester accessible hors ligne.

## Hors périmètre

- Backend, comptes en ligne ou synchronisation entre appareils.
- Déploiement ou dépendance à Docker.

La consultation d’Open Food Facts peut nécessiter une connexion réseau ; le mode hors ligne concerne l’application et les données déjà disponibles localement.