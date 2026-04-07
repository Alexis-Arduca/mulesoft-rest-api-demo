# mulesoft-users-api

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> 🎓 Projet d'apprentissage - Première prise en main de MuleSoft Anypoint, implémentation d'une API REST de gestion d'utilisateurs.

---

## Contexte

Ce projet a été réalisé en autonomie afin de me former sur **MuleSoft** et les **microservices**.

---

## Outils utilisés

| Outil | Rôle |
|---|---|
| **MuleSoft Anypoint Platform** | Plateforme d'intégration cloud |
| **Anypoint Code Builder (VS Code)** | Extension MuleSoft pour VS Code |
| **OAS 3.0 (YAML)** | Langage de spécification de l'API |
| **Anypoint Exchange** | Marketplace MuleSoft pour publier la spec |
| **Mule Runtime 4.11.2** | Moteur d'exécution Mule |
| **Java 17** | Requis par le runtime Mule |

> ℹ️ **Note sur l'environnement** : Anypoint Studio (l'IDE officiel MuleSoft) a été écarté en raison de contraintes d'installation sur Windows et sur ma machine (chemins trop longs, consommation mémoire élevée). Anypoint Code Builder, l'alternative moderne basée sur VS Code, a été utilisé à la place et est suffisante pour un projet d'apprentissage.

---

## Ce qui est fait

- Création d'un compte Anypoint Platform
- Installation et configuration d'Anypoint Code Builder sur VS Code
- Conception d'une spécification API REST en OAS 3.0 (YAML) avec 4 endpoints
- Publication de la spec sur Anypoint Exchange
- Génération du projet Mule d'implémentation à partir de la spec
- Implémentation des flows Mule en XML (GET /users, GET /users/{id}, POST /users, PATCH /users/{id})
- Gestion des erreurs HTTP propre (400, 404, 405, 415, 501)
- ⚠️ Exécution locale bloquée par un bug connu de Maven sur Windows (fichiers POM corrompus avec BOM UTF-8 incompatible lors du téléchargement des dépendances MuleSoft)

---

## Endpoints de l'API

| Méthode | Endpoint | Description |
|---|---|---|
| GET | `/api/users` | Retourne la liste de tous les utilisateurs |
| GET | `/api/users/{id}` | Retourne un utilisateur par son ID (404 si non trouvé) |
| POST | `/api/users` | Crée un nouvel utilisateur (201) |
| PATCH | `/api/users/{id}` | Met à jour partiellement un utilisateur (404 si non trouvé) |

> 💡 **Pourquoi PATCH et non PUT ?** PATCH est la bonne pratique REST pour une mise à jour partielle. Seuls les champs fournis sont modifiés, les autres restent inchangés. PUT remplacerait l'intégralité de la ressource. C'est ce dont l'on avait rapidement parlé durant notre entretien.

---

## Exemples de réponses

**GET /api/users**
```json
[
  { "id": "1", "name": "Alice Dupont", "email": "alice@example.com" },
  { "id": "2", "name": "Bob Martin", "email": "bob@example.com" },
  { "id": "3", "name": "Charlie Durand", "email": "charlie@example.com" }
]
```

**POST /api/users**
```json
// Body
{ "name": "Nouvel Utilisateur", "email": "nouveau@example.com" }

// Réponse 201
{ "id": "uuid-généré", "name": "Nouvel Utilisateur", "email": "nouveau@example.com", "message": "Utilisateur créé avec succès" }
```

**PATCH /api/users/1**
```json
// Body (seuls les champs à modifier)
{ "email": "alice.nouveau@example.com" }

// Réponse 200
{ "id": "1", "name": "Alice Dupont", "email": "alice.nouveau@example.com", "message": "Utilisateur mis à jour avec succès" }
```

---

## Structure du projet

```
mulesoft-users-api/
├── users-api-learning.yaml     # Spécification OAS 3.0 de l'API
├── exchange.json               # Métadonnées MuleSoft
├── users-api-impl/             # Projet Mule d'implémentation
│   ├── src/
│   │   ├── main/
│   │   │   ├── mule/
│   │   │   │   └── users-api-impl.xml   # Flows Mule (logique métier)
│   │   │   └── resources/
│   │   │       └── log4j2.xml
│   │   └── test/munit/
│   └── pom.xml
└── README.md
```

---

## Ce que j'ai appris

- Architecture et concepts de **MuleSoft Anypoint Platform**
- Conception d'une API avec **OAS 3.0 (YAML)**
- Publication d'un asset sur **Anypoint Exchange**
- Structure et logique des **flows Mule en XML**
- Transformation de données avec **DataWeave 2.0**
- Bonne pratique REST : **PATCH vs PUT** pour les mises à jour partielles
- Gestion des erreurs HTTP (400, 404, 405, 415, 501) dans un contexte MuleSoft

---

## Prochaines étapes

- [ ] Tests MUnit (tests unitaires MuleSoft)
- [ ] Déploiement sur CloudHub
- [ ] Connexion à une vraie base de données

---

## Licence

Ce projet est sous licence **MIT** - voir le fichier [LICENSE](LICENSE) pour plus de détails.

---

## Auteur

**Alexis Arduca** - Étudiant 5ème année Epitech Montpellier  
[alexis.arduca@epitech.eu](mailto:alexis.arduca@epitech.eu)