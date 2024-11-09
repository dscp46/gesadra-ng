# gesadra-ng
Gestionnaire d'activation pour une ADRASEC

Ce dépôt est constitué pour compiler, dans un premier temps, les idées nécessaires au développement d'un outil de gestion d'une activation dans le cadre Adrasec.
L'outil se concentrera, dans un premier temps, sur la gestion d'une main courante. Une fois ce module complété, un gestionnaire de vue opérationnelle commune sera ajouté.

## Scénarios d'usage
  * En arrivant sur l'outil, je m'identifie à l'aide d'un compte personnel.
  * Si je suis connecté depuis un réseau tactique (dont l'accès est réputé contrôlé) un droit d'accès en lecture seule m'est accordé automatiquement.
  * En tant qu'administrateur, je peux autoriser un navigateur à disposer automatiquement de droits en lecture et écriture (dispositif anti-lockout).
  * En tant qu'administrateur, je peux révoquer une telle autorisation.
  * En tant qu'utilisateur depuis un navigateur préalablement autorisé, je peux sélectionner mon identité depuis une liste déroulante. 
  * Une fois dûment autorisé, la liste des activations en cours m'est affichée.
  * En tant qu'utilisateur avec un droit de lecture, je peux consulter les activations en cours et cloturées. Si une activation est confidentielle, je peux consulter son contenu si et seulement si j'en suis le demandeur.
  * En tant qu'utilisateur avec un droit d'écriture, je peux créer une nouvelle activation. Je deviens le propriétaire de cette activation.
  * En tant que propriétaire d'une activation, je peux ajouter un évennement dans sa main courante.
  * En tant que propriétaire d'une activation, je peux transférer la propriété de mon activation à une autre personne qui dispose de droits en écriture.
  * En tant que propriétaire d'une activation, je renseigne la liste des stations APRS à surveiller.
  * En tant que propriétaire d'une activation, je peux clore mon activation. Une fois close, les éléments de mon activation deviennent immutables.
  * En tant que station APRS surveillée, l'ensemble des trames APRS que je transmets sont consignées dans la main courante.
  * En tant qu'utilisateur avec un droit de lecture, je peux exporter une activation. Cet export peut être chiffré à l'aide d'un mot de passe.
  * En tant qu'utilisateur avec un droit d'écriture, je peux importer une activation à partir d'un fichier d'export.
  * Lorsque je perds la connexion à mon serveur, je peux continuer à éditer localement ma main courante.
  * L'interface m'indique si je suis hors connexion, et l'heure de ma dernière connexion au serveur.
  * Lorsque la connexion à mon serveur est rétablie, mes changements sont envoyés sans mon intervention sur le serveur.
  * En tant qu'utilisateur avec un droit de lecture, je peux exporter une main courante soit au format PDF.

### Pour le cas d'une base utilisateur locale
  * Si j'ai perdu mon mot de passe, je peux m'envoyer un e-mail pour le changer.
  * Mot mot de passe doit respecter des règles de sécurité définiees (12 caractères, avec au moins 3 des 4 parmi: majuscule, minuscule, chiffre et caractère spécial).
  * Si j'ai perdu mon adresse e-mail, un administrateur peut changer mon adresse e-mail, et m'envoyer un autre mot de passe.
  * En tant qu'utilisateur avec un droit d'écriture, je peux créer un nouvel utilisateur avec des droits en écriture.
  * En tant qu'utilisateur avec un droit d'écriture, je peux créer un nouveau demandeur.
  * En tant qu'utilisateur depuis un navigateur préalablement autorisé, je ne peux pas changer mon mot de passe sans m'être préalablement connecté. 

## Objets et leurs attributs / actions
### Activation
 * Identifiant unique
 * Propriétaire (obligatoire).
 * Ordinateur propriétaire (optionnel).
 * Type d'activation (SATER, moyens supplétifs de comm, etc.)
 * Demandeur
 * Timestamp d'ouverture
 * Timestamp de cloture

### Entrée de main courante
 * Timestamp
 * Auteur
 * Type (standard (quoi qui ou), report sater, trame APRS)
 * Saisi par le propriétaire ou collecté automatiquement (pour archivage données COP/CTP).
 * Contenu

### Utilisateur
 * Nom d'utilisateur
 * Nom d'affichage
 * Adresse e-mail
 * Hash du mot de passe
 * Rôles accordés (lecture/1, écriture/2, gestionnaire d'organisme/4, administrateur/8)
 * Organisme de rattachement
 * Base externe (si applicable, pour déléguer auth et autz) 

### Organisme / Demandeur

## Points à clarifier
* Si base locale, mécanisme SCIM à prévoir pour les organismes?
* Oauth2 pour plus tard?
* Réutilisation d'une base eBrigade pour les membres?
* Date de cloture automatique d'une activation sans activité?
