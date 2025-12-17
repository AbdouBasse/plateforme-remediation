# Guide de déploiement local – Plateforme de Remédiation

Ce guide explique comment installer et lancer la plateforme Moodle en local, étape par étape.

---

## 1. Prérequis

Avant de commencer, assurez-vous d’avoir :
- Un ordinateur sous Linux ou macOS (Windows possible avec WSL2).
- **Git** installé.
- **Docker** et **Docker Compose** installés.
- Connexion internet pour télécharger les images.

---

## 2. Récupération du projet

Clonez le dépôt GitHub :

```bash
git clone https://github.com/<ton-compte>/plateforme-remediation.git
cd plateforme-remediation/infra/docker

## 3.Lancement des services
docker compose up -d

## 4.Accès à Moodle
Suivez l’assistant d’installation Moodle :
Base de données :
Hôte : mariadb
Nom : moodle
Utilisateur : moodle
Mot de passe : moodlepass
Créez un compte administrateur.
Définissez la langue par défaut : Français.
Définissez le fuseau horaire : Africa/Dakar.

## 5.Vérification
Vérifiez que vous pouvez vous connecter avec le compte admin.
Créez un premier cours test (ex. “Mathématiques fondamentales”).
Ajoutez un quiz simple pour tester la remédiation.

## 6.Arrêt et redémarrage
docker compose down
docker compose up -d

## 7.Sauvegarde des données
Les données sont stockées dans des volumes Docker :
db_data : base MariaDB.
moodle_data : fichiers Moodle.
Pour sauvegarder : 
docker compose stop
docker run --rm -v plateforme-remediation_db_data:/var/lib/mysql -v $(pwd):/backup alpine tar czf /backup/db_backup.tar.gz /var/lib/mysql
docker run --rm -v plateforme-remediation_moodle_data:/bitnami/moodle -v $(pwd):/backup alpine tar czf /backup/moodle_backup.tar.gz /bitnami/moodle

## 8.Dépannage
Vérifier les logs :
docker logs moodle
docker logs mariadb
docker logs nginx

Vérifier la configuration Nginx :
nginx -t -c ./nginx.conf


✅ Résultat attendu
À la fin de ce guide, vous avez :
Moodle fonctionnel en local.
Un compte administrateur créé.
Un premier cours test prêt à être utilisé.
