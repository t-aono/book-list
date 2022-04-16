# book-list

## Overview

-   Single Page Application that allows you to manage books.

## Description

-   You can register, edit, and delete book titles.
-   The front end is built using Vue.js and the back end is built using Laravel.
-   SQLite is used for the database.

## Demo

![fqaeWCmFFOiVnQ7SHAKP1650095807-1650095920](https://user-images.githubusercontent.com/46856574/163667274-f194f750-6e6d-41dd-b19b-bb6d84653f5d.gif)

<!-- ## VS. -->

<!-- ## Requirement -->

## Usage

Launch locally

1. create database.sqlite

    ```
    touch database/database.sqlite
    ```

2. make `.env` file

    ```
    cp .env.example .env
    ```

3. package installation and build

    ```
    composer install
    npm install && npm run dev
    ```

4. make table

    ```
    php artisan migrate
    ```

5. start the server

    ```
    php artisan serve
    ```

<!-- ## Install -->

<!-- ## Contribution -->

<!-- ## Licence -->

## Author

[t-aono](https://github.com/t-aono)

<!-- README.md Sample -->
<!-- https://deeeet.com/writing/2014/07/31/readme/ -->
