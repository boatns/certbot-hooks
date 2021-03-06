# BoatNS authenticator hook for Certbot

This hook allows Certbot to use DNS-01 challenge for domains hosted by BoatNS.

## Setup

Clone repository and create a `.boatns-auth` file:

    git clone https://github.com/boatns/certbot-hooks.git
    cd certbot-hooks
    cp .boatns-auth.sample .boatns-auth

Create API key: [boatns.com](https://boatns.com/) > Login > Profile > API keys

Replace `<boatns-auth-secret>` with the API key auth secret in the `.boatns-auth` file.

## Issue certificate

```
certbot certonly \
  --manual \
  --preferred-challenges=dns \
  --manual-auth-hook /path/to/certbot-hooks/authenticator \
  -d secure.example.com
```

## Cleanup Hook

There is no need for a cleanup hook, the validation record is automatically deleted after 15 minutes.

## Certbot Documentation

Validation hooks: <https://certbot.eff.org/docs/using.html#pre-and-post-validation-hooks>

