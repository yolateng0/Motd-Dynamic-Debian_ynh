## ScriptMotd_Ynh Dynamic MOTD for Yunohost v2+ Debian Ubuntu Raspbian

>Affichage dynamique SSH spécial serveur Yunohost avec mise à jour de sécurités à prioriser

>Debian Dynamic Message of the Day with Updates

>https://yunohost.org/

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
>https://wiki.debian.org/motd

>https://scotte.github.io/2014/03/a-better-dynamic-motd/

#How to script updates to your /etc/motd

A little less known thing about /etc/motd in Debian and Ubuntu is that pam will actually update your /etc/motd based simply on the scripts in /etc/update-motd.d. So to replicate the above scripts, you could do:

        mkdir /etc/update-motd.d
        cat > /etc/update-motd.d/10uname <<EOF
        #! /bin/sh
        uname -snrvm
        EOF
        cat > /etc/update-motd.d/20tail <<EOF
        #! /bin/sh
        [ ! -f /etc/motd.tail ] && exit 0
        cat /etc/motd.tail
        EOF
        chmod a+x /etc/update-motd.d/*

> Then you could add other scripts to your /etc/update-motd.d directory to add stuff to your /etc/motd. See the manpage for more information. 
