# Traefik reverse proxy with backend services

Easy to use tutorial how to use **[docker](https://www.docker.com/) and [traefik](https://traefik.io/) as automatic SSL proxy** with auto-redirect from http to https **in front of a flexible infrastructure of backend services**, like this one:


![Architecture](https://raw.githubusercontent.com/containous/traefik/master/docs/img/architecture.png)

## How to use

### Prerequisites
- `docker`, `docker-Compose` and `git` (all latest) must be installed.

### Start up frontend proxy
- Clone this repo: 

  ```git clone https://github.com/bitleaf/simple-traefik-proxy-and-services.git```

- Go into folder `frontend-traefik`: 

  ```cd frontend-traefik```

- Create empty file `acme.json` to store SSL certificate data and set correct permissions: 
 
  ```touch traefik-conf/acme.json && chmod 600 traefik-conf/acme.json```

- Customize the config file `traefik-conf/traefik.toml` to your environment. Change `domain` and `email`.

- Create docker network for the proxy: 

  ```docker network create proxy```

- Start traefik: 

  ```docker-compose up -d```

- Now continue with starting up at least one backend service. Then, traefik can automatically issue a valid SSL certificate from [Let's encrypt](https://letsencrypt.org/).


### Start up backend services
- Go into a folder of the backend services and follow the specific README. The service `backend-whoami` is a simple first service to start with.

## Kudos
Thanks to [firecyberice](https://github.com/firecyberice) for the basic architectural idea of this deployment and [baez90](https://github.com/baez90) for reminding me about this architecture and providing a working example!

## Support this project

If you want this project to get better, support me with a few cents:

<a href="https://liberapay.com/Bitleaf/donate"><img alt="Donate using Liberapay" src="https://liberapay.com/assets/widgets/donate.svg"></a>

## License

![](https://www.gnu.org/graphics/gplv3-127x51.png)

The project is licensed unter the GPLv3.

Copyright (C) Mathias Renner

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

See <http://www.gnu.org/licenses/> fore more information.

