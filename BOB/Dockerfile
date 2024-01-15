# Utiliser une image de base Debian
FROM ubuntu:latest

# Mettre à jour les paquets et installer les nécessaires
RUN apt-get update && \
    apt-get install -y nano inetutils-ping strongswan openssl

# Générer la clé PSK et l'écrire dans ipsec.secrets
RUN openssl rand -base64 32 | awk '{print "10.0.0.100 10.0.0.200 : PSK \""$1"\""}' > /etc/ipsec.secrets

# Copier les fichiers de configuration dans le conteneur
COPY ipsec.conf /etc/ipsec.conf

# Démarrer StrongSwan
CMD ["ipsec", "start", "--nofork"]
