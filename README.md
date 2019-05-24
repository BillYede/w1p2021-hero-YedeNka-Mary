# Le site dont vous êtes le héros

URL du site : https://amazing-bill.netlify.com/

### Groupe

- Bill Wilson Yede Nka
- Alexandre Mary


| Type  | Objectif | Fait ? | 
| ----- | -------- | ------ |
| Setup | Le repository respecte la nomenclature `w1p2021-hero-amsellem-calou`, avec tous les noms des membres, et les membres sont cités dans le README.md | OUI |
| Setup | Le site est en ligne, et l'URL est citée dans le README.md | OUI |
| Setup | Le site utilise VueJS | OUI |
| Setup | Cloner le repository et exécuter `npm install` puis `npm run dev` s'effectue sans encombre | OUI |
| Données | Un schéma numérique ou papier (scanné ou photographié) décrivant les différentes étapes et enchaînements possible. Affiché dans ce readme (si plusieurs images sont nécessaires, en afficher plusieurs, mais essayer d'être synthétique). | OUI |
| Données | Un fichier `data.json` est utilisé pour stocker la structure du jeu | OUI |
| Données | Le fichier `data.json` décrit 30 phases de jeu ou plus. Indiquez *En partie* s'il en décrit plus de 15. | OUI |
| Pages | Une page d'accueil est présente | OUI |
| Pages | Une page de choix du personnage est présente | OUI |
| Pages | Une page de victoire est présente | OUI |
| Pages | Une page d'échec est présente | OUI |
| Routing | Une route dont l'`id` varie permet d'afficher les différentes étapes du jeu | OUI |
| Routing | Lorsqu'on recharge la page (`Ctrl + R`), on se trouve toujours à la même étape | OUI |
| Transitions | Chaque page apparaît grâce à une transition fluide (la complexité de la transition n'est pas prise en compte ici) | OUI |
| Transitions | Les transitions internes au jeu (d'une étape à une autre) et externes (intro, fin...) sont différentes | OUI |
| État | Le choix du personnage et/ou de ses caractéristiques impacte l'aventure au moins une fois. **Indiquez ici comment succintement.** | Lors du début de l'aventure le joueur a le droit de choisir une boussole ou une épée.
En fonction du choix effectué il pourra par exemple avec l'épée battre un adversaire et passez à une étape qui ne lui aurait pas été accessible sans.|
| État | Une décision ou un événement aléatoire survenu pendant l'aventure a un impact sur la suite, au moins une fois. **Indiquez ici comment succintement.** | - |
| État | Le choix du personnage et/ou ce qu'il s'est passé pendant l'aventure impactent l'écran de fin. **Indiquez ici comment succintement.** | Le nombre de changements de pages effectués par l'intermédiaire de cliques sur les différents boutons est affiché sur l'écran de fin. |
| État | Au moins un service (classe de type `GameService`) est utilisé | OUI |
| Sauvegarde | Lorsqu'on recharge la page (`Ctrl + R`), le personnage, ses caractéristiques, les choix du joueur et tout le reste sont rétablis | OUI |
| Sauvegarde | Lorsqu'on quitte le jeu et qu'on revient plus tard à la page d'accueil (sur le même navigateur), il est possible de reprendre l'aventure où on l'avait laissée | OUI |
| Multimédia | L'expérience présente une vidéo ou plus | OUI |
| Multimédia | L'expérience présente un audio ou plus | OUI |
| Multimédia | L'utilisateur a la possibilité de couper le son à tout moment | - |


## Prologue

- Voici le cahier des charges que doit respecter **au minimum** le projet.
- Tout ce qui n'est pas précisé relève de vos choix personnels.

### Git

1. Forkez ce repository et renommez-le selon la nommenclature `w1p2021-hero-amsellem-calou`, en remplaçant les noms par les vôtres.
2. Utilisez [netlify](https://www.netlify.com/) ou le service de votre choix pour mettre votre projet en ligne.
3. Remplacez la fausse URL en haut de ce fichier par l'URL de votre projet.
4. Renseignez les membres de votre groupe en haut du fichier.

### Environnement technique

Le projet doit être construit avec le framework [VueJS](https://vuejs.org/).

### Lancer le projet

Se mettre dans un terminal dans le répertoire du projet forké, puis :
* `npm i`
* `npm run dev`

#### Plugins conseillés

- [Vue.js devtools pour Chrome, inspecteur vue](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
- [Vue.js devtools pour Firefox, inspecteur vue](https://addons.mozilla.org/fr/firefox/addon/vue-js-devtools/)
- [Plugin vue pour VSCode, coloration syntaxique](https://marketplace.visualstudio.com/items?itemName=octref.vetur)
- [Plugin eslint pour VSCode, validation de code](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

### Structure des données

Le projet doit contenir un fichier `data.json` contenant l'intégralité des données nécessaires à la génération du jeu.

#### Données de test

Avant d'écrire votre histoire, commencez par un jeu de données de test constitué ainsi :

| phase n° | titre             | action A                 | action B             | Fin ?    |
| -------- | ----------------- | ------------------------ | -------------------- | -------- |
| 1        | Bienvenue !       | avancer (-> vers 2)      |                      |
| 2        | Ou aller ?        | à gauche (-> vers 3)     | à droite (-> vers 4) |
| 3        | Chemin tranquille | avancer (-> vers 5)      |                      |
| 4        | Chemin dangereux  | revenir (-> vers 2)      | avancer (-> vers 6)  |
| 5        | Arrivée           | continuer (vers `/win`)  |                      | Victoire |
| 6        | Piège mortel      | continuer (vers `/lose`) |                      | Échec    |

- À vous de trouver comment représenter ces données sous forme d'un `json` exploitable par votre JavaScript.
- Par la suite, vous écrirez une histoire complète constituée d'au moins **30 phases**.
- Les chemins peuvent s'entremêler, et les victoires et les échecs peuvent être multiples.
- Chaque phase pourra offrir un ou plusieurs choix (sans se limiter à deux).
- Votre `json` s'enrichira de nouvelles informations pour chaque phase (texte(s), image(s)...).

## Semaine 1 : Routing & transitions

### Routes

Le projet doit contenir les pages suivantes :

| url          | description                 | paramètres                   | destination                      |
| ------------ | --------------------------- | ---------------------------- | -------------------------------- |
| `/`          | Page d'accueil              |                              | `/character`                     |
| `/character` | Page de choix du personnage |                              | `/game/1`                        |
| `/game/:id`  | Pages de l'aventure         | id : identifiant de la phase | `/game/:id` ou `/win` ou `/lose` |
| `/win`       | Page de victoire            |                              | `/`                              |
| `/lose`      | Page d'échec                |                              | `/`                              |

- Commencez par créer des pages constituées d'un simple texte de test. Elles se construiront par la suite.
- Lorsque l'utilisateur recharge le navigateur, la page courante doit être restaurée correctement. Si je suis sur `game/3` et que je rafraîchi, je suis toujours sur `game/3`.

#### La page /character

Vide pour l'instant, sa logique sera approfondie au cours des semaines suivantes.

#### La page /game/:id

- Chaque phase est un `object` identifié par un `id` dans le fichier `data.json`.
- Lorsque la page est affichée, elle doit charger la phase de jeu correspondante.
- Au début, affichez seulement l'`object` brut. Le contenu des pages sera mis en place plus tard.

### Transitions

- Le passage d'une page à l'autre doit être fluide pour l'utilisateur.
- Utilisez les transitions et les animations de votre choix pour parvenir à cet effet.
- Les transitions ne seront pas toutes identiques.

Voici un exemple de trame :

- _Loader_ <sub><sup>(3 secondes fixes pour l'instant, logique à implémenter par la suite)</sup></sub>
- _Transition d'ouverture_
  - Page d'accueil
- _Transition_
  - Page de sélection du personnage
- _Transition du hors-jeu vers le jeu_ <sub><sup>(ex: passage par un écran noir, comme un jeu vidéo - soyez inventifs !)</sup></sub>
  - Phase 1
- _Transition de phase_
  - Phase 2
- _Transition de phase_
  - Phase 3
- _Transition du jeu vers le hors-jeu_
  - Page de victoire ou d'échec

## Semaine 2 : À venir

Proposez vos idées de fonctionnalités pour la semaine 2 et votez pour celles des autres [sur ce sondage collaboratif](https://poll.ly/#/Pw7KgAnK).
