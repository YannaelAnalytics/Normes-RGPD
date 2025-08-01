# 🔐 Mise en conformité RGPD d'une base de données clients

Ce document présente la méthodologie de nettoyage et de pseudonymisation de notre base de données client initialement non conforme au RGPD, tout en conservant son potentiel analytique.

---

## 🗂️ Méthodologie

### I. 🧹 Nettoyage & transformation avec **PowerQuery (Excel)**

- Chargement du fichier CSV à mettre en conformité dans PowerQuery.
- Promotion des en-têtes de colonnes.
- Nettoyage des données incohérentes avec la fonction **"Remplacer les valeurs"**.
- Suppression des **données sensibles non nécessaires** : Nom, Email, N° de Sécurité Sociale, Groupe sanguin, Employeur, ID web, Adresse complète, Coordonnées GPS.
- **Pseudonymisation** :
  - Conversion de la **date de naissance en âge**.
  - Fractionnement de l’adresse → conservation de **ville et code postal uniquement**.
- **Catégorisation** de variables personnelles :
  - Tranches d’âge
  - Niveaux de revenus
  - Valeur de la résidence

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
