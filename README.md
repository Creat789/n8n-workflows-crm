# Property CRM JSON Schema

Ce dépôt contient la définition complète du **JSON Schema** pour la gestion d’un bien immobilier dans un CRM, couvrant toutes ses caractéristiques, diagnostics, aspects juridiques, financiers ainsi que les descriptions multimédia.

---

## Description

Le fichier `property-crm.json` modélise un objet `Property` très détaillé, permettant de représenter un bien immobilier dans toute sa complexité :  
de ses caractéristiques physiques, à ses aspects administratifs, financiers, diagnostics techniques et documents associés.

---

## Structure détaillée

### 1. Identifiants & Métadonnées

- **id** (string, UUID) : Identifiant unique du bien.
- **agencyId** (string) : Identifiant de l’agence.
- **transactionType** (string) : Type de transaction (ex : vente, location).
- **type** (string) : Type de bien (ex : appartement, maison, terrain).
- **status** (string) : Statut (ex : disponible, vendu).
- **publishedAt** (date-time) : Date de publication.
- **createdAt**, **updatedAt** (date-time) : Dates de création et modification.

### 2. Prix

- **price** (objet) :  
  - **amount** (number) : Montant.  
  - **currency** (string) : Devise (ex : EUR).

### 3. Adresse

- **address** (objet) :  
  - **street** (string) : Adresse.  
  - **postalCode** (string) : Code postal.  
  - **city** (string) : Ville.  
  - **country** (string) : Pays.  
  - **latitude** (number) : Latitude GPS.  
  - **longitude** (number) : Longitude GPS.

### 4. Surface & Dimensions

- **area** (objet) :  
  - **builtArea** (number) : Surface construite (m²).  
  - **livingArea** (number) : Surface habitable (m²).  
  - **landArea** (number) : Surface terrain (m²).  
- **dimensions** (objet) :  
  - **length** (number) : Longueur (m).  
  - **width** (number) : Largeur (m).  
  - **height** (number) : Hauteur (m).

### 5. Informations Agence & Collaborateur

- **agencyInfo** (objet) :  
  - **name** (string) : Nom de l’agence.  
  - **phone** (string) : Téléphone.  
  - **email** (string) : Email.  
- **assignedCollaborator** (objet) :  
  - **id** (string) : ID collaborateur.  
  - **name** (string) : Nom.  
  - **phone** (string) : Téléphone.  
  - **email** (string) : Email.

### 6. Caractéristiques du Bien

- **bedrooms** (integer) : Nombre de chambres.  
- **bathrooms** (integer) : Nombre de salles de bain.  
- **hasElevator** (boolean) : Présence d’ascenseur.  
- **hasBalcony** (boolean) : Présence d’un balcon.  
- **hasTerrace** (boolean) : Présence d’une terrasse.  
- **parkingSpaces** (integer) : Nombre de places de parking.  
- **garageSpaces** (integer) : Nombre de garages.  
- **heating** (objet) :  
  - **type** (string) : Type de chauffage (ex : électrique, gaz).  
  - **installationDate** (date) : Date d’installation.  
- **pool** (objet) :  
  - **hasPool** (boolean) : Présence piscine.  
  - **poolType** (string) : Type (ex : creusée, hors-sol).  
- **gardenArea** (number) : Surface jardin (m²).  
- **landDevelopment** (objet) :  
  - **buildable** (boolean) : Terrain constructible.  
  - **urbanEquipments** (array) : Liste des équipements urbains présents.

### 7. Location & Usage

- **lease** (objet) :  
  - **type** (string) : Type de bail (ex : location vide, meublée).  
  - **startDate** (date) : Date début bail.  
  - **durationMonths** (integer) : Durée en mois.  
  - **rentAmount** (number) : Loyer mensuel.  
  - **chargesAmount** (number) : Charges mensuelles.  
- **intendedUse** (string) : Usage prévu (habitation, commercial, mixte).

### 8. Aspects Juridiques & Financiers

- **vefa** (objet) :  
  - **isVefa** (boolean) : Vente en état futur d’achèvement.  
  - **deliveryDate** (date) : Date livraison prévue.  
  - **contractSignedDate** (date) : Date signature contrat.  
- **viager** (objet) :  
  - **isViager** (boolean) : Vente en viager.  
  - **rentAmount** (number) : Rente viagère.  
  - **rentPeriodicity** (string) : Périodicité (mensuelle, trimestrielle).  
  - **deathDate** (date) : Date décès (le cas échéant).

### 9. Copropriété

- **coOwnership** (objet) :  
  - **numberOfUnits** (integer) : Nombre d’unités dans la copro.  
  - **annualCharges** (number) : Charges annuelles (€).  
  - **syndic** (objet) :  
    - **name** (string) : Nom syndic.  
    - **phone** (string) : Téléphone.  
    - **email** (string) : Email.  
  - **commonAreaDiagnostics** (objet) :  
    - **structureStatus** (string) : État structure.  
    - **waterLeakStatus** (string) : Problèmes fuites.  
    - **lastInspectionDate** (date) : Date dernier contrôle.

### 10. Diagnostics Techniques

- **diagnostics** (objet) :  
  - **energyPerformance** (string) : Diagnostic DPE (ex : A, B, C).  
  - **asbestos** (boolean) : Présence amiante.  
  - **lead** (boolean) : Présence plomb.  
  - **floodRisk** (boolean) : Risque inondation.  
  - **technicalReports** (array) : Liste de documents techniques.  
- **technicalDocuments** (array) :  
  - Chaque document a un **type** (string), **url** (string), **date** (date).

### 11. Descriptions & Médias

- **title** (string) : Titre court.  
- **shortDescription** (string) : Description courte.  
- **longDescription** (string) : Description longue détaillée.  
- **keywords** (array of strings) : Mots-clés générés automatiquement par IA.  
- **photos** (array of strings) : URLs des photos.  
- **documents** (array) :  
  - **type** (string) : Type de document (ex : plan, diagnostic).  
  - **url** (string) : Lien vers document.

---

## Utilisation

- Ce schéma valide et structure les données relatives aux biens immobiliers dans un CRM.  
- Permet une gestion complète, incluant aspects juridiques et diagnostics techniques.  
- Facilite l’intégration avec des systèmes tiers et outils d’intelligence artificielle.

---

## Liens & Références

- Référentiel principal : `property-crm.json`  
- [Dépôt GitHub des workflows CRM](https://github.com/Creat789/n8n-workflows-crm/tree/main/workflows)

---

## Licence

MIT License

---

*Document généré automatiquement pour décrire la structure JSON complète des biens immobiliers dans le CRM.*
