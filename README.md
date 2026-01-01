# Benchmarking des Technologies d'API : Évaluation Comparative

## Projet : Système de Gestion de Réservations Hôtelières

**Technologies évaluées :**  
REST API • SOAP • GraphQL • gRPC

**Infrastructure de test :**  
JMeter (tests de charge) • Prometheus (monitoring)

---

## Vue d'ensemble

Ce projet consiste en une analyse comparative approfondie de quatre architectures d'API différentes dans le contexte d'une application de réservation hôtelière. L'évaluation porte sur plusieurs dimensions critiques pour le choix d'une solution technique adaptée aux besoins d'une entreprise.

Les critères d'évaluation principaux incluent :
- **Temps de réponse** et latence
- **Capacité de traitement** (throughput)
- **Efficacité des ressources** (CPU et RAM)
- **Facilité de développement**
- **Niveau de sécurité**

L'ensemble des mesures de performance a été collecté via des tests de charge automatisés avec JMeter, tandis que les métriques système ont été capturées en temps réel grâce à Prometheus.

---

## Description du Domaine Métier

Le système de réservation hôtelière représente un cas d'usage typique nécessitant une architecture robuste capable de supporter :
- une charge importante de requêtes simultanées,
- des réponses rapides pour une expérience utilisateur optimale,
- une disponibilité continue,
- des mécanismes de sécurité avancés.

Les fonctionnalités testées couvrent l'ensemble des opérations CRUD :
- Ajout de nouvelles réservations
- Consultation des réservations existantes
- Mise à jour des informations de réservation
- Suppression de réservations

---

## Objectifs de l'Étude

Cette recherche vise à :
1. Établir une comparaison objective entre REST, SOAP, GraphQL et gRPC
2. Quantifier les performances en termes de latence et de débit
3. Examiner l'impact sur les ressources système (processeur et mémoire)
4. Comparer la complexité de mise en œuvre
5. Analyser les aspects sécuritaires
6. Proposer des recommandations basées sur les résultats obtenus

---

## Configuration Expérimentale

### Environnement de Test

- **Outil de charge :** Apache JMeter pour simuler les utilisateurs concurrents
- **Monitoring :** Prometheus pour le suivi des métriques CPU et mémoire
- **Configuration :** Environnement standardisé identique pour toutes les implémentations

### Scénarios de Charge

Les tests ont été effectués avec différents niveaux de charge :
- **10 utilisateurs simultanés** (charge légère)
- **100 utilisateurs simultanés** (charge modérée)
- **500 utilisateurs simultanés** (charge élevée)
- **1000 utilisateurs simultanés** (charge extrême)

Chaque scénario inclut l'exécution complète des opérations CRUD.

---

## Résultats : Analyse de la Latence

Le tableau ci-dessous présente les temps de réponse moyens (en millisecondes) pour chaque opération et chaque niveau de charge :

| Charge | Opération | REST | SOAP | GraphQL | gRPC |
|--------|-----------|------|------|---------|------|
| 10 | Création | 41 | 55 | 15 | 311 |
| 10 | Lecture | 32 | 25 | 14 | 25 |
| 10 | Modification | 11 | 11 | 11 | 27 |
| 10 | Suppression | 8 | 7 | 9 | 12 |
| 100 | Création | 26 | 34 | 175 | 105 |
| 100 | Lecture | 14 | 19 | 274 | 12 |
| 100 | Modification | 6 | 7 | 165 | 9 |
| 100 | Suppression | 5 | 5 | 104 | 6 |
| 500 | Création | 595 | 58 | 28 | 29 |
| 500 | Lecture | 588 | 31 | 34 | 10 |
| 500 | Modification | 521 | 16 | 17 | 9 |
| 500 | Suppression | 418 | 11 | 11 | 5 |
| 1000 | Création | 805 | 133 | 76 | 38 |
| 1000 | Lecture | 775 | 76 | 79 | 9 |
| 1000 | Modification | 677 | 51 | 49 | 6 |
| 1000 | Suppression | 573 | 35 | 39 | 5 |

---

## Résultats : Capacité de Traitement (Throughput)

Le débit mesuré en requêtes par seconde selon la charge appliquée :

| Charge | REST | SOAP | GraphQL | gRPC |
|--------|------|------|---------|------|
| 10 | 1.3 | 4.4 | 4.4 | 1.8 |
| 100 | 1.9 | 40 | 40 | 1.6 |
| 500 | 5.7 | 26 | 200 | 0.4 |
| 1000 | 9.8 | 398 | 400 | 0.43 |

---

## Analyse de la Consommation des Ressources

### Utilisation du Processeur

| Charge | REST | SOAP | GraphQL | gRPC |
|--------|------|------|---------|------|
| 10 | 9.7% | 0.04% | 15.48% | 12.98% |
| 100 | 9.6% | 12% | 13.51% | 11.72% |
| 500 | 13.25% | 11% | 10.22% | 11.87% |
| 1000 | 14.7% | 19.56% | 12.12% | 9.48% |

### Utilisation de la Mémoire

| Charge | REST | SOAP | GraphQL | gRPC |
|--------|------|------|---------|------|
| 10 | 155.8 MB | 187 MB | 224 MB | 257 MB |
| 100 | 243 MB | 240 MB | 386 MB | 223 MB |
| 500 | 258 MB | 186 MB | 220 MB | 260 MB |
| 1000 | 303 MB | 356 MB | 310 MB | 239 MB |

---

## Évaluation de la Complexité de Développement

| Aspect | REST | SOAP | GraphQL | gRPC |
|--------|------|------|---------|------|
| Durée de développement | 1–2 h | 2–3 h | 2–4 h | 3–5 h |
| Volume de code | Minimal | Important | Modéré | Modéré |
| Écosystème d'outils | Très riche | Riche | Riche | Modéré |
| Temps d'apprentissage | 1–2 jours | 3–5 jours | 2–3 jours | 3–4 jours |

---

## Analyse de la Sécurité

| Aspect | REST | SOAP | GraphQL | gRPC |
|--------|------|------|---------|------|
| Support TLS/SSL | ✓ | ✓ | ✓ | ✓ |
| Mécanismes d'authentification | OAuth2, JWT | WS-Security | OAuth2, JWT | JWT, mTLS |
| Robustesse face aux attaques | Modérée | Élevée | Modérée | Élevée |

---

## Synthèse Comparative

| Critère | REST | SOAP | GraphQL | gRPC |
|---------|------|------|---------|------|
| Latence | Élevée | Moyenne | Faible | Très faible |
| Throughput | Faible | Élevé | Très élevé | Faible |
| Utilisation CPU | Moyenne | Moyenne | Moyenne | Faible |
| Utilisation mémoire | Moyenne | Moyenne | Élevée | Moyenne |
| Sécurité | Bonne | Très élevée | Bonne | Très élevée |
| Facilité d'implémentation | Très élevée | Faible | Moyenne | Moyenne |

---

## Interprétation des Résultats et Recommandations

Les résultats de cette étude comparative révèlent des caractéristiques distinctes pour chaque technologie :

- **GraphQL** se distingue par son excellent débit, particulièrement sous des charges importantes, ce qui en fait un choix privilégié pour des applications nécessitant un haut volume de requêtes.

- **gRPC** excelle en termes de latence minimale et d'efficacité processeur, idéal pour des systèmes où la réactivité est critique.

- **SOAP** offre une sécurité renforcée et une robustesse appréciable, mais au prix d'une complexité de développement plus importante.

- **REST** conserve son avantage principal : la simplicité de mise en œuvre, bien qu'il présente des limitations en termes de scalabilité à très grande échelle.

La sélection de la technologie appropriée doit être guidée par les spécificités du projet, les contraintes de performance attendues et les exigences de sécurité du domaine applicatif.

---

*Projet académique - Évaluation comparative des architectures d'API modernes*
