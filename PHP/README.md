# PHP Container

These files will implement a PHP Docker container with the following items:

## PHP Stack

- PHP (Dockerfile)
  - Version 8.1 
  - It also contains the required plugins for correct working of PHP like ZIP, mcrypt, CURL, PNG, etc.
  - Tested with Laravel 7 and 8
- NodeJS (Dockerfile)
  - Version 16.17.0 LTS
  - Tested with VueJS 2 and 3
- Python (Dockerfile)
  - Version 3 (latest)

## Additional images

Also we have the following images in docker-compose file:

- NGINX as Web Server (latest version)
- MariaDB as Database Server (latest version)
- Redis as Cache Database Server (latest version)

This container stack has been tested even with MacOS M1 architecture (Apple Silicon) and works like a charm.

## Want to collaborate?

Please send me a message to Twitter (@RZEROSTERN) or an email to marco.ramirez@rzerocorp.com for getting in touch.
Also if you have an issue or want to propose a fix, please leave it in the Issues tab on Github. I'll fix it ASAP.

#### Made in Mexico with love by RZEROSTERN
