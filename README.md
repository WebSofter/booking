# Laravel 6.0 CRUD Application and Authentication via Auth0

Author David Amirkhanov (websofter) [https://wsofter.ru](https://wsofter.ru)

A hotel **booking system** that allows the user to log in through the Auth 0 system and gain access to search and booking

![Laravel 6 crud booking app demo screenshot](https://i.ibb.co/sbkb98J/screen-1.png)

![Laravel 6 crud booking app demo user account/dashboard screenshot](https://cdn.auth0.com/blog/laravel-6-crud/laravel-6-crud-app.png)

## Installation

**Clone the repo**

```bash
git clone https://github.com/WebSofter/booking
```

**Switch into the newly created repo folder**

```bash
cd travel-planet-crud
```

**Install the dependencies**

```bash
composer install
npm install
```

**Create the `.env` file**

```bash
mv .env.example .env
```

**Generate encryption key**

```bash
php artisan key:generate
```

**Signup for Auth0 account**

This application requires users to login. To make sure everything is works correctly, you need to [sign up for a free Auth0 account](https://auth0.com/signup).

Click on "Applications" and then create a new application. Name it anything you'd like and select "Regular web app". 

Scroll down and find "Allowed callback URLs". Fill this in with the URL you've been using for your application and then add `auth0/callback` to the end. E.g. `http://homestead.test/auth0/callback`.

Fill in the "Logout URL" with just the URL. E.g. `http://homestead.test`.

There are three Auth0 values on this page that you'll need to fill in in your `.env` file. Check out the [tutorial](https://auth0.com/blog/build-a-laravel-6-app-with-authentication/#Adding-Authentication-to-Your-Laravel-6-0-Application) for more information about this. 

```
AUTH0_DOMAIN=your-auth0-domain.auth0.com
AUTH0_CLIENT_ID=your-client-id
AUTH0_CLIENT_SECRET=your-client-secret
```

## Setup Homestead

If you don't already have VirtualBox and Vagrant setup, I recommend reading through that section of the tutorial.

Otherwise, generate your `Homestead.yaml` file now.

**Mac or Linux:**

```bash
php vendor/bin/homestead make
```

**Windows:**

```bash
vendor\\bin\\homestead make
```

You might need to updating your folder mapping. Just replace `/path/to/the/repo/travel-planet-crud` with the full path to wherever you cloned this repo.

```yaml
folders:
    -
        map: /path/to/the/repo/travel-planet-crud
        to: /home/vagrant/code
```

Once you have your updated `Homestead.yaml` file, start your VM with:

```bash
vagrant up
```

## Create, Migrate, and Seed the Database

**SSH into your VM**

```bash
vagrant ssh
cd code
```

**Run the migrations**

```bash
php artisan migrate
```

**Seed the database**

```bash
php artisan db:seed
```

**Exit the VM**

```bash
exit
```

## Book a Trip!

Now just head to [`http://localhost:8000/`](http://localhost:8000/) to check out your new Laravel 6 reservation booking system! Go ahead and sign up, head to the [hotels page](http://localhost:8000/hotels), and make some new reservations.

## Suspend the VM

Once you're done playing around, remember to suspend your VM.

```bash
vagrant suspend
```
