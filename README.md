# 🔐 RGPD Data Cleaning – Cas pratique & Guide de bonnes pratiques

Ce projet combine un **exemple fictif** de mise en conformité RGPD d’une base de données client et un **guide synthétique** des règles à suivre pour protéger les données personnelles dans le cadre d’un projet data.

---

## 🎯 Objectif du projet

L’objectif est de transformer une base SQL initialement non conforme au RGPD en une base **pseudonymisée, minimisée et sécurisée**, tout en conservant sa valeur analytique.

Le traitement a été réalisé de la manière suivante :
- **Extraction SQL** → export CSV
- **Transformation dans PowerQuery / Excel**
- Application de règles RGPD : pseudonymisation, minimisation, séparation des identifiants, documentation, restriction des accès
