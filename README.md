# Plateforme de Remédiation (basée sur Moodle)

Une plateforme éducative open-source et low-cost pour écoles, centres de formation et universités.  
Elle combine la **remédiation pédagogique** (soutien, rattrapage, interventions personnalisées) avec une **culture DevOps** (CI/CD, documentation, automatisation).

---

## 🎯 Objectifs
- Offrir des modules de remédiation accessibles (maths, TIC/Linux, motivation).
- Déployer rapidement avec peu de matériel.
- Adopter DevOps : versionnage, CI, documentation claire, amélioration continue.

---

## 🚀 Démarrage rapide

### Prérequis
- Linux ou macOS, Git, Docker et Docker Compose
- Optionnel : Ansible pour déploiement serveur

### Lancer en local avec Docker
```bash
git clone https://github.com/<ton-compte>/plateforme-remediation.git
cd plateforme-remediation/infra/docker
docker compose up -d
