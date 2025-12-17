# Image de base officielle Bitnami Moodle
FROM bitnami/moodle:latest

# Mainteneur
LABEL maintainer="Abdou Basse <contact@example.com>"

# Définir quelques variables d'environnement utiles
ENV MOODLE_SITE_NAME="Plateforme Remediation"
ENV MOODLE_LANG="fr"
ENV TZ="Africa/Dakar"

# Passer en root pour installer des extensions PHP
USER root

# Installer des extensions PHP nécessaires pour LDAP, XMLRPC, etc.
RUN install_packages \
    php-ldap \
    php-intl \
    php-xmlrpc \
    php-zip \
    php-gd

# Exemple : ajouter un plugin ou thème personnalisé
# COPY plugins/myplugin /bitnami/moodle/mod/myplugin

# Revenir à l’utilisateur non-root (sécurité)
USER 1001
