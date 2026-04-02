# org.freedesktop.Sdk.Extension.php85

This extension adds PHP support to Flatpak.

PHP installs to `/usr/lib/sdk/php85` inside the sandbox.

Example Visual Studio Code Configuration

```json
"php.validate.executablePath": "/usr/lib/sdk/php85/bin/php",
"php.executablePath": "/usr/lib/sdk/php85/bin/php",
```

Includes

* [php](https://php.net/)
* [composer](https://github.com/composer/composer)
* [PHIVE](https://phar.io/)
* [apcu](https://pecl.php.net/package/APCu)
* [xdebug](https://xdebug.org/)
* [pie](https://www.php.net/manual/en/install.pie.intro.php)

Each Flatpak can have its own custom php configuration files.
e.g. for Visual Studio Code
`~/.var/app/com.visualstudio.code/config/php/8.5/ini/my-custom.ini` or `/var/config/php/8.5/ini/my-custom.ini` from a sandboxed shell.

Global composer installs are limited to the Flatpak they were installed in.

#### Troubleshooting
`/usr/bin/env: ‘php’: No such file or directory`

Run `. /usr/lib/sdk/php85/enable.sh` or add `/usr/lib/sdk/php85/bin` to your $PATH.

#### Modules

```bash
bash-5.0$ php -m
[PHP Modules]
apcu
bz2
Core
ctype
curl
date
dom
fileinfo
filter
hash
iconv
intl
json
lexbor
libxml
mbstring
openssl
pcntl
pcre
PDO
pdo_sqlite
Phar
posix
random
Reflection
session
SimpleXML
SPL
sqlite3
standard
tokenizer
uri
xdebug
xml
xmlreader
xmlwriter
Zend OPcache
zip
zlib

[Zend Modules]
Xdebug
Zend OPcache
```
#### Build
```bash
flatpak-builder --repo repo .build org.freedesktop.Sdk.Extension.php85.json --force-clean
```
