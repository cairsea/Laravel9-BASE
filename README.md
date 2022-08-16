# Laravel9 BASE

Laravel v9.25.1 (PHP v8.1.8)

## 初期設定

### 日本語設定

config/app.php

```php
    'timezone' => 'Asia/Tokyo',
    'locale' => 'ja',
    'faker_locale' => 'ja_JP',
```

### sail起動

`sail up -d`

### Sailカスタマイズ（dockerフォルダを移動）

`sail artisan sail:publish`

### sail バグ対策 vite.config.js に追記

```js
～略～

export default defineConfig({
    plugins: [
        laravel({
            input: [
                'resources/css/app.css',
                'resources/js/app.js',
            ],
            refresh: true,
        }),
    ],
    // 👇追加
    server: {
        hmr: {
            host: 'localhost'
        }
    }
});
```

### Xdebug Sail設定

.env の以下の一行を追記

```
SAIL_XDEBUG_MODE=develop,debug
```

launch.json に pathMappings と hostnameを追加

```json
            "port": 9003,
            "pathMappings": {
                "/var/www/html": "${workspaceFolder}"
            },
            "hostname": "localhost",
```

### Sail ポート番号変更 .env に任意のポート番号を追記

```
# ポート番号変更
APP_PORT=8080
FORWARD_DB_PORT=13306
FORWARD_REDIS_PORT=16379
```

### sail 再起動

```
sail down
sail up -d
```
