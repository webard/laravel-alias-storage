# Laravel Alias Storage

Original package: https://github.com/besanek/laravel-alias-storage

**Will be deleted if original package accept PR with Laravel 11 compatibility.**

Meta filesystem, witch you can acreate aliases for other filesystems.

## Requirement

-   PHP >= 8.1
-   Laravel = 11.x

## Installing

```shell
$ composer require "webard/laravel-alias-storage"
```

## Basic Usage
```php
<?php // config/filesystems.php

return [
    'something' => [
        'driver' => 'alias',
        'target' => 'local',
    ],
];
```

In that case, calling  `Storage::disk('something')` will returns local filesystem.

## Real life use case

```php
<?php // config/filesystems.php

return [
    'video' => [
        'driver' => 'alias',
        'target' => env('VIDEO_STORAGE', 'local'),
    ],
    'local' => [
        'driver' => 'local',
        'root' => storage_path('app'),
    ],
    's3' => [
        'driver' => 's3',
        // config ...
    ]
];
```

In local development, you can store videos in local filesystem. But in production, you can set environment `VIDEO_STORAGE=s3` and
your video uploads are stored and served from S3. Awesome!
