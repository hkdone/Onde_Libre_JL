# Note de cadrage — Projet « Onde Libre Studio »

**Destinataire :** Camille Vasseur, Fondatrice-Productrice d'Onde Libre Studio  
**Objet :** Présentation de votre future application tout-en-un de pilotage du studio (Jalon 1)  
**Date :** Novembre 2026

---

## 1. Pourquoi ce projet et quel problème il résout

Aujourd'hui, votre équipe de 11 personnes jongle entre plusieurs outils qui ne se parlent pas : un outil pour planifier les enregistrements, un autre pour suivre les invités, un service pour publier les épisodes et un dernier pour suivre les campagnes de vos sponsors. Résultat : des informations recopiées à la main, des fiches parfois contradictoires, des intégrations fragiles et aucun tableau de bord clair pour savoir immédiatement où en est chaque épisode.

Avec **trois nouveaux podcasts en préparation pour la rentrée**, l'objectif est clair : **repartir sur une base propre et unique**, conçue sur mesure pour votre façon de travailler, que votre équipe pourra utiliser et faire évoluer en toute autonomie après mon intervention.

---

## 2. Ce que fera votre application (Version 1)

L'application réunira en un seul endroit les **trois grandes familles** de votre quotidien, autour du parcours d'un épisode :

1. **Le pilotage des épisodes (le cœur de l'outil)**
   - Chaque épisode appartient à une émission (podcast original ou podcast de marque) et suit **5 étapes claires et uniques** :
     **Idée** → **Invité confirmé** → **Enregistré** → **Monté** → **Publié**.
   - Des repères visuels simples (texte + icône + couleur) permettent à toute l'équipe de voir immédiatement ce qui avance et ce qui bloque.
2. **Le carnet d'invités centralisé**
   - Une fiche unique par invité : qui il est, comment l'équipe l'a contacté et la liste de tous les épisodes auxquels il a déjà participé. Fini les doublons ou les invités confirmés dans un agenda mais introuvables en production.
3. **La diffusion, l'audience et le suivi des sponsors**
   - Suivi des publications multi-plateformes et **récupération automatique de données externes** (diffusion ou audience) sans ressaisie manuelle.
   - Si le service externe rencontre une panne temporaire, l'application continue de fonctionner normalement en affichant les dernières données connues avec un message clair.
   - Enregistrement dès maintenant des **campagnes sponsors** rattachées aux épisodes diffusés, pour préparer sereinement votre futur espace partenaires.

### Ce qui reste volontairement en dehors de cette première version
Pour livrer un outil fiable et prêt pour la rentrée sans disperser les efforts, la version 1 ne couvre pas : l'accès direct des sponsors externes à un portail dédié, le montage/stockage des fichiers audio lourds, ni la facturation comptable. La base est toutefois déjà prête pour accueillir un espace partenaires dans une phase ultérieure.

---

## 3. Qui a accès à quoi ? (Sécurité & confidentialité)

Chacun des 11 collaborateurs se connecte avec **son propre compte**. Les droits sont automatiquement adaptés au rôle de la personne, directement dans la base de données :

| Rôle dans le studio | Ce qu'il peut voir et faire | Ce qui reste protégé |
|---|---|---|
| **Équipe Production** *(éditorial & réalisation)* | Gérer les émissions, faire avancer les épisodes de *Idée* à *Monté*, gérer les fiches invités et les enregistrements. | Ne voit pas les données financières et contractuelles des campagnes sponsors. |
| **Équipe Diffusion** *(publication & audience)* | Consulter les épisodes prêts à publier, gérer les sorties multi-plateformes, passer un épisode en *Publié* et consulter/actualiser les données d'audience. | N'accède ni aux campagnes sponsors réservées à la direction, ni aux coordonnées privées des invités non nécessaires à la publication. |
| **Direction** *(Camille Vasseur)* | **Vue de pilotage globale** : tous les épisodes en cours, à venir et publiés, les blocages éventuels, les indicateurs d'audience et la gestion complète des campagnes sponsors. | Accès complet et exclusif aux données sensibles du studio. |

---

## 4. Comment nous avançons ensemble (6 étapes, 3 points d'étape)

Pour éviter les mauvaises surprises et garantir la solidité de l'outil, le projet avance étape par étape :

1. **Étape 1 (📍 Point d'étape 1 — aujourd'hui)** : Cadrage de l'architecture et validation de cette note avec vous, avant toute construction.
2. **Étape 2** : Création de la base de données sécurisée (tables, règles anti-doublons et cloisonnement des accès par rôle).
3. **Étape 3 (📍 Point d'étape 2)** : Maquettes des écrans puis construction de l'application (gestion des épisodes, fiches invités, vue direction).
4. **Étape 4 (📍 Point d'étape 3)** : Activation des comptes utilisateurs et vérification réelle que chaque rôle ne voit que son périmètre.
5. **Étape 5** : Connexion au service externe de diffusion/audience et tests de résistance en cas de panne.
6. **Étape 6** : Mise en ligne définitive, sauvegarde complète du projet et remise des guides.

---

## 5. Votre autonomie après la livraison

Pour que le studio ne soit **plus jamais dépendant d'un prestataire ou d'un outil opaque**, la livraison inclura systématiquement :
- **Un guide d'utilisation par métier** (Production, Diffusion, Direction) expliquant les gestes du quotidien.
- **Des fiches de dépannage simples** (que faire si un nouveau collaborateur n'a pas accès, si la connexion externe ne répond plus, ou si une mise à jour échoue).
- **Une documentation claire de l'outil et de son historique** permettant à un autre intervenant de reprendre ou faire évoluer l'application sans repartir de zéro.
