# Notes Raspberry

## Création carte SD et installations
Source : [raspbian-france](https://raspbian-france.fr/creation-carte-sd-raspberry-raspbian-sous-gnulinux/)

- Formater en NTFS
- Dans le terminal entrer la commande
```console
sudo dd bs=1M if=chemin_vers_le_img_de_raspbian of=/dev/votre_carte 
status=progress conv=fsync
```
- Par sécurité, l'accès en SSH au Raspberry Pi n'est plus activé par défaut. Pour l'activer, il faut créer un fichier nommé "ssh" dans le dossier "/boot" de la carte SD. 
- Connecter la Raspberry Pi à la box en Wi-Fi

Créer un fichier wpa_supplicant.conf, situé à la racine de la partition boot de la carte.
```console
country=fr
update_config=1
ctrl_interface=/var/run/wpa_supplicant

network={
 scan_ssid=1
 ssid="MaBoxInternet"
 psk="ClefSecurite"
}
```
- Mise à jour Distrib
```console
apt-get update
```
- Mise à jour de la derniere version de rapsbian 
```console
apt-get upgrade
```
- Mise à jour du firmware ).
```console
rpi-update
```

## Wifi mode ad-hoc
- dans le fichier /etc/network/interfaces ( fichier vide à la base ) :
```console
auto wlan0 
iface wlan0 inet static
address 192.168.1.2
netmask 255.255.255.0
wireless-mode ad-hoc
wireless-essid RPI
wireless-channel 5
wireless-power on
```

L’interet de cette technique est de créer un réseau privé totalement isolé des autres. Le fait de vider le fichier /etc/network/interfaces suffit pour travailler en mode filaire et le réseau had hoc n’existe plus mais il faut rebooter les 2 cartes à chaque changement. 

- Sur un ordianteur avec Ubuntu le fichier interface est : 
```console
auto wlp2s0
iface wlp2s0 inet static
address 192.168.1.3
netmask 255.255.255.0
wireless-channel 5
wireless-essid RPI
wireless-mode ad-hoc
wireless-power on
```












