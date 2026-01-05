---
{"dg-publish":true,"permalink":"/learning/linux/0-errors-that-you-could-experiment/","tags":["debian-13"]}
---

# Error: 404 not found

## What does it consist?

This error appeared me when I was trying to upgrade an apt package. Trying to upgrade protonvpn package:

```shell
sudo apt install network-manager-openvpn network-manager-openvpn-gnome [sudo] contraseña para alan: Installing: network-manager-openvpn network-manager-openvpn-gnome Installing dependencies: easy-rsa libeac3 libpkcs11-helper1t64 opensc opensc-pkcs11 openvpn Paquetes sugeridos: resolvconf openvpn-dco-dkms openvpn-systemd-resolved Summary: Upgrading: 0, Installing: 8, Removing: 0, Not Upgrading: 0 Download size: 292 kB / 2 468 kB Space needed: 9 002 kB / 357 GB available Continue? [S/n] S Err:1 [http://deb.debian.org/debian](http://deb.debian.org/debian) trixie/main amd64 network-manager-openvpn amd64 1.12.0-2 404 Not Found [IP: 199.232.158.132 80] Err:2 [http://deb.debian.org/debian](http://deb.debian.org/debian) trixie/main amd64 network-manager-openvpn-gnome amd64 1.12.0-2 404 Not Found [IP: 199.232.158.132 80] Error: Fallo al obtener [http://deb.debian.org/debian/pool/main/n/network-manager-openvpn/network-manager-openvpn_1.12.0-2_amd64.deb](http://deb.debian.org/debian/pool/main/n/network-manager-openvpn/network-manager-openvpn_1.12.0-2_amd64.deb) 404 Not Found [IP: 199.232.158.132 80] Error: Fallo al obtener [http://deb.debian.org/debian/pool/main/n/network-manager-openvpn/network-manager-openvpn-gnome_1.12.0-2_amd64.deb](http://deb.debian.org/debian/pool/main/n/network-manager-openvpn/network-manager-openvpn-gnome_1.12.0-2_amd64.deb) 404 Not Found [IP: 199.232.158.132 80] Error: No se pudieron obtener algunos archivos, ¿quizás deba ejecutar «apt-get update» o deba intentarlo de nuevo con --fix-missing?
```

With help from AI I found the solution

You have to remove from ``/var/lib/apt/lists/`` all sources list:

```shell
sudo rm -rf /var/lib/apt/lists/*
```

This will delete all package lists in cache that APT keeps in local storage. **After this**, you have to run ``sudo apt update`` to synchronize the new updates from package source (apt repositories)

After this, I recomend you reboot your system and, then you can  try to install that program or package that showed you this kind of error.