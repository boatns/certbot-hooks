# BoatNS authenticator hook for Certbot

This hook allows Certbot to use DNS-01 challenge for domains hosted by <a href="https://boatns.com/">BoatNS</a>

## Setup

Clone repository and create a `.boatns-auth` file:

    git clone https://github.com/boatns/certbot-hooks.git
    cd certbot-hooks
    cp .boatns-auth.sample .boatns-auth

Go to [boatns.com](https://boatns.com/) and create API key at: Login > API

Edit the `.boatns-auth` file and replace `<boatns-auth-secret>` with the API key auth secret.

## Issue certificate

```
certbot certonly \
  --manual \
  --preferred-challenges=dns \
  --manual-auth-hook /PATH/TO/certbot-hooks/authenticator \
  --manual-cleanup-hook /PATH/TO/certbot-hooks/cleanup \
  -d secure.example.com
```

## Domain specific API key

By default the authenticator hook loads the BoatNS API key from the file `.boatns-auth` for all requests.

But if we want to use a different API key for a specific domain, we could do so by creating a `.boatns-auth.DOMAIN` file - ie. create the file `.boatns-auth.some.example.com` for the domain `some.example.com`

## Certbot Documentation

Validation hooks: <https://certbot.eff.org/docs/using.html#pre-and-post-validation-hooks>

