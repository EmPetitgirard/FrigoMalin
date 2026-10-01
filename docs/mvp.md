# Périmètre du POC FrigoMalin

## Objectif

Valider qu’un foyer peut inventorier ses aliments, repérer ceux à consommer bientôt et éviter les achats en double depuis une application web installable, utilisable hors ligne et hébergée uniquement avec des fichiers statiques.

La référence produit est [PRODUCT.md](../PRODUCT.md). La priorisation utilise **MoSCoW** : **MUST** est indispensable au POC, **SHOULD** apporte de la valeur sans bloquer sa validation, **COULD** est facultatif et **WON'T** est exclu de cette version.

## Périmètre priorisé

| Fonctionnalité | Priorité | Justification | Critère |
|---|---|---|---|
| Application client-only distribuée comme fichiers statiques | MUST | Respecte la contrainte d’hébergement et garde l’architecture minimale. | L’application fonctionne depuis un hébergement statique HTTPS, sans serveur applicatif, backend ni Docker. |
| Inventaire du réfrigérateur et des placards | MUST | C’est la source des recommandations repas et de la vérification des courses. | L’utilisateur peut ajouter, consulter, modifier et supprimer un produit avec nom, quantité et emplacement ; les changements persistent après rechargement. |
| Scan de code-barres par caméra | MUST | Accélère la saisie et constitue le parcours de référence du produit. | Sur un téléphone compatible, caméra autorisée et éclairage usuel, le code est reconnu et le formulaire de saisie affiché avec le code renseigné en moins de 5 s dans au moins 9 essais sur 10, à partir du moment où le code entre dans le viseur. |
| Recherche de fiche Open Food Facts | MUST | Réduit la saisie après le scan, sans introduire de backend propre. | En ligne, une fiche trouvée préremplit les informations disponibles ; si le service est lent, indisponible ou le produit absent, la saisie manuelle reste possible sans bloquer le scan. |
| Saisie manuelle d’un produit | MUST | Rend l’inventaire utilisable sans caméra, code connu ou connexion. | Un produit peut être enregistré manuellement et retrouvé dans l’inventaire en mode hors ligne. |
| Dates DLC et DDM | MUST | Permet de prioriser les aliments à consommer et d’éviter les confusions de date. | Chaque produit peut recevoir une date et un type DLC ou DDM ; l’inventaire permet d’identifier les produits arrivant à échéance en premier. |
| « Que cuisiner ? » à partir des produits à utiliser bientôt | MUST | Transforme l’inventaire en action concrète contre le gaspillage. | Avec un jeu de données de démonstration comprenant un produit proche de sa date, l’écran propose au moins une idée et met en évidence ce produit ; le calcul fonctionne sans réseau. |
| Liste de courses anti-doublon | MUST | Évite d’acheter un produit déjà présent au foyer. | Lorsqu’un produit de l’inventaire est ajouté à la liste, il est signalé comme déjà disponible et n’est pas ajouté une seconde fois par défaut. |
| PWA installable et parcours essentiel hors ligne | MUST | Permet l’usage quotidien et l’accès à l’inventaire sans connexion. | Après un premier chargement en ligne, l’application s’ouvre hors ligne ; inventaire, dates, suggestions locales et liste de courses restent consultables et modifiables. Sur les navigateurs compatibles, l’installation PWA est proposée. |
| Tableau « kg et € sauvés » | SHOULD | Rend l’impact visible, mais son calcul n’est pas nécessaire pour valider le parcours central. | Les produits marqués comme sauvés contribuent à des totaux présentés comme estimations ; poids et valeur manquants sont signalés plutôt que présentés comme des mesures exactes. |
| Backend, comptes et synchronisation entre appareils | WON'T | Incompatibles avec le POC statique et le stockage local retenu. | Aucun compte ni service backend n’est requis ; les données restent sur l’appareil et ne se synchronisent pas. |
| Docker et services de recettes distants | WON'T | Inutiles pour livrer l’expérience statique et rendraient le mode hors ligne dépendant du réseau. | Le démarrage et l’usage du POC ne requièrent ni Docker ni API de recettes. |

## Hypothèses et limites

- Le navigateur doit être servi en HTTPS pour permettre l’accès caméra et le service worker, sauf en développement local.
- Les données de l’utilisateur sont enregistrées localement dans le navigateur. Effacer ses données de site ou changer d’appareil peut donc les rendre indisponibles.
- La consultation d’Open Food Facts nécessite une connexion ; elle enrichit le produit en arrière-plan et ne fait pas partie du chronomètre de reconnaissance du code.
- Hors connexion, le scan peut identifier le code si la caméra fonctionne, mais les informations produit doivent être saisies ou provenir des données locales.
- Le critère des 5 s est vérifié sur un téléphone compatible, avec permission caméra accordée, éclairage usuel et code-barres dans le viseur. Il mesure la reconnaissance et l’affichage du formulaire, pas le temps de réponse d’un service externe.
- Les suggestions du POC reposent sur des règles et données embarquées localement ; elles ne constituent pas un moteur de recettes complet.
- Les valeurs du tableau d’impact sont des estimations dépendant des quantités, poids et valeurs connus ou saisis.

## Validation du POC

Le POC est concluant si les critères MUST sont satisfaits, notamment le test de scan (au moins 9 réussites sur 10 sous 5 s), la persistance locale après rechargement, et la consultation et modification des données essentielles après le premier chargement hors ligne. Le déploiement de validation doit servir uniquement des fichiers statiques, sans backend ni Docker..