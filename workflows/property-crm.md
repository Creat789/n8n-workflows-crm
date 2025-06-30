# Property JSON Schema

Ce document décrit le schéma JSON d'un objet **Property** représentant une propriété immobilière avec ses nombreuses caractéristiques.

---

## Structure de l'objet `Property`

```json
{
  "id": "string (UUID)",
  "agencyId": "string",
  "transactionType": "string",
  "type": "string",
  "status": "string",
  "publishedAt": "string (date-time)",
  "price": {
    "amount": "float",
    "currency": "string"
  },
  "address": {
    "street": "string",
    "postalCode": "string",
    "city": "string",
    "country": "string",
    "latitude": "float (optionnel)",
    "longitude": "float (optionnel)"
  },
  "area": {
    "builtArea": "float (optionnel)",
    "livingArea": "float (optionnel)",
    "landArea": "float (optionnel)"
  },
  "agencyInfo": {
    "name": "string (optionnel)",
    "contact": {
      "phone": "string (optionnel)",
      "email": "string (optionnel)"
    }
  },
  "assignedCollaborator": {
    "collaboratorId": "string",
    "name": "string (optionnel)",
    "phone": "string (optionnel)",
    "email": "string (optionnel)"
  },
  "bedrooms": "integer (optionnel)",
  "bathrooms": "integer (optionnel)",
  "separateToilets": "boolean (optionnel)",
  "floor": "integer (optionnel)",
  "totalFloors": "integer (optionnel)",
  "elevator": "boolean (optionnel)",
  "balcony": "boolean (optionnel)",
  "terrace": "boolean (optionnel)",
  "parkingIncluded": "boolean (optionnel)",
  "garage": "boolean (optionnel)",
  "levels": "integer (optionnel)",
  "heating": {
    "type": "string (optionnel)",
    "installationDate": "string (date-time, optionnel)"
  },
  "fireplace": "boolean (optionnel)",
  "pool": {
    "exists": "boolean (optionnel)",
    "type": "string (optionnel)"
  },
  "gardenArea": "float (optionnel)",
  "landDevelopment": {
    "isBuildable": "boolean (optionnel)",
    "urbanCertificate": "string (optionnel)",
    "zoning": "string (optionnel)",
    "utilities": {
      "water": "boolean (optionnel)",
      "sewer": "boolean (optionnel)",
      "electricity": "boolean (optionnel)",
      "telecom": "boolean (optionnel)"
    }
  },
  "parkingType": "string (optionnel)",
  "dimensions": {
    "length": "float (optionnel)",
    "width": "float (optionnel)",
    "height": "float (optionnel)"
  },
  "accessibilityForDisabled": "boolean (optionnel)",
  "lease": {
    "type": "string (optionnel)",
    "startDate": "string (date-time, optionnel)",
    "durationYears": "integer (optionnel)",
    "rent": {
      "amount": "float (optionnel)",
      "currency": "string (optionnel)",
      "maintenanceFees": "float (optionnel)"
    }
  },
  "intendedUse": "string (optionnel)",
  "vefa": {
    "developer": "string (optionnel)",
    "expectedDelivery": "string (date-time, optionnel)",
    "paymentPlan": [
      {
        "milestone": "string",
        "percentage": "float"
      }
    ],
    "completionGuarantee": {
      "insurer": "string (optionnel)",
      "expiryDate": "string (date-time, optionnel)"
    }
  },
  "viager": {
    "usufructOwner": "string (optionnel)",
    "bareOwner": "string (optionnel)",
    "bouquet": {
      "amount": "float (optionnel)",
      "currency": "string (optionnel)"
    },
    "rente": {
      "amount": "float (optionnel)",
      "currency": "string (optionnel)",
      "frequency": "string (optionnel)"
    }
  },
  "coOwnership": {
    "totalUnits": "integer (optionnel)",
    "annualCharges": "float (optionnel)",
    "propertyManager": {
      "name": "string (optionnel)",
      "contact": "string (optionnel)"
    },
    "diagnosticsCommonAreas": {
      "asbestos": "string (optionnel)",
      "lead": "string (optionnel)",
      "otherRisks": "string (optionnel)"
    }
  },
  "diagnostics": {
    "energyPerformance": {
      "rating": "string (optionnel)",
      "consumption": "float (optionnel)"
    },
    "greenhouseEmissions": {
      "rating": "string (optionnel)",
      "emissions": "float (optionnel)"
    },
    "asbestos": "string (optionnel)",
    "lead": "string (optionnel)",
    "floodRisk": "string (optionnel)"
  },
  "title": "string (optionnel)",
  "shortDescription": "string (optionnel)",
  "longDescription": "string (optionnel)",
  "keywords": [
    "string"
  ],
  "photos": [
    "string (URI)"
  ],
  "documents": [
    {
      "type": "string",
      "url": "string (URI)"
    }
  ],
  "technicalDocuments": {
    "constructionYear": "integer (optionnel)",
    "diagnostics": {
      "asbestos": {
        "present": "boolean",
        "reportDate": "string (date, optionnel)",
        "reportUrl": "string (URI, optionnel)"
      },
      "lead": {
        "present": "boolean",
        "reportDate": "string (date, optionnel)",
        "reportUrl": "string (URI, optionnel)"
      },
      "termites": {
        "present": "boolean",
        "reportDate": "string (date, optionnel)",
        "reportUrl": "string (URI, optionnel)"
      },
      "radon": {
        "riskLevel": "string (optionnel)",
        "reportDate": "string (date, optionnel)",
        "reportUrl": "string (URI, optionnel)"
      }
    },
    "installationsConformes": {
      "gas": {
        "compliant": "boolean",
        "inspectionDate": "string (date, optionnel)",
        "inspectionReportUrl": "string (URI, optionnel)"
      },
      "electricity": {
        "compliant": "boolean",
        "inspectionDate": "string (date, optionnel)",
        "inspectionReportUrl": "string (URI, optionnel)"
      },
      "sewer": {
        "compliant": "boolean",
        "inspectionDate": "string (date, optionnel)",
        "inspectionReportUrl": "string (URI, optionnel)"
      }
    },
    "risks": {
      "floodRisk": {
        "level": "string (optionnel)",
        "lastUpdated": "string (date, optionnel)"
      }
    },
    "complianceCertificates": [
      {
        "certificateType": "string",
        "issueDate": "string (date)",
        "certificateUrl": "string (URI, optionnel)"
      }
    ],
    "regulationsMet": [
      "string"
    ],
    "technicalDocumentsList": [
      {
        "documentName": "string",
        "documentUrl": "string (URI)"
      }
    ],
    "lastRevisionDate": "string (date, optionnel)"
  }
}
```

| Champ                | Type                    | Description                                                                                  |
|----------------------|-------------------------|----------------------------------------------------------------------------------------------|
| `id`                 | string (UUID)           | Identifiant unique de la propriété.                                                         |
| `agencyId`           | string                  | Identifiant de l'agence immobilière.                                                        |
| `transactionType`    | string                  | Type de transaction (ex : vente, location).                                                 |
| `type`               | string                  | Type de bien (ex : appartement, maison).                                                    |
| `status`             | string                  | Statut du bien (ex : disponible, vendu).                                                    |
| `publishedAt`        | string (date-time)      | Date de publication de l'annonce.                                                           |
| `price`              | object                  | Prix du bien avec montant (`amount`) et devise (`currency`).                                |
| `address`            | object                  | Adresse complète : rue, code postal, ville, pays, latitude, longitude.                      |
| `bedrooms`           | integer (nullable)      | Nombre de chambres.                                                                          |
| `bathrooms`          | integer (nullable)      | Nombre de salles de bain.                                                                    |
| `separateToilets`    | boolean (nullable)      | Présence de toilettes séparées.                                                             |
| `floor`              | integer (nullable)      | Numéro de l'étage.                                                                           |
| `totalFloors`        | integer (nullable)      | Nombre total d'étages dans l'immeuble.                                                      |
| `elevator`           | boolean (nullable)      | Présence d'un ascenseur.                                                                     |
| `balcony`            | boolean (nullable)      | Présence d'un balcon.                                                                        |
| `terrace`            | boolean (nullable)      | Présence d'une terrasse.                                                                     |
| `parkingIncluded`    | boolean (nullable)      | Parking inclus dans le bien.                                                                 |
| `garage`             | boolean (nullable)      | Présence d'un garage.                                                                        |
| `heating`            | object                  | Informations sur le chauffage : type et date d'installation.                                |
| `pool`               | object                  | Présence et type de piscine.                                                                |
| `gardenArea`         | number (float, nullable)| Surface du jardin en m².                                                                     |
| `landDevelopment`    | object                  | Infos sur constructibilité, certificat urbain, zonage, utilités.                            |
| `lease`              | object                  | Détails sur le bail : type, date de début, durée, loyer, charges.                           |
| `vefa`               | object                  | Vente en l'état futur d'achèvement : promoteur, livraison prévue, plan de paiement.         |
| `viager`             | object                  | Infos viager : usufruitier, nu-propriétaire, bouquet, rente.                                |
| `coOwnership`        | object                  | Copropriété : nombre d'unités, charges annuelles, syndic, diagnostics parties communes.     |
| `diagnostics`        | object                  | Diagnostics énergétiques et risques (amiante, plomb, risque inondation, etc.).              |
| `title`              | string                  | Titre de l'annonce.                                                                          |
| `shortDescription`   | string                  | Description courte.                                                                          |
| `longDescription`    | string                  | Description longue.                                                                          |
| `keywords`           | array[string]           | Mots-clés générés automatiquement par l'IA (ex: "vue mer", "accès handicapé").             |
| `photos`             | array[string (uri)]     | Liste d'URLs des photos.                                                                     |
| `documents`          | array[object]           | Documents associés avec type et URL.                                                        |
| `technicalDocuments` | object                  | Documents techniques, diagnostics, certificats de conformité, dates de révision.           |
