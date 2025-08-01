# 🔐 Mise en conformité RGPD d'une base de données clients

Ce document présente la méthodologie de nettoyage et de pseudonymisation de notre base de données client initialement non conforme au RGPD, tout en conservant son potentiel analytique.

---

## 🗂️ Méthodologie

### I. 🧹 Nettoyage & transformation avec **PowerQuery (Excel)**

- Chargement du fichier CSV à mettre en conformité dans PowerQuery
- Promotion des en-têtes de colonnes
- Nettoyage des données incohérentes avec la fonction **"Remplacer les valeurs"**
- Suppression des **données sensibles non nécessaires** : Nom, Email, N° de Sécurité Sociale, Groupe sanguin, Employeur, ID web, Adresse complète, Coordonnées GPS
- **Pseudonymisation** :
  - Conversion de la **date de naissance en âge**
  - Fractionnement de l’adresse → conservation de **ville et code postal uniquement**
- **Catégorisation** de variables personnelles :
  - Tranches d’âge, niveaux de revenus, valeur de la résidence

---

## ✅ Bonnes pratiques appliquées

- **Minimisation** des données collectées (seulement ce qui est utile) & suppression de toutes données sensibles inutiles à l’activité commerciale
- **Pseudonymisation** systématique des données identifiantes
- Formatage des variables pour améliorer la lisibilité et la segmentation
- Garantie de la conformité pour un usage analytique ou marketing sans identification directe

---

## 📌 Préconisations RGPD

- Supprimer durablement les données sensibles inutiles
- Remplacer toute donnée permettant l'identification par un **ID**, une **catégorie** ou une **zone géographique élargie**
- Être **transparent avec les clients** sur les données collectées et leurs droits (accès, rectification, suppression)
- Ne conserver les données d’anciens clients que **1 à 2 ans maximum**

---

## 💡 Objectif

Assurer l’anonymat des clients tout en maintenant une base de données **qualitative**, exploitable pour l’analyse commerciale, statistique ou marketing, dans le respect des obligations légales RGPD.

I) SQL
• Import de la base données sur SQLite Studio.
• Extraction de la table au format .csv
II) PowerQuery
• Ouvrir Microsoft Excel
• Aller dans Données > Obtenir des données > A partir d’un fichier > A partir d’un fichier CSV
• La fenêtre du PowerQuery s’ouvre, cliquer sur « Transformer les données »
• Promouvoir la première ligne en tant qu’en-tête de colonnes.
• S’assurer de l’homogénéité des données des colonnes en supprimant les coquilles en utilisant la fonction « Remplacer les valeurs ».
• Supprimer les colonnes contenant des données sensibles non conformes à savoir : Employeur, numéro de Sécurité Sociale, Groupe Sanguin, ID site web, Nom, Emails, Points perdus, Latitude et longitude de la résidence principale.
• Remplacer la colonne Date de naissance par une colonne « Âge » en soustrayant la date de nais-sance à la date d’aujourd’hui, puis en convertissant le nombre de jours en nombre d’années sous forme d’entiers.
• Ne plus afficher l’adresse complète, mais uniquement la ville et le code postal en utilisant la fonction « Fractionner la colonne ». Supprimer ensuite le numéro et le nom de la rue du domicile du client.
• Transformer ensuite les âges, les tranches de revenus et la valeur de la résidence principale en intervalles de valeurs pour une meilleure segmentation. Pour cela créer une condition pour la colonne spécifiant que si une valeur était comprise dans un intervalle donné, afficher une valeur donnée, ici la tranche d’âge ou de revenus correspondantes.
• Avant de fermer et charger les données, s’assurer de bien ranger les colonnes et grouper les informations liées. Également vérifier que le bon type de données et attribué à chaque colonne. Dans notre cas, on a transformé les « oui » et « non » de la colonne est rouge en TRUE et FALSE pour convertir en booléen, transformé les points en virgules pour convertir en valeurs nu-mériques les colonnes « Age véhicule » et « Tarif Devis ».
• Enregistrer au format .csv point-virgule.

III) Préconisations
L’objectif de ces démarches est d’assurer l’anonymat de la base de clientèle tout en garantissant la qualité des données pour exploitation commerciale.
Cela passe donc par la nécessité de ne plus stocker les données sensibles énoncées dans la partie précédente (Num SS, Groupe Sanguin, Nom…) car elles n’ont pas de lien avec l’activité commerciale et n’ont pas à être exploité dans le cadre des activités de l’entreprise. Il faut donc également supprimer toute trace de telles données déjà collectées et présentes dans les bases de données
Toujours remplacer les données pouvant permettre d’identifier les clients soit par des ID (por remplacer le nom), soit par des intervalles (qui permettent de situer assez précisément le client au niveau des revenus, de l’âge…) soit par des données trop larges pour identifier précisément une personne (ville au lieu d’adresse complète, profession seule sans spécifier l’employeur…).
Il convient enfin d’être transparent vis-à-vis du client quant aux données le concernant qui sont utilisées ainsi qu’au niveau des droits dont il dispose sur celles-ci. Les données des anciens clients doivent être conservées durant un laps de temps raisonnable de 1 à 2 ans maximum.


