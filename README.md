# 🚀 SPACE GOOSE : L'Odyssée de Neptune

Un jeu de plateau spatial tactique et dynamique jouable dans le navigateur, réinventant le traditionnel **Jeu de l'Oie** avec des mécaniques de cartes façon *Mille Bornes* et une mise en scène inspirée de *Mario Party*. 

---

## 🌌 Synopsis & Objectif

De **2 à 4 pilotes** s'élancent depuis le **Soleil (Case 1)** dans une course effrénée à travers le système solaire. L'objectif est d'être le premier vaisseau à atterrir **exactement sur Neptune (Case 63)**, au cœur de la spirale galactique.

---

## 🎮 Déroulement d'un Tour (Core Loop)

Le jeu se joue en multijoueur local (*Hotseat* sur le même écran). À chaque tour, le pilote actif dispose de deux phases :

1. **Phase Tactique (Optionnelle) :** Le joueur peut sélectionner **une seule Carte Action** dans son inventaire (panneau de droite). La carte passe alors en état *"Primed"* (surlignée en doré) et son effet s'appliquera automatiquement au moment du lancer. Cliquer à nouveau sur la carte annule sa sélection.
2. **Phase de Propulsion :** Le joueur clique sur **« Lancer les Dés »** (panneau de gauche). 
   * Par défaut, le vaisseau lance **2 dés à 6 faces (2D6)**.
   * La carte préparée (s'il y en a une) est consommée et modifie le lancer ou déclenche son effet spécial.
   * Le vaisseau avance case par case en décomptant ses points de mouvement, puis déclenche l'événement de la case d'arrivée.

### ⚠️ Règle d'Approche Finale (Le Rebonds)
Pour conquérir **Neptune (Case 63)**, la précision est absolue. Si le score de vos dés dépasse le nombre de cases restantes, votre vaisseau rebondit sur le champ gravitationnel de Neptune et **recule du nombre de cases excédentaires**.

---

## 🪐 Les Cases Spéciales du Plateau

Les cases standards restent assombries et ne s'illuminent en dégradé (du rouge solaire au rose nébuleux) que lorsqu'un vaisseau s'y arrête. Les cases spéciales, elles, émettent un signal permanent :

| Case(s) | Icône | Nom | Effet (Trigger) |
| :--- | :---: | :--- | :--- |
| **Case 1** | ☀️ | **Le Soleil** | Point de départ de la course (*Player Start*). |
| **Case 6** | 🌉 | **Portail Spatial** | Téléportation immédiate vers la **Case 12**. |
| **9, 18, 27, 36, 45, 54** | 🌀 | **Trous de Ver** | *(Les Oies)* Propulse le vaisseau en doublant le score du lancer de dés. |
| **Case 19** | 🛰️ | **Station Spatiale** | Arrêt de maintenance obligatoire : le pilote **passe 1 tour**. |
| **Case 31 & 52** | 🕳️ / 👽 | **Trou Noir & Prison Alien** | Piège gravitationnel : le vaisseau est **bloqué pendant 3 tours**. *(Un joueur est libéré plus tôt si un autre vaisseau atterrit sur la case et prend sa place, ou via une carte dédiée).* |
| **Case 42** | 🌫️ | **Nébuleuse Dense** | Panne de capteurs : le vaisseau dérive en arrière jusqu'à la **Case 30**. |
| **Case 58** | 💥 | **Supernova** | Explosion critique : le vaisseau est renvoyé tout au début, sur le **Soleil (Case 1)**. |
| **Cases `[?]`** | ❓ | **Balise Mystère** | Permet de piocher aléatoirement une **Carte Tactique** (limite de 4 cartes en main). |
| **Case 63** | 🔱 | **Neptune** | Ligne d'arrivée. Atterrir pile dessus déclenche la victoire immédiate ! |

---

## 🃏 L'Arsenal : Les Cartes Tactiques

En s'arrêtant sur une case `[?]`, le pilote ajoute une carte à son inventaire. Les cartes sont classées par rareté et permettent de manipuler le hasard ou de saboter ses adversaires :

* ⚪ **Dé de Précision** *(Commune)* : Remplace les deux dés par **un seul mini-dé (1 à 3)**. L'outil ultime en fin de partie pour éviter de dépasser Neptune.
* ⚪ **Propulseur +3** *(Commune)* : Ajoute un bonus fixe de **+3** au résultat du lancer de dés.
* 🔵 **Double Propulseur** *(Rare)* : Multiplie le score total des dés par **2**.
* 🔵 **Sortie de Trou** *(Rare)* : Permet de s'échapper instantanément d'un **Trou Noir (31)** ou de la **Prison Alien (52)** et de jouer son tour normalement.
* 🔵 **Bouclier Déflecteur** *(Rare)* : Active une barrière énergétique pour le tour en cours. Si le vaisseau atterrit sur un piège (Station, Trou Noir, Nébuleuse, Supernova), **l'effet négatif est totalement annulé**.
* 🟣 **Onde IEM** *(Épique)* : En plus de votre lancer normal, envoie une impulsion électromagnétique sur le joueur actuellement en **1ère position**, le faisant reculer de **4 cases**.
* 🟡 **Surcharge Hyperdrive** *(Légendaire)* : Pousse les moteurs au maximum en lançant **3 dés (ou Dé x3)** pour une traversée fulgurante de la galaxie.

---

## 🛠️ Fonctionnalités & Architecture Technique

* **Zéro Dépendance Externe :** L'intégralité du jeu (rendu, logique, audio) tient dans un seul fichier `index.html` autonome.
* **Génération Mathématique :** Le plateau est généré dynamiquement via une **spirale d'Archimède** calculée en JavaScript, doublée d'un tracé SVG en pointillés reliant les constellations.
* **Orientation Vectorielle (LookAt Rotation) :** Les vaisseaux (rendus en SVG dynamique) calculent automatiquement l'angle trigonométrique vers la case suivante (`Math.atan2`) pour toujours pointer dans le sens de la marche.
* **Synthétiseur Audio Procédural (Web Audio API) :** Tous les bruitages (rebonds chromatiques case par case, alertes de pièges, fanfare de victoire, distorsion de trou de ver) sont générés en temps réel par des oscillateurs mathématiques, sans aucun fichier MP3 externe.
* **Game Juice & VFX :** Système de particules moteur au déplacement, *Floating Texts* animés sur les événements et *Camera Shake* lors des catastrophes spatiales.

---

## 🚀 Installation & Lancement

1. Téléchargez ou copiez le fichier `index.html`.
2. Double-cliquez dessus pour l'ouvrir dans n'importe quel navigateur web moderne (Chrome, Firefox, Edge, Safari).
3. Choisissez le nombre de pilotes (2 à 4) et lancez la partie !
