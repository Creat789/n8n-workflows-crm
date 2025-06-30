# Schéma JSON - Propriété Immobilière (Property)

Ce document décrit la structure JSON et les métadonnées associées pour un objet **Property** représentant un bien immobilier dans un CRM.

---

## Structure des champs principaux

### Identifiants et informations générales

| Champ            | Type          | Description orale                                    | Priorité | Rempli par défaut |
|------------------|---------------|-----------------------------------------------------|----------|-------------------|
| `id`             | string        | L'identifiant unique du bien est `{value}`.         | 1        | Non               |
| `transactionType`| string        | Il s'agit d'une transaction de type `{value}`.      | 1        | Non               |
| `type`           | string        | Le bien est un(e) `{value}`.                         | 1        | Non               |
| `status`         | string        | Le statut actuel est `{value}`.                       | 2        | Non               |

---

### Prix

| Champ            | Type          | Description orale                                   | Priorité | Rempli par défaut |
|------------------|---------------|----------------------------------------------------|----------|-------------------|
| `price.amount`   | number/null    | Le prix est de `{value}` euros.                     | 1        | Non               |
| `price.currency` | string        | La devise est `{value}`.                            | 1        | Oui (par défaut "EUR") |

---

### Adresse

| Champ           | Type          | Description orale                                    | Priorité | Rempli par défaut |
|-----------------|---------------|-----------------------------------------------------|----------|-------------------|
| `address.street`  | string/null   | Le bien se situe au `{value}`.                       | 1        | Non               |
| `address.postalCode` | string/null | Le code postal est `{value}`.                        | 1        | Non               |
| `address.city`    | string/null   | La ville est `{value}`.                              | 1        | Non               |
| `address.country` | string/null   | Le pays est `{value}`.                               | 2        | Non               |

---

### Surface & pièces

| Champ           | Type          | Description orale                                    | Priorité | Rempli par défaut |
|-----------------|---------------|-----------------------------------------------------|----------|-------------------|
| `area.livingArea`| number/null   | La surface habitable est de `{value}` mètres carrés.| 1        | Non               |
| `bedrooms`      | integer/null  | Le bien possède `{value}` chambres.                  | 2        | Non               |
| `bathrooms`     | integer/null  | Le bien possède `{value}` salles de bain.            | 2        | Non               |

---

### Étage & équipements

| Champ            | Type          | Description orale                                    | Priorité | Rempli par défaut |
|------------------|---------------|-----------------------------------------------------|----------|-------------------|
| `floor`          | integer/null  | Le bien se situe au `{value}`ᵉ étage.               | 3        | Non               |
| `totalFloors`    | integer/null  | L'immeuble compte `{value}` étages au total.        | 3        | Non               |
| `balcony`        | boolean/null  | Le bien dispose d'un balcon.                         | 3        | Non               |
| `terrace`        | boolean/null  | Le bien dispose d'une terrasse.                      | 3        | Non               |
| `parkingIncluded`| boolean/null  | Le bien inclut un parking.                           | 3        | Non               |
| `garage`         | boolean/null  | Le bien dispose d'un garage.                         | 3        | Non               |

---

### Chauffage et piscine

| Champ            | Type          | Description orale                                    | Priorité | Rempli par défaut |
|------------------|---------------|-----------------------------------------------------|----------|-------------------|
| `heating.type`   | string/null   | Le type de chauffage est `{value}`.                 | 3        | Non               |
| `pool.exists`    | boolean/null  | Le bien dispose d'une piscine.                       | 3        | Non               |

---

### Description et mots-clés

| Champ              | Type          | Description orale                                   | Priorité | Rempli par défaut |
|--------------------|---------------|----------------------------------------------------|----------|-------------------|
| `title`            | string        | Le titre de l'annonce est : `{value}`.             | 1        | Non               |
| `shortDescription` | string/null   | Description courte : `{value}`.                     | 2        | Non               |
| `keywords`         | array         | Mots clés associés : `{value}`.                     | 3        | Non               |

---

### Construction

| Champ              | Type          | Description orale                                   | Priorité | Rempli par défaut |
|--------------------|---------------|----------------------------------------------------|----------|-------------------|
| `constructionYear` | integer/null  | Le bâtiment a été construit en `{value}`.          | 2        | Non               |

---

## Notes

- Chaque champ possède une priorité qui peut guider l’ordre de saisie ou d’oralisation.  
- Les champs `oralSummary` sont des phrases modèles à utiliser pour restituer oralement la donnée.  
- Le champ `filled` indique si la donnée est renseignée (`true`) ou non (`false`).  

---

*Document généré automatiquement à partir du modèle JSON donné.*
