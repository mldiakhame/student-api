# student-api

API REST Spring Boot pour la gestion d'étudiants — TP Intégration Continue avec Jenkins.

**Module** : Livraison Continue (2IDA2103) — Master 1 UNCHK  
**Auteur** : Dr. Mouhamadou Lamine DIAKHAME
**Auteur** : Etudiant MICDA Alpha DIALLO
## Prérequis

- Java 17
- Maven 3.9

## Lancer le projet

```bash
mvn spring-boot:run
```

## Exécuter les tests

```bash
mvn clean test
```

## Vérifier la couverture (seuil 70 %)

```bash
mvn verify
```

## Endpoints

| Méthode | URL                    | Description              |
|---------|------------------------|--------------------------|
| GET     | /api/students          | Liste tous les étudiants |
| GET     | /api/students/{id}     | Récupère un étudiant     |
| POST    | /api/students          | Crée un étudiant         |
| DELETE  | /api/students/{id}     | Supprime un étudiant     |

## Exemple de requête POST

```json
{
  "nom": "Diop",
  "prenom": "Awa",
  "email": "awa@uvs.sn",
  "moyenne": 14.5
}
```
