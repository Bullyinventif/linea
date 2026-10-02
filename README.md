# Linea

Linea est un éditeur de frises chronologiques en français : créez une histoire, ajoutez ses dates et ses périodes, puis partagez-la ou imprimez-la.

> **État du dépôt :** la documentation est disponible. Les fichiers de l’application développée dans Work cloud restent à transférer ; les commandes ci-dessous fonctionneront après leur ajout. Ce dépôt ne contient pas encore le site exécutable.

## Fonctionnalités de la version développée

- Plusieurs frises, avec titre et description.
- Événements : année obligatoire, mois et jour facultatifs, nom et description.
- Périodes avec dates de début et de fin : 1918–1920 ou février–octobre d’une même année.
- Choix parmi 48 icônes ou ajout d’un emoji personnel, y compris les emojis composés.
- Couleurs par événement et images ajoutées depuis l’appareil ou depuis un lien.
- Consultation des descriptions et des images en cliquant sur un événement.
- Vues horizontale et verticale, affichage compact ou aéré.
- Modes clair, sombre et automatique, avec six couleurs pour l’application.
- Sauvegarde locale dans le navigateur, sans compte.

## Quatre styles

| Style | Présentation |
| --- | --- |
| **Liste claire** | Une carte par événement, dates en gros et périodes explicites. Proposé par défaut pour les nouvelles frises, en vertical. |
| **Épuré** | Cartes arrondies disposées autour d’une ligne chronologique. |
| **Chronologie** | Dates alignées dans une bande ; traits pour les dates ponctuelles et blocs reliant les débuts et fins des périodes. |
| **Aventure** | Un chemin entre des îlots, inspiré des cartes de sélection de mondes de jeux vidéo. |

Les repères sont classés chronologiquement. Leur espacement est régulier : la longueur des segments ne représente pas une durée proportionnelle.

## Ouvrir l’application

Après l’ajout des fichiers, deux possibilités :

### Sans installation

Ouvrez **`Linea.html`** dans un navigateur. Ce fichier autonome contient l’éditeur et fonctionne hors ligne.

### Pour développer

Installez Node.js, puis, dans le dossier du projet :

```sh
npm start
```

Ouvrez ensuite **http://localhost:4173**.

Aucune dépendance à installer pour faire fonctionner le site.

```sh
npm test       # Vérifications automatisées
npm run build  # Génération de outputs/Linea.html
```

## Créer une frise

1. Choisissez un style sur l’accueil et cliquez sur **Créer une frise**.
2. Saisissez le titre et la description.
3. Ajoutez une date ponctuelle ou une période avec son nom, son emoji et sa couleur.
4. Ajoutez une description et, si vous le souhaitez, des images.
5. Cliquez sur l’événement pour consulter ou modifier ses détails.
6. Choisissez l’orientation, puis exportez ou partagez votre création.

Les années négatives représentent les dates avant J.-C. L’année 0 est refusée. Un jour nécessite un mois et les dates du calendrier sont vérifiées.

## Importer, partager et exporter

- **`.linea` / `.json`** : projet modifiable, réimportable dans l’éditeur.
- **HTML interactif** : copie autonome en lecture seule, avec descriptions et images incorporées. Peut être importée dans l’éditeur pour créer une copie modifiable.
- **Lien de partage** : ouvre directement une copie en lecture seule, lorsque l’application est hébergée. Les modifications futures ne changent pas cette copie.
- **PNG / JPG** : image de la frise, avec les détails complets à l’export.
- **SVG** : image vectorielle.
- **PDF** : document paginé constitué d’images ; son texte n’est pas sélectionnable.
- **Imprimer** : préparation des pages puis ouverture de la boîte d’impression du navigateur.

Les exports imprimables utilisent un fond clair. Les préférences de couleurs et de mode sombre concernent l’appareil utilisé.

## Données et limites

Les frises sont stockées localement dans le navigateur. Exportez régulièrement un fichier `.linea` pour conserver une sauvegarde indépendante. Il n’y a pas de synchronisation entre appareils.

- Jusqu’à 500 événements par frise et 8 images par événement.
- Images source de moins de 20 Mo, réduites à 1400 px maximum et incorporées en JPEG.
- Imports limités à 20 Mo ; PDF limités à 200 pages.
- Les images distantes doivent autoriser leur téléchargement par le navigateur pour être incluses dans les exports. Sinon, ajoutez-les depuis votre appareil.
- Les fichiers HTML importés sont lus comme des données : leurs scripts ne sont pas exécutés.
- Le partage en lecture seule est un mode de consultation, pas un contrôle d’accès.

## Fichiers à transférer

```text
index.html        Structure de l’application
style.css         Interface, thèmes et adaptation mobile
core.js           Dates, validation, import et formats de fichiers
scene.js          Rendus des quatre styles de frise
app.js            Éditeur, sauvegarde, partage et exports
server.cjs        Serveur local de développement
build.cjs         Construction du fichier autonome
package.json      Commandes du projet
tests/            Tests et vérifications complémentaires
Linea.html        Application autonome
README.md         Documentation
```

## Vérifications de la version développée

La version cloud a passé **23 tests automatisés** et **40 exports de contrôle** sur les quatre styles et les deux orientations. Les tests couvrent les dates, périodes, interactions dans un DOM simulé, stockage, import, partage, emojis, apparence et structure PDF.

Le contrôle complémentaire des exports utilise `sharp`, `@napi-rs/canvas` et `pdf-lib`, uniquement pour les tests :

```sh
node tests/export-smoke.cjs <dossier-node_modules-contenant-ces-bibliothèques>
```

Les rendus ont été inspectés. Les interactions dans un navigateur réel et la boîte d’impression restent à vérifier : Chromium n’a pas pu être installé dans l’environnement de test.

## Hébergement

Après le transfert du code, le site pourra être hébergé sur un service statique, par exemple GitHub Pages, avec `index.html`, `style.css`, `core.js`, `scene.js` et `app.js`. Le fichier autonome peut aussi être hébergé seul. L’hébergement n’est pas encore configuré dans ce dépôt.
