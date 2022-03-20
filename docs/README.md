# Custom PHP language modules for Nginx Unit on Debian

This Debian repository provides packages with custom PHP language modules for [Nginx Unit](https://unit.nginx.org) built against [PHP packages](https://packages.sury.org/php/) from [deb.sury.org](https://deb.sury.org/). I tried to make building process as transparent as possible - you can check all infrastructure related files [in parent GitHub project](https://github.com/Articus/unit-php). Repository is updated for each Nginx Unit release by [manual GitHub Actions workflow run](https://github.com/Articus/unit-php/actions/workflows/build-unit-php.yml).

Currently, the following versions are supported:
* Debian 10 Buster: PHP 7.4 , PHP 8.0 and PHP 8.1
* Debian 11 Bullseye: PHP 8.0 and PHP 8.1

## How to use

1. Ensure that `apt` can handle HTTPS Debian repository with GPG signing key:
```shell
apt install apt-transport-https ca-certificates gnupg
```
2. Install signing key:
```shell
apt-key adv --fetch-keys https://articus.github.io/unit-php/apt.pgp
```
3. Add repository list file:
```shell
#For Debian 10
echo "deb https://articus.github.io/unit-php/ buster main" > /etc/apt/sources.list.d/unit-php.list
echo "deb-src https://articus.github.io/unit-php/ buster main" >> /etc/apt/sources.list.d/unit-php.list

#For Debian 11
echo "deb https://articus.github.io/unit-php/ bullseye main" > /etc/apt/sources.list.d/unit-php.list
echo "deb-src https://articus.github.io/unit-php/ bullseye main" >> /etc/apt/sources.list.d/unit-php.list
```
4. Install corresponding [Nginx Unit Debian repository](https://unit.nginx.org/installation/#debian) and [deb.sury.org Debian repository](https://packages.sury.org/php/README.txt) (or provide another source for similar named Nginx Unit and PHP packages)
5. Install PHP language module package:
```shell
#For PHP 7.4
apt update
apt install unit-php7.4

#For PHP 8.0
apt update
apt install unit-php8.0

#For PHP 8.1
apt update
apt install unit-php8.1
```
## Enjoy!
Hopefully, this repository will be useful for someone except me.

If you have any suggestions, advices, questions or fixes feel free to [submit issue](https://github.com/Articus/unit-php/issues) or [pull request](https://github.com/Articus/unit-php/pulls).
