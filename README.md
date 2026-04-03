# mulesoft-users-api

> 🎓 Projet d'apprentissage. Première prise en main de MuleSoft Anypoint, implémentation d'une API REST de gestion d'utilisateurs.

---

## Contexte

Ce projet a été réalisé en autonomie afin de me former sur **MuleSoft** et les **microservices**

---

## Outils utilisés

|               Outil                 |                    Rôle                   |
|-------------------------------------|-------------------------------------------|
| **MuleSoft Anypoint Platform**      | Plateforme d'intégration cloud            |
| **Anypoint Code Builder (VS Code)** | Extension MuleSoft pour VS Code           |
| **OAS 3.0 (YAML)**                  | Langage de spécification de l'API         |
| **Anypoint Exchange**               | Marketplace MuleSoft pour publier la spec |
| **Mule Runtime 4.11.2**             | Moteur d'exécution Mule                   |
| **Java 17**                         | Requis par le runtime Mule                |
|-------------------------------------|-------------------------------------------|

Information: Anypoint Studio (l'IDE officiel MuleSoft) a été écarté en raison de contraintes d'installation sur Windows et sur ma machine (chemins trop longs, consommation mémoire élevée). Anypoint Code Builder, l'alternative moderne basée sur VS Code, a été utilisé à la place et est suffisante pour un projet d'apprentissage.

---

## Ce qui est fait

- Création d'un compte Anypoint Platform
- Installation d'Anypoint Code Builder sur VS Code
- Conception d'une spécification API REST en OAS 3.0 (YAML) avec 3 endpoints
- Publication de la spec sur Anypoint Exchange
- Génération du projet Mule d'implémentation à partir de la spec

---

## Endpoints de l'API

| Méthode |    Endpoint   |            Description             |
|---------|---------------|------------------------------------|
| GET     | `/users`      | Retourne tous les utilisateurs     |
| GET     | `/users/{id}` | Retourne un utilisateur par son ID |
| POST    | `/users`      | Crée un nouvel utilisateur         |
|---------|---------------|------------------------------------|

---

## Structure du projet

```
mulesoft-users-api/
├── users-api-learning.yaml   # Spécification OAS 3.0 de l'API
├── exchange.json             # Métadonnées MuleSoft
├── users-api-impl/           # Projet d'implémentation Mule
│   ├── src/main/mule/
│   │   └── users-api-impl.xml   # Flows Mule (pas commencer)
│   └── pom.xml
├── .gitignore
├──
└── README.md
```

---

## Auteur

**Alexis Arduca** - Étudiant 5ème année Epitech Montpellier  
[alexis.arduca@epitech.eu](mailto:alexis.arduca@epitech.eu)