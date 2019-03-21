# WordPress & PSR-2 Coding Standards for PHP_CodeSniffer

PHP_CodeSniffer ruleset to enforce WordPress &amp; PSR-2 coding conventions

## Introduction

A rule set that combines [WordPress Coding Standards](https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards) and [PSR-2](https://www.php-fig.org/psr/psr-2/).
The goal is to reduce the stress on developers by reducing the differences in coding conventions with other PHP applications.

## Installation

### Automatic install

Add the following scripts in `composer.json`

```json
{
  "scripts": {
    "install-codestandards": ["Dealerdirect\\Composer\\Plugin\\Installers\\PHPCodeSniffer\\Plugin::run"],
    "post-install-cmd": ["@install-codestandards"]
  }
}
```

```sh
composer require --dev dealerdirect/phpcodesniffer-composer-installer
composer require --dev yutahaga/wpcs-psr2
```

### Manually install

```sh
composer require --dev yutahaga/wpcs-psr2
phpcs --config-set installed_paths ./vendor/yutahaga/wpcs-psr2,./vendor/wp-coding-standards/wpcs,other-ruleset
```

## Usage

Here is an example of the `phpcs.xml`

```xml
<?xml version="1.0"?>
<ruleset name="My Coding Standards">
  <description>My Coding Standards extends WordPress-Extra and PSR-2</description>

  <rule ref="WordPress-PSR2" />

  <file>./app</file>
  <file>./bootstrap</file>
  <file>./config</file>
  <file>./functions.php</file>

  <exclude-pattern>bootstrap/cache/*.php</exclude-pattern>
  <exclude-pattern>*/*.js</exclude-pattern>
  <exclude-pattern>*/*.css</exclude-pattern>
  <exclude-pattern>*/*.xml</exclude-pattern>
  <exclude-pattern>*/node_modules/*</exclude-pattern>
  <exclude-pattern>*/vendor/*</exclude-pattern>
</ruleset>
```
