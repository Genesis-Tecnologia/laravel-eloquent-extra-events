# eloquent-extra-events

[![Total Downloads](https://poser.pugx.org/genesistecnologia/eloquent-extra-events/downloads)](https://packagist.org/packages/genesistecnologia/eloquent-extra-events)
[![Monthly Downloads](https://poser.pugx.org/genesistecnologia/eloquent-extra-events/d/monthly)](https://packagist.org/packages/genesistecnologia/eloquent-extra-events)
[![Daily Downloads](https://poser.pugx.org/genesistecnologia/eloquent-extra-events/d/daily)](https://packagist.org/packages/genesistecnologia/eloquent-extra-events)
[![Latest Stable Version](https://poser.pugx.org/genesistecnologia/eloquent-extra-events/v/stable)](https://packagist.org/packages/genesistecnologia/eloquent-extra-events)
[![Latest Unstable Version](https://poser.pugx.org/genesistecnologia/eloquent-extra-events/v/unstable)](https://packagist.org/packages/genesistecnologia/eloquent-extra-events)
[![License](https://poser.pugx.org/genesistecnologia/eloquent-extra-events/license)](https://packagist.org/packages/genesistecnologia/eloquent-extra-events)

Install:

```
For 5.2.x, 5.3.x and 5.4.x:
composer require genesistecnologia/eloquent-extra-events:0.3.5
```

```
For 5.5.x:
composer require genesistecnologia/eloquent-extra-events
```

In your model:

`use GenesisTecnologia\LaravelEloquentExtraEvents\ExtraEventsTrait;`

Events:
  * eloquent.syncing
  * eloquent.synced
  * eloquent.attaching
  * eloquent.attached
  * eloquent.detaching
  * eloquent.detached

Listen events in `App\Providers\AppServiceProvider`:

```
In 5.2.x and 5.3.x:
Event::listen('eloquent.syncing*', function (array $eventData) {
});

In 5.4.x and 5.5.x:
Event::listen('eloquent.syncing*', function ($eventName, array $eventData) {
});

```

Available properties:

- `$eventData['parent_model']`: `string` e.g. `'App\Models\Model'`
- `$eventData['parent_id']`: `integer` e.g. `42`
- `$eventData['related_model']`: `string` e.g. `'App\Models\Model'`
- (except eloquent.synced) `$eventData['related_ids']`: `array` e.g. `[31,41]`
- (Only eloquent.detached) `$eventData['results']`: `integer` e.g. `2`
- (Only eloquent.synced) `$eventData['changes']`: `array` with the following keys:
  - `'attached'`: `array` e.g. `[1, 8]`
  - `'detached'`: `array` e.g. `[15, 16]`
  - `'updated'`: `array` e.g. `[23]`
  
  

Note: sync trigger attach and detach.
