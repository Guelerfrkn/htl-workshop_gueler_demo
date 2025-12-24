# htl-workshop

## Setup and run the project locally

### Setup environment

Create a file `.env.dev` and fill in the environment variables with your values.

````text
APP_SECRET=...
ALANCAPTCHA_API_KEY=...
````

### Install dependencies and run app

```bash
mkdir -p public/uploads/catPictures
chmod -R 775 public/uploads
sudo chown -R $USER:www-data public/uploads

docker compose -f compose.development.yaml up
docker exec -it htl_workshop_dev_web bash
composer install
php bin/console doctrine:database:create
php bin/console doctrine:migrations:migrate
```
