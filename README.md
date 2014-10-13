# uzyexe/keychain

## What is keychain.io

keychain.io is simple service to put your public key on servers for easy login (via SSH).
keychain.io use s3, sendgrid email.

[http://keychain.io](http://keychain.io)
[http://aws.amazon.com/s3/](http://aws.amazon.com/s3/)
[http://sendgrid.com](http://sendgrid.com)

## Dockerfile

[**Trusted Build**](https://registry.hub.docker.com/u/uzyexe/keychain/)

This Docker image is based on the [debian:wheezy](https://registry.hub.docker.com/_/debian/) base image.

## How to use this image

Create s3 backet.

[http://aws.amazon.com/s3/](http://aws.amazon.com/s3/)

Create sendgrid account.

[http://sendgrid.com](http://sendgrid.com)

Starting keychain.io container.

```
docker run \
  -e YOUR_AWS_ACCESS_KEY_ID=abc123 \
  -e YOUR_AWS_SECRET_ACCESS_KEY=abcd1234 \
  -e YOUR_SENDGRID_USERNAME=username \
  -e YOUR_SENDGRID_PASSWORD=password \
  -e YOUR_KEYCHAIN_BUCKET_NAME=keychain.io \
  -p 5000:5000 \
  uzyexe/keychain
```

## Upload your default SSH key

```
curl -s example.keychain.io:5000/<email>/upload | bash
```

## Install your key into authorized_keys

```
curl -s example.keychain.io:5000/<email>/install | bash
```

## API URLs

```
example.keychain.io:5000/<email>
example.keychain.io:5000/<email>/upload
example.keychain.io:5000/<email>/install
example.keychain.io:5000/<email>/fingerprint
example.keychain.io:5000/<email>/confirm/<token>
example.keychain.io:5000/<email>/all
example.keychain.io:5000/<email>/all/install
example.keychain.io:5000/<email>/<namedkey>
example.keychain.io:5000/<email>/<namedkey>/fingerprint
example.keychain.io:5000/<email>/<namedkey>/install
example.keychain.io:5000/<email>/<namedkey>/upload
```

