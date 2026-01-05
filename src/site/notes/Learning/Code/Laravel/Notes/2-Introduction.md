---
{"dg-publish":true,"permalink":"/learning/code/laravel/notes/2-introduction/"}
---

# 📚 Contents
- [[#Install Laravel 12|Install Laravel 12]]
	- [[#Install Laravel 12#For Linux/Mac OS|For Linux/Mac OS]]
	- [[#Install Laravel 12#For Windows|For Windows]]
- [[#How to create a Laravel Project|How to create a Laravel Project]]
	- [[#How to create a Laravel Project#Linux|Linux]]
	- [[#How to create a Laravel Project#Windows|Windows]]

---
## Install Laravel 12

### For Linux/Mac OS

For linux and Mac, you can run this command:

**Linux**

```shell
/bin/bash -c "$(curl -fsSL https://php.new/install/linux/8.4)"
```

**Mac**

```shell
/bin/bash -c "$(curl -fsSL https://php.new/install/mac/8.4)"
```

### For Windows

If you are running windows, you have just to install PHP, then install Composer:

```shell
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'.PHP_EOL; } else { echo 'Installer corrupt'.PHP_EOL; unlink('composer-setup.php'); exit(1); }"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```

## How to create a Laravel Project

### Linux

As a Linux user, I will recomend you two options:

1. Go to your favourite path and execute ``composer create-project laravel/laravel new-project``
2. Go to Apache 2 path and execute ``composer create-project laravel/laravel new-project``

### Windows

>[!DANGER] This section is not translated yet
>You may probably contribute to this repository doing a translation of this Knowledge Book

Para comenzar a usar Laravel, hay tres requisitos a cumplir.

- Tener Xampp y configurar el archivo `php.ini` quitando el comentario de la linea **zip.**
- Instalar composer
- Ejecutar en la ruta que deseamos el siguiente comando

```powershell
composer create-project laravel/laravel example-app
```
