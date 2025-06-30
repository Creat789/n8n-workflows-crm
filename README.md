# CRM Immobilier — Schéma de Propriété

Ce dépôt contient la définition **OpenAPI (Swagger)** et la documentation associée pour le schéma unifié **Property** utilisé dans un CRM immobilier SaaS multi‑locataire. Chaque agence (locataire) dispose de ses propres données, et chaque bien est relié à un collaborateur.

---

## 📗 Table des Matières

1. [Présentation](#présentation)  
2. [Points Clés du Schéma](#points-clés-du-schéma)  
3. [Composants & Champs](#composants--champs)  
4. [Exemple d’Objet Property](#exemple-dobjet-property)  
5. [Intégration](#intégration)  
6. [Validation & Outils](#validation--outils)  
7. [Contribuer](#contribuer)  
8. [Licence](#licence)  

---

## 🔍 Présentation

Notre CRM doit gérer un seul schéma, flexible, pour représenter tous les types de biens :

- **Résidentiel** : appartements, maisons, villas  
- **Terrain** : constructible, agricole  
- **Parking** : intérieur, extérieur, box  
- **Commercial** : bureaux, commerce, entrepôts  
- **Ventes spécifiques** : VEFA, viager, location‑accession, échange, etc.

Ce modèle unifié permet de :

- **Isoler les données par locataire** (`agencyId`)  
- **Assigner un collaborateur** (`assignedCollaborator`)  
- **Gérer tous les types de transaction** (`transactionType`)  
- **Suivre les statuts avancés** (`status`, `publication`, `offers`)  
- **Étiqueter dynamiquement les biens** (`tags`)  
- **Champs optionnels** pour les détails spécifiques  

---

## ✨ Points Clés du Schéma

- **`transactionType`** : sale, rental, lease, lease_to_own, vefa, viager, sale_with_tenant, sale_on_margin, sale_share, exchange  
- **`type`** : apartment, house, land, parking, commercial, vefa, etc.  
- **`status`** : available, under_offer, under_contract, sold, rented, withdrawn  
- **`publication`** : `{ channel, publishedAt, expiresAt, featured }`  
- **`offers`** : suivi des offres reçues et des conditions  
- **`tags`** : étiquettes personnalisées définies par l’agence  
- **`assignedCollaborator`** : lie chaque bien à un collaborateur interne  
- **Blocs optionnels** :  
  - Maison : `levels`, `heating`, `pool`, `gardenArea`  
  - Terrain : `landDevelopment` (zonage, utilities)  
  - Parking : `dimensions`, `accessibilityForDisabled`  
  - Local commercial : `lease`, `intendedUse`  
  - VEFA : `vefa` (paymentPlan, completionGuarantee)  
  - Viager : `viager` (bouquet, rente)  
- **Copropriété** : `coOwnership`  
- **Diagnostics** : energyPerformance, greenhouseEmissions, asbestos, floodRisk  
- **Médias & docs** : `photos`, `documents`  

---

## 📋 Composants & Champs

### Champs principaux

| Champ                   | Type       | Obligatoire | Description                                             |
| ----------------------- | ---------- | ----------- | ------------------------------------------------------- |
| `id`                    | UUID       | Oui         | Identifiant unique                                      |
| `agencyId`              | string     | Oui         | Identifiant de l’agence (locataire)                     |
| `transactionType`       | string     | Oui         | Modalité de transaction (voir ci‑dessus)                |
| `type`                  | string     | Oui         | Catégorie de bien                                       |
| `status`                | string     | Oui         | Statut de publication (ex. available, under_offer...)   |
| `publication`           | object     | Non         | `{ channel, publishedAt, expiresAt, featured }`         |
| `tags`                  | array      | Non         | Liste d’étiquettes libres (ex. “mandat exclusif”)       |
| `offers`                | array      | Non         | Offres reçues sur le bien, avec conditions éventuelles  |
| `price`                 | object     | Oui         | `{ amount, currency }`                                  |
| `address`               | object     | Oui         | `{ street, postalCode, city, country, latitude, lng }`  |
| `assignedCollaborator`  | object     | Oui         | `{ collaboratorId, name, phone, email }`                |

### Sous‑objets selon type

- **Maison** : `levels`, `heating`, `fireplace`, `pool`, `gardenArea`  
- **Terrain** : `landDevelopment` (buildable, zoning, utilities)  
- **Parking** : `parkingType`, `dimensions`, `accessibilityForDisabled`  
- **Commercial** : `lease`, `intendedUse`  
- **VEFA** : `vefa` (developer, expectedDelivery, paymentPlan, completionGuarantee)  
- **Viager** : `viager` (usufructOwner, bareOwner, bouquet, rente)  

### Champs utilitaires

- **Copropriété** : `coOwnership`  
- **Diagnostics** : `diagnostics`  
- **Descriptions & médias** : `title`, `shortDescription`, `longDescription`, `photos`, `documents`  
- **Métadonnées & statistiques** : `createdAt`, `updatedAt`, `statistics`  

---

## 📌 Exemple d’Objet Property

```json
{
  "id": "4a7d1e4b-9f34-4c1b-80d8-5a2a7b0e9c3f",
  "agencyId": "agency_123",
  "transactionType": "sale",
  "type": "apartment",
  "status": "under_offer",
  "publication": {
    "channel": "SeLoger",
    "publishedAt": "2025-06-01T10:30:00Z",
    "expiresAt": "2025-08-01T00:00:00Z",
    "featured": true
  },
  "tags": ["mandat exclusif", "coup de cœur"],
  "offers": [
    {
      "amount": 340000,
      "buyer": "buyer_789",
      "submittedAt": "2025-06-15T12:00:00Z",
      "status": "pending",
      "conditions": ["sous réserve de financement"]
    }
  ],
  "price": { "amount": 350000, "currency": "EUR" },
  "address": {
    "street": "12 Rue de la Liberté",
    "postalCode": "75011",
    "city": "Paris",
    "country": "France",
    "latitude": 48.8566,
    "longitude": 2.3522
  },
  "assignedCollaborator": {
    "collaboratorId": "col_456",
    "name": "Alice Martin",
    "phone": "+33 6 12 34 56 78",
    "email": "alice@agency.com"
  },
  "bedrooms": 2,
  "bathrooms": 1,
  "floor": 3,
  "elevator": true,
  "coOwnership": {
    "totalUnits": 20,
    "annualFees": 2400,
    "propertyManager": {
      "name": "Syndic Pro",
      "contact": "contact@syndicpro.com"
    }
  },
  "diagnostics": {
    "energyPerformance": { "rating": "C", "consumption": 120 },
    "greenhouseEmissions": { "rating": "D", "emissions": 28 },
    "asbestos": "none",
    "lead": "none",
    "floodRisk": "low"
  },
  "title": "Charming 2‑bedroom in Bastille",
  "shortDescription": "Bright apartment with elevator, 55 m², 3rd floor",
  "longDescription": "Located in the heart of the 11th arrondissement... (more details)",
  "photos": [
    "https://cdn.agency.com/photos/apt123-1.jpg",
    "https://cdn.agency.com/photos/apt123-2.jpg"
  ],
  "documents": [
    { "type": "floor plan", "url": "https://cdn.agency.com/docs/apt123-plan.pdf" }
  ],
  "createdAt": "2025-05-20T09:00:00Z",
  "updatedAt": "2025-06-01T10:30:00Z",
  "statistics": { "views": 150, "inquiries": 7 }
}
