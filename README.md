# GroupProject-Team2

## Application Description:

This gaming application aims to simplify the process of finding a new game for gamers or people looking to get into gaming. It features a modern design and a random game generator that allows users to quickly discover new games. The application has four main pages, including a login page, a register page, a recommendation page, and a user page where users can save and like game suggestions. Users log in to save or like recommendations, and passwords are encrypted. The recommendation page displays one game at a time, and users can continuously view new games. This application is designed for ease of use and aims to help users spend more time gaming and less time deciding what to play.

## Contributors

- Joseph Pleasant, Keith Bates, Kimberly Marthias, Emma Lowery, Harrison Pena, Kevin McMahon 

## Technology Stack

- This website uses HTML, CSS, JavaScript, SQL, nodeJS and EJS in terms of programming langauges. Additonally a PostgreSQL database and Docker Compose are used for the website's backend.

## Prerequisites to run the application

- In order to run the application, you must have Docker Compose installed.

## Steps to deploy Gameroll on your CU private server

1. Change the docker-compose.yaml file web port from ‘3000:3000’ to ‘:3000’ and push your change to the repo.
2. While connected to the campus internet, use ssh through your terminal of choice to connect to your private server. The command is:
```
ssh <YOUR_IDENTIKEY>@csci3308.int.colorado.edu
```
3. Once the connection is established navigate to the directory you would like to have the deployment in.
3. Install rootless-docker with the command:
```
dockerd-rootless-setuptool.sh install
```
4. Now clone the DigitalDash repo with the command:
```
git clone git@github.com:dnerever/DigitalDash.git
```
5. Change the permissions for your repo with two commands:
```
chmod 777 .
chmod 766 package-lock.json
```
6. Add a .env within the gameroll/ directory.
7. Create a Twitch API key which can be done by following [IGDB’s guide](https://igdb.github.io/api/references/authentication/) (They explain it better than I could :)). Also here is IGDB’s guide that you must follow to get your bearer access token.
8. Navigate to the gameroll/ directory:
```
cd gameroll/
```
9. Now create a .env file:
```
touch .env
```
10. Now that we have both our Client ID and Bearer Token we can enter those in our .env file using vim with the command:
 ```
 vim .env
 ```
 Vim file example:
 ```
 # database credentials
 POSTGRES_USER="postgres"
 POSTGRES_PASSWORD="pwd"
 POSTGRES_DB="gameroll_db"

 SESSION_SECRET="super duper secret! Gameroll"
 client_id="<YOUR_CLIENT_ID>"
 authorization="Bearer <ACCESS_TOKEN>"
 ```
 Now save your .env and close the vim editor.
11. Ensure you’re in gameroll/ and run:
 ```
 docker-compose up -d
 ```
12. Find the exposed ports with:
 ```
 docker-compose ps
 ```
13. Access the web server through a browser (Example: http://csci3308.int.colorado.edu:3000):
 ```
 http://csci3308.int.colorado.edu:<YOUR_EXPOSED_DOCKER_WEB_PORT>
 ```
<!-- 14. That’s all! Enjoy all of your new games (We do have a hosted version of our application). -->

## Steps to deploy locally:
1. Make sure you have docker compose installed.
2. In a terminal of your choice navigate to your desired location for the repo.
3. Once there clone the repo:
```
git clone git@github.com:dnerever/DigitalDash.git
```
4. Navigate to the gameroll/ directory:
```
cd gameroll/
```
5. Add a .env within the gameroll/ directory.
    1. Create a Twitch API key which can be done by following [IGDB’s guide](https://igdb.github.io/api/references/authentication/) (They explain it better than I could :)).
    2. Also here is IGDB’s guide that you must follow to get your bearer access token.
    3. In the gameroll/ directory create a .env file:
    ```
    touch .env
    ```
    4. Enter both the Client ID and Bearer Token in our .env file using vim:
    ```
    vim .env
    ```
        a.Example .env:
        ```
        Vim file example:
        # database credentials
        POSTGRES_USER="postgres"
        POSTGRES_PASSWORD="pwd"
        POSTGRES_DB="gameroll_db"

        SESSION_SECRET="super duper secret! Gameroll"
        client_id="<YOUR_CLIENT_ID>"
        authorization="Bearer <ACCESS_TOKEN>"
        ```
    5. Save the file and exit vim
6. From the gameroll/ shutdown all other docker-compose containers:
```
docker-compose down -volumes
```
7. Start docker-compose:
```
docker-compose up -d
```
8. Wait until the API connection is secured (~5 seconds)
9. Access the web app from a browser of your choice:
[localhost:3000](localhost:3000)

<!-- **How to run tests**

N/A - to be added at a later date

**Link to application**

N/A - to be added at a later date -->
