# traefik-letsencrypt

## Preparing

 * Copy `traefik.toml_example` to `traefik.toml` and change `email` variable to your email address;

## Run 

Run `docker-compose up -d` 

## Example 
Copy provided example code to some `docker-compose.yml` file, change `example.com` to your domain and run it:

```
version: '2'

# Use traefik network
networks:
  default:
    external:
      name: traefik-letsencrypt_webgateway

services:
  nginx:
    image: nginx:alpine
    hostname: example.com
    labels:
      # Labels for Traefik
      - "traefik.enable=true"
      - "traefik.backend=example.com"
      - "traefik.frontend.rule=Host:example.com, example.com"
      - "traefik.frontend.headers.SSLRedirect=true"
      - "traefik.frontend.headers.SSLHost=example.com"
```

Check you're domain in a browser
