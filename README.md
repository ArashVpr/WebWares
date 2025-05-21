![screencapture-localhost-8080-2025-05-21-15_51_36](https://github.com/user-attachments/assets/e4425f0a-e0de-4e54-ba6f-5050581ae6a1)
![screencapture-localhost-8080-categorie-4-2025-05-21-15_53_02](https://github.com/user-attachments/assets/a4cc9956-20b3-44c0-a003-3cfef6b5a32b)
![screencapture-localhost-8080-produit-2025-05-21-15_51_59](https://github.com/user-attachments/assets/2b13875a-1bb1-4a23-8956-1338eb6ab85b)
![screencapture-localhost-8080-product-details-4-2025-05-21-15_52_33](https://github.com/user-attachments/assets/41b76edf-4a23-4d95-ba12-f98532d82f41)

---

Voici la version française professionnelle de ton fichier `README.md` pour **WebWares** :

---

# 📦 Documentation WebWares

Une application web moderne développée avec Vue.js pour la gestion des produits, des utilisateurs et des commandes.

---

## 📚 Table des matières

1. [Introduction](#1-introduction)
2. [Fonctionnalités](#2-fonctionnalités)
3. [Installation du projet](#3-installation-du-projet)
4. [Structure des dossiers](#4-structure-des-dossiers)
5. [Composants et vues clés](#5-composants-et-vues-clés)
6. [Gestion d’état (Vuex)](#6-gestion-détat-vuex)
7. [Routage](#7-routage)
8. [Stylisation](#8-stylisation)
9. [API et gestion des données](#9-api-et-gestion-des-données)
10. [Déploiement](#10-déploiement)
11. [Contribuer](#11-contribuer)
12. [Licence](#12-licence)

---

## 1. 🚀 Introduction

**WebWares** est une application modulaire et responsive développée avec Vue 3, permettant la gestion des utilisateurs, des produits et des commandes. Elle comprend des opérations CRUD complètes, l’authentification des utilisateurs, ainsi qu’un tableau de bord administrateur.

Technologies principales :

* **Vue 3**
* **Vuex** pour la gestion d’état
* **Vue Router** pour la navigation

---

## 2. ✨ Fonctionnalités

* **Gestion des utilisateurs**

  * Inscription, connexion, modification de profil
  * Rôles : Administrateur / Utilisateur

* **Gestion des produits**

  * Ajouter, modifier, supprimer et afficher des produits

* **Gestion des commandes**

  * Ajouter au panier, valider et gérer les commandes

* **Tableau de bord admin**

  * Gestion des utilisateurs, produits et catégories

* **Design responsive**

  * Compatible mobile avec un en-tête dédié

* **Intégration du stockage local**

  * Persistance des données utilisateur et commande

---

## 3. 🛠 Installation du projet

### Prérequis

* Node.js (v14+)
* npm ou yarn

### Installation

```bash
git clone https://github.com/ton-utilisateur/webwares.git
cd webwares
npm install
```

### Lancer le serveur de développement

```bash
npm run serve
```

### Compiler pour la production

```bash
npm run build
```

### Linter le code

```bash
npm run lint
```

---

## 4. 📁 Structure des dossiers

```
src/
├── assets/
├── components/
├── router/
├── store/
├── views/
└── App.vue
```

---

## 5. 🧩 Composants et vues clés

### Composants

* `HeaderComponent.vue` – Barre de navigation principale
* `FooterComponent.vue` – Pied de page présent partout
* `HeroComponent.vue` – Section d’accueil
* `ModalComponent.vue` – Boîte de dialogue réutilisable
* `ButtonComponent.vue` – Boutons réutilisables
* `NosAvantageComponent.vue` – Mise en avant des avantages

### Vues

* `LoginPage.vue` – Connexion
* `RegistrationPage.vue` – Inscription
* `PolitiqueConfidentialite.vue` – Politique de confidentialité
* `BackProduit.vue` – Gestion des produits (admin)
* `BackUser.vue` – Gestion des utilisateurs (admin)
* `ConfirmCommande.vue` – Confirmation de commande
* `DetailProduit.vue` – Détails produit
* `PanierProduit.vue` – Panier

---

## 6. 🔄 Gestion d’état (Vuex)

### State

```js
currentUtilisateur
produits
categories
commandes
```

### Mutations

```js
addUser
updateUtilisateur
incrementQuantite
decrementQuantite
```

### Actions

```js
registerUser
addProduitToPanier
loadCurrentUtilisateurFromLocalStorage
```

### Getters

```js
isLoggedIn
isAdmin
total
```

---

## 7. 🧭 Routage

L’application utilise **Vue Router**. Les routes sont définies dans `router/index.js`.

### Routes principales

| Chemin               | Page                    |
| -------------------- | ----------------------- |
| `/login`             | Page de connexion       |
| `/register`          | Page d'inscription      |
| `/modif-produit/:id` | Modifier un produit     |
| `/modif-user/:id`    | Modifier un utilisateur |
| `/resume-commande`   | Résumé de commande      |

---

## 8. 🎨 Stylisation

* CSS scoped pour les composants
* Variables globales définies via `:root` dans `App.vue`

---

## 9. 📦 API et gestion des données

Actuellement, l’application ne consomme pas d’API externe.

* Les données sont gérées localement avec **Vuex**
* Persistées via **localStorage**

### Clés du stockage local

* `currentUtilisateur`
* `commandes`
* `savedCommandes`

---

## 10. 🚚 Déploiement

1. Compiler le projet :

   ```bash
   npm run build
   ```

2. Copier le contenu du dossier `dist/` vers le répertoire public de votre serveur.

---

## 11. 🤝 Contribuer

Nous accueillons les contributions avec plaisir !

1. Forker ce dépôt
2. Créer une branche (`git checkout -b feature/ma-fonctionnalité`)
3. Commiter vos modifications (`git commit -m 'Ajout d'une fonctionnalité'`)
4. Pousser votre branche (`git push origin feature/ma-fonctionnalité`)
5. Créer une Pull Request

---

## 12. 📄 Licence

Ce projet est sous licence **MIT**.
Consultez le fichier [LICENSE](./LICENSE) pour plus de détails.

---


