# LARAVEL REST API

**Technologies:** PHP 8.3, Laravel 11, MySQL 8

## Initial Local Setup (Ubuntu)

### 1. Clone the Project

Clone this repository:

```
git clone <repo-url>
```

### 2. Start Containers

Navigate to the `docker-compose-lamp` folder and start the containers in the background:

```
docker compose up -d
```

### 3. Create the Database

Create the `laravel_rest_api` and `laravel_rest_api_test` databases in MySQL on host machine for the project. (username: root, password: tiger)

### 4. Access the Web Container

Launch Bash in the `webserver` container:

```
docker compose exec webserver bash
```

Navigate to the project folder:

```
cd /var/www/html/
```

### 5. Configure `.env`

Copy `.env.example` to `.env`:

```
cp .env.example .env
```

### 6. Install Dependencies

Install all dependencies using Composer:

```
composer install
```

### 7. Generate Application Key

```
php artisan key:generate
```

### 8. Fix Errors

```
php artisan optimize:clear
chmod -R 777 bootstrap/cache
chmod -R 777 storage
```

### 9. Run Migrations and Seeders

```
php artisan migrate:fresh --seed
```

### 10. Configure Hosts File on Host Machine

Open `/etc/hosts`:

```
sudo nano /etc/hosts
```

Add the following line:

```
127.0.0.1   laravel-rest-api.local
```

### 11. Access API Documentation

You can now use the API documentation. See the [`api-docs.json`](storage/api-docs/api-docs.json) file and start testing
API requests.
Swagger UI will be available at http://your-api-project.test/api/documentation. Replace your-api-project.test with your
local development domain http://laravel-rest-api.local/api/documentation . 🚀

### 12. Change HTTP Port if Needed

If port 80 is already in use (e.g., by a frontend application), you can change the HTTP port
HOST_MACHINE_UNSECURE_HOST_PORT in the .env file in the laravel-sanctum-docker-compose folder

### 13. Other commands
```
docker compose stop
docker compose start
docker compose down
docker compose up -d
docker compose exec vue bash
docker compose build --no-cache
-------------------------
./vendor/bin/pint
php artisan l5-swagger:generate
php artisan test
php artisan migrate:fresh --seed

Using --hours=0.01 removes tokens that expired less than a minute ago
php artisan sanctum:prune-expired --hours=0.01
```
