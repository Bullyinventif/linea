# Linea — contexte complet de reprise

## Décision actuelle et périmètre

Eliott veut recommencer son application de frises chronologiques avec une interface plus simple. **Repartir de zéro pour le code en conservant les besoins**, ignorer les anciennes versions. Ne pas récupérer, reconstruire ou continuer leurs fichiers sans nouvelle demande. Ne pas recommencer le transfert de l’ancien code sur GitHub.

La première étape demandée est de proposer plusieurs styles de site dans des maquettes interactives directement dans ChatGPT, via Visualize / app_block si ces capacités sont réellement disponibles. Eliott souhaite comparer sans télécharger. Attendre son choix avant de coder l’application complète. Une reprise progressive et validée visuellement est préférable.

Ce document conserve le contexte du projet et des blocages, pas le code ni une transcription mot à mot de la conversation.

## Objectif du produit

Créer facilement des frises chronologiques en français ; ajouter des dates, des périodes, des descriptions et des images ; consulter, partager et imprimer. L’aspect souhaité est très clair, arrondi, soigné et inspiré d’Apple. Les dates doivent se remarquer et être immédiatement compréhensibles.

## Besoins fonctionnels conservés

- Créer une frise avec titre et description ; ouvrir un fichier pour continuer une frise.
- Ajouter, modifier et supprimer des événements.
- Chaque événement : année obligatoire ; mois facultatif ; jour facultatif nécessitant un mois ; nom ; description facultative.
- Choisir l’emoji ou l’icône du repère. Accepter un emoji personnel, y compris les emojis composés.
- Ajouter des images par upload ou lien.
- Cliquer sur une date ou un événement pour consulter description et images.
- Ajouter des périodes avec début et fin : 1918–1920, février–octobre de la même année, ou dates plus précises.
- Passer entre horizontal et vertical.
- Choisir le style de chaque frise et éventuellement le style par défaut des futures frises.
- Mode sombre et thèmes de couleurs de l’application.
- Présentation compacte. « Plus compressible » a été interprété comme « compact », sans confirmation explicite.
- Sauvegarde modifiable sous forme de fichier, importable ensuite.
- Partage d’un fichier interactif qui s’ouvre directement en lecture seule.
- Partage par lien qui ouvre la frise directement en lecture seule sur un site hébergé.
- Export PNG, JPG, PDF, et impression facile.
- Tester les fonctions et corriger les bugs rencontrés. Distinguer clairement tests automatiques, inspection visuelle et tests dans un vrai navigateur.

Les données, comptes et synchronisation ne sont pas définis pour la nouvelle version. Ne pas ajouter automatiquement Firebase ou un système de comptes.

## Parcours et simplicité

### Accueil

Deux actions principales : **Créer une frise** et **Ouvrir un fichier**.

Fond demandé : quadrillage blanc, légèrement brillant, avec un mouvement subtil évoquant un tissu. Garder l’animation discrète et respecter la réduction des animations.

### Éditeur

La frise occupe la place centrale. Un bouton évident permet d’ajouter un événement. Les détails et les réglages peuvent apparaître dans un panneau ou une fenêtre. Apparence, partage et export restent accessibles dans des menus secondaires.

Cette organisation est une proposition, pas une maquette déjà validée. Éviter de montrer toutes les possibilités simultanément.

### Consultation partagée

Ouvrir directement la frise. Les événements restent consultables ; masquer les commandes de modification. La lecture seule est un mode de consultation, pas une protection d’accès.

## Styles de frise envisagés

Les styles des frises sont distincts des styles de l’interface du site.

1. **Épuré** : ligne simple, points et cartes arrondies.
2. **Chronologie en bande/bloc** : dates écrites à l’intérieur. Une date ponctuelle se marque par un trait vertical ; une période par un trait ou rectangle horizontal reliant début et fin. Le premier essai a été jugé confus. Éviter les répétitions, rendre les extrémités évidentes et garder les titres lisibles.
3. **Aventure** : carte originale inspirée de la sélection de mondes de Mario Bros ; chemin entre des îlots. Ce n’est pas une carte de niveau jouable.
4. **Liste claire** : proposition ajoutée pour avoir le style le plus simple. Une carte par événement, ordre chronologique, dates en gros et périodes écrites avec début et fin explicites. À réévaluer pour la nouvelle version ; aucune implémentation ancienne n’est imposée.

L’utilisateur avait mentionné une image de référence « img_1 », mais son contenu n’était pas disponible. Ne pas prétendre l’avoir vue ou reproduite.

## Directions proposées pour l’interface du nouveau site

Ces trois pistes ont seulement été décrites. Elles n’ont pas été choisies par Eliott ni présentées dans de vraies maquettes.

| Direction | Apparence | Organisation proposée |
| --- | --- | --- |
| Apple minimal | Blanc, bleu doux, cartes arrondies, boutons sobres | Frise centrale, bouton « + Événement », panneau de modification. |
| Carnet d’histoire | Fond quadrillé, crème et pastels | Dates très visibles, événements comme des notes, périodes en bandes. |
| Studio créatif | Blanc, violet, grandes icônes, touches ludiques | Création guidée : date, nom, puis détails. |

La recommandation de l’assistant était Apple minimal avec un quadrillage discret de Carnet d’histoire. Ce n’est pas un choix de l’utilisateur.

Pour les maquettes, montrer les mêmes exemples d’accueil et d’éditeur dans chaque direction, avec un événement ponctuel et une période. Proposer des variantes réellement différentes tout en gardant une interface simple.

## Contraintes et choix à préciser lors du développement

- La précédente app utilisait HTML/CSS/JavaScript sans framework ; ce n’est pas une contrainte définitive.
- Définir le format modifiable, la sauvegarde et le comportement hors ligne.
- Un lien partagé doit pointer vers une application accessible au destinataire ; un chemin local ne suffit pas.
- Décider si les distances sur la frise représentent les durées ou seulement l’ordre. L’ancien code utilisait un espacement régulier, donc non proportionnel.
- Valider le calendrier, les périodes inversées et les précisions différentes entre début et fin.
- Les années avant J.-C. étaient acceptées dans l’ancienne app ; l’année 0 était refusée. Leur maintien reste à décider.
- Vérifier mobile, textes longs, périodes superposées, images et impression.
- Les images par lien peuvent être consultables mais non exportables selon les autorisations du site distant.
- Le mode sombre de l’ancienne version concernait l’appareil ; les exports imprimables étaient clairs. À décider pour la nouvelle.
- Ne pas imposer les anciennes limites techniques : 500 événements, 8 images, import 20 Mo, JPEG 1400 px et PDF 200 pages étaient des choix de l’ancien code.

## GitHub et état des écritures

Compte : **Bullyinventif**.
Dépôt fourni et autorisé : **https://github.com/Bullyinventif/linea**.
Branche observée : **main**.

Un README décrivant l’ancienne application a été ajouté par l’assistant :
commit 58869e4267594fe6d79ce16624d9117b7d3e3270.

Aucun code d’application n’a été envoyé par l’assistant avant la préparation des présents documents de reprise. Ces deux fichiers de contexte sont de la documentation, pas une nouvelle implémentation.

Vérifier le dépôt avant toute modification : Eliott peut avoir ajouté des fichiers. Réécrire le README autour de la nouvelle version quand son code sera prêt ; ses anciennes mentions de fonctionnalités et de tests ne prouvent pas l’état du futur projet.

Déposer du code dans le dépôt a été autorisé. Une publication du site n’a pas été demandée explicitement ; ne pas confondre dépôt du code et déploiement.

## Historique des fichiers et blocages

La précédente version complète comportait quatre styles, les périodes, les images, les exports, le mode sombre, les couleurs et les emojis libres.

Deux environnements ont alterné :
- Cloud Linux : /workspace/scratch/2ede660c7e57/project ; fichiers Linea.html et Linea-projet.zip dans le dossier parent.
- Windows : C:\Users\eliot\Documents\Codex\2026-10-01\je-veux-cr-er-un-site.

Le dernier ZIP cloud connu faisait 127437 octets, et Linea.html 261504 octets. Ils ont été retrouvés lors d’un accès au cloud, puis cet accès est redevenu indisponible. Leur suppression n’a pas été constatée. Ne pas supposer qu’ils sont accessibles aujourd’hui.

Le chemin /workspace/... est distant et Linux : il ne faut pas y ajouter C: ou AppData. Le dossier Windows souhaité C:\Users\eliot\Desktop\Jeu code\Linea n’a pas reçu de copie confirmée.

Une ancienne version 2 avait été sauvegardée :
- Linea-projet.zip : libfile_f3c1aa9e04608191a3e5cd653789f775 ; version 1 ; fichier file_000000003564820a85ea1dfcbc913e50.
- Linea.html : libfile_e4777a66da548191bbb5b0be08293500 ; version 1 ; fichier file_000000002fdc820a9c67c9ab5ec0e3f8.

Ces sauvegardes sont anciennes, pas la dernière version à quatre styles. Les mises à jour durables de la version récente ont échoué. Les identifiants servent uniquement à comprendre l’historique ; ne pas les récupérer pour la reprise de zéro.

L’utilisateur n’a pas le ZIP sur son PC. Ne pas lui demander cet ancien fichier pour recommencer.

Les erreurs rencontrées incluent « sandbox provisioning failed ». L’assistant a renvoyé plusieurs fois des liens temporaires inaccessibles et proposé une manipulation locale inadaptée. Il a ensuite tenté de reconstruire la version récente depuis la sauvegarde précédente. Cette reconstruction partielle est restée en mémoire et n’a pas été transférée dans GitHub. Eliott a demandé de l’arrêter.

Eliott a signalé un incident sur ChatGPT Status concernant la génération de code et l’accès aux fichiers. Le lien exact avec les erreurs n’a pas été vérifié indépendamment.

Il veut désormais abandonner ces versions et ce processus de récupération, pas reprendre la reconstruction.

## Vérifications passées : ne pas les attribuer au nouveau code

L’ancienne version cloud avait passé 23 tests automatisés et 40 exports de contrôle, avec des interactions simulées et des moteurs de rendu d’images. Aucun test complet dans un vrai navigateur n’avait réussi à être lancé ; Chromium n’avait pas pu être installé.

La reconstruction partielle avait 22 vérifications sur 23 réussies au moment de l’arrêt. L’échec concernait le comptage d’une phrase dans le SVG d’un texte long ; il n’a pas été examiné jusqu’au bout.

Ces résultats ne valident pas la future application. Tester le nouveau code sur ses propres exigences, sans recopier ces chiffres comme preuve.

## Façon de collaborer

Eliott souhaite un ton français clair, motivant et naturel, avec des explications étape par étape utiles. Il s’est agacé des erreurs d’accès, des faux espoirs de téléchargement et du travail supplémentaire consommant ses crédits.

- Avancer par petites étapes.
- Commencer par les maquettes, pas toute l’app.
- Ne pas lancer de grosse récupération ou régénération sans demande.
- Distinguer prévu, codé, testé, sauvegardé et publié.
- Ne jamais annoncer qu’un fichier est sur son PC, Drive ou GitHub sans réussite confirmée.
- Si un outil est absent ou bloqué, expliquer brièvement et proposer une alternative réaliste.
- Éviter les demandes de confirmation inutiles.
- Ne pas introduire Bubble Inc. : Linea n’a pas été demandé comme partie de cet univers.
