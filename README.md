[![Pipeline](https://gitlab.elias-haeussler.de/eliashaeussler/composer-update-check/badges/master/pipeline.svg)](https://gitlab.elias-haeussler.de/eliashaeussler/composer-update-check/-/pipelines)
[![Coverage](https://gitlab.elias-haeussler.de/eliashaeussler/composer-update-check/badges/master/coverage.svg)](https://gitlab.elias-haeussler.de/eliashaeussler/composer-update-check/-/pipelines)

# Composer update check plugin

> Composer Plugin to check outdated packages, based on their requirements

## Installation

```bash
composer req --dev eliashaeussler/composer-update-check
```

## Usage

```bash
# Check all root requirements
composer update-check

# Skip dev-requirements
composer update-check --no-dev

# Exclude custom packages from update check
composer update-check -i "my-vendor/*" -i "roave/security-advisories"

# Exclude dev-requirements and custom packages
composer update-check -i "my-vendor/*" --no-dev
```

## Development

### Preparation

```bash
# Clone repository
git clone https://gitlab.elias-haeussler.de/eliashaeussler/composer-update-check.git
cd composer-update-check

# Install Composer dependencies
composer install
```

### Run tests

Unit tests of this plugin can be executed using the provided Composer
command `test`. You can pass all available arguments to PHPUnit.

```bash
# Run tests
composer test

# Run tests and print coverage result
composer test -- --coverage-text
```

### Simulate application

A Composer script `simulate` exists which lets you run the Composer
command `update-check`, which is provided by this plugin. All parameters
passed to the script will be redirected to the Composer command.

```bash
# Run "composer update-check" command without parameters
composer simulate

# Pass parameters to "composer update-check" command
composer simulate -- -i "composer/*"
composer simulate -- --no-dev
```

Alternatively, this script can be called without Composer context:

```bash
./bin/simulate-application.sh
```

## License

[GPL 3.0 or later](LICENSE)
