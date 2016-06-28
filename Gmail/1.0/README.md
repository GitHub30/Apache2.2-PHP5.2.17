# Apache2.2 + PHP5.2 + Gmail

## Installation

```
IMAGE=gmail:1.0
YOUR_EMAIL=foo@gmail.com
YOUR_PASSWORD=fooword

docker build -t $IMAGE --build-arg EMAIL=$YOUR_EMAIL --build-arg PASSWORD=$YOUR_PASSWORD .
docker run --name some-name -v "$PWD":/usr/local/apache2/htdocs/ -d $IMAGE
```

## If you would like to send mail simply

```
ssmtp -t < test-mail
```
