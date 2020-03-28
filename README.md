
**Deploy Owncloud with docker, Hiawatha web server as reverse proxy and Letsencrypt**

There are few self-hosted solution for hosting and exchange files, but as I don't need a lot of extra futures, just to share documents, I decided to work with Owncloud. Every file sharing project have advantages and disadvantages.  

We are going to use docker deployment with docker volumes, only limitations is that they can be only 100GB of size, but this project will be EOL one day and we will move to something new or evolve this project to next level.

We use .env file in this project, and variables are used only first time when we deploy Ownncloud, after this all editing need to be run inside containers.

**Deploy**

After setting all VARIABLES in .env file, we can start our Owncloud instance

```docker-compose up -d```

**Stop**

```docker-compose down```


**Installing ReverseProxy (Hiawatha web server)**

1. Get the repository's public key:

```sudo apt-key adv --recv-keys --keyserver keys.gnupg.net 79AF54A9```

2. Add the following line to your /etc/apt/sources.list (or a new file in /etc/apt/sources.list.d/):

```deb http://mirror.tuxhelp.org/debian/ squeeze main```

3. Run:

```sudo apt-get update```

```sudo apt install hiawatha```

Check hiawatha-letsencrypt.md for setting Letsencrypt certificate (PoC).
