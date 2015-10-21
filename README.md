## ScriptMotd_Ynh Dynamic MOTD for Yunohost v2+ Debian

>Affichage dynamique SSH spécial serveur Yunohost avec mise à jour installable

>Debian Dynamic Message of the Day with Updates

#Install Figlet / installe Figlet - ASCII art :

    sudo apt-get install figlet

#Create directory / Créez un nouveau dossier. 

    sudo git clone https://github.com/yolateng0/Motd-Dynamic-Debian_ynh.git /etc/update-motd.d

#Change to new directory / ouvrir le nouveau dossier

    cd /etc/update-motd.d/

#Remove MOTD file / Suppression

    sudo rm -frv /etc/motd

#Symlink dynamic MOTD file / lien symbolique pour le fichier motd

    sudo ln -s /var/run/motd /etc/motd

#Reboot System for settings to take effect / Rebooter votre serveur
    sudo reboot
    
#SOURCES
https://wiki.debian.org/motd
