# AutoMapper+ PHPStan configuration

This package provides a configuration for [AutoMapper+](https://github.com/mark-gerarts/automapper-plus).
It serves as a workaround for the problem described in [this issue](https://github.com/mark-gerarts/automapper-plus/issues/42).

## Background

Basically, we introduced a third parameter (`$context`) to the `map` method of 
the `MapperInterface`. This was introduced after the 1.0 release, so to prevent
introducing breaking changes, the interface doesn't explicitly have the
`$context` parameter. It will be explicitly added in the 2.0 release.

But, in the meantime PHPStan will complain about the missing parameter if you
use it in your code. The message will be something like this:

```
Method AutoMapperPlus\MapperInterface::map() invoked with 3 parameters, 2 required. 
```

This package suppresses these errors.

## Usage and installation

This package is installed automatically with the base library. To enable it 
there are 2 options:

- Using [phpstan/extension-installer](https://github.com/phpstan/extension-installer). This will register the extension automatically.
- Manually register the configuration.

```yaml
includes:
    - vendor/mark-gerarts/phpstan-automapper-plus/phpstan.neon
```