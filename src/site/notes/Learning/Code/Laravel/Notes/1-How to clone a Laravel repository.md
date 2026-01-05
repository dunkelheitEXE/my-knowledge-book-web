---
{"dg-publish":true,"permalink":"/learning/code/laravel/notes/1-how-to-clone-a-laravel-repository/"}
---

## How to clone correctly a obsidian repository

### Clone

- First, you have to execute ``git clone`` command

```bash
git clone <https://github.com/user/repositorio.git>
```

>Insetad of `https://github.com/user/repositorio.git`, you have to put your repo link

### Go to the repository

```bash
cd repositorio
```

---

### Install Composer dependencies

If you don't have composer, download and install it

Then execute:

```bash
composer install
```

This command will install all Laravel Dependencies

---

### Config file

Laravel uses a configuration file (``.env``), when you create your laravel project this does not exist, to create and prepare you have to copy from ``.env.example``:

```bash
cp .env.example .env
```

---

### Then, generate key

Laravel requires a unique key to save all sensitive data:

```bash
php artisan key:generate
```

---

### Configurate Database

Edit ``.env`` and set your DB values

```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=name_of_your_db
DB_USERNAME=user
DB_PASSWORD=password

```

If you are using XAMPP, check if it is running

---

### Migrate Database

If you are using migrations or database, you have to migrate all tables and fields with

```bash
php artisan migrate
```

If you need test data:

```bash
php artisan db:seed
```

---

### Change permissions

Laravel needs permission to access to ``storage`` and ``bootstarp/cache``:

```bash
chmod -R 775 storage bootstrap/cache
```

If you have other any trouble, try:

```bash
sudo chown -R www-data:www-data storage bootstrap/cache
```

---

### Start Laravel server

To try app, you can run:

```bash
php artisan serve
```

By default, the application will run on: [http://127.0.0.1:8000](http://127.0.0.1:8000/)

---

### Install Node

If your project is using Tailwindcss, Vue or React:

```bash
npm install
```

And compile Assets

```bash
npm run dev
```

(O `npm run build` para producción)

---
### If you do not have Tailwindcss

```shell
npm install tailwindcss @tailwindcss/vite
```