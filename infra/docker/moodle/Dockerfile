# Image de base officielle Bitnami Moodle
FROM bitnami/moodle:latest

# Mainteneur
LABEL maintainer="Abdou Basse <abdoubasseoconoor@gmail.com>"

# Variables d'environnement (optionnelles)
ENV MOODLE_SITE_NAME="Plateforme Remediation"
ENV MOODLE_LANG="fr"

# Installer des extensions PHP supplémentaires si besoin
USER root
RUN install_packages \
    php-ldap \
    php-intl \
    php-xmlrpc

# Copier un thème ou plugin personnalisé (exemple)
# COPY plugins/myplugin /bitnami/moodle/mod/myplugin

# Revenir à l’utilisateur non-root
USER 1001
