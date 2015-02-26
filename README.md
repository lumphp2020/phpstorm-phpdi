# PHP-DI plugin for PhpStorm

This is very simple plugin which only implements type provider for services returned from PHP-DI container.

Strictly speaking current implementation is not dependent on PHP-DI in any way. It just supports certain way of receiving services from container which is widely used in PHP-DI:

```php
<?php
$postRepository = $container->get(PostRepository::class);
```

So the only thing this plugin does is:

1. It looks for all "get" method calls.
2. It filters out all except those where first argument contains `::class` substring.
3. It extracts class FQN from the first argument and provides it as a return type for that specific method call.

Result:

![Example screenshot](example.png?raw=true "Example screenshot")

Licence: MIT
