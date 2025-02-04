# Nova ProgressBar Field


This package allows you to add progressbar fields to your resources and dashboards in [Nova](https://nova.laravel.com).

It basically takes a field with a decimal value between 0 and 1 and shows it as a percentage progress bar.

It edits like a text field.

<img src="https://github.com/flatroy/nova-progressbar-field/blob/main/img/screenshot-index.jpg" alt="index example">
<img src="https://github.com/flatroy/nova-progressbar-field/blob/main/img/screenshot-detail.jpg" alt="detail example">

#### DISCLAIMER:

This package is still work in progress. Feel free to help improve it.

[Original Package](https://packagist.org/packages/signifly/nova-progressbar-field)

-   [Requirements](#requirements)
-   [Installation](#installation)
-   [Basic Usage](#basic-usage)
-   [Advanced Options](#advanced-options)

---

## Requirements

-   [Laravel v9.0.\*](https://laravel.com/docs/9.0)
-   [Laravel Nova v4.\*](https://nova.laravel.com/docs/4.0/)

---

## Installation

Just run:

```bash
composer require flatroy/nova-progressbar-field
```

After this the setup will be complete, you can use the components listed here.

---

## Basic Usage

```php
// in App\Nova\User
...
use Flatroy\FieldProgressbar\FieldProgressbar;
...

/**
 * Get the fields displayed by the resource.
 *
 * @param \Laravel\Nova\Http\Requests\NovaRequest $request
 * @return array
 */
public function fields(NovaRequest $request)
{
    return [
        Number::make(__('Score'), 'score')
            ->min(0.01)
            ->max(1)
            ->step(0.01)
            ->hideFromIndex()
            ->hideFromDetail(),

        FieldProgressbar::make(__('Score'), 'score')
            ->hideWhenUpdating()
            ->hideWhenCreating()
            ->sortable(),  
    ];
}

```

---

## Advanced Options

### Custom color

```php
public function cards(NovaRequest $request)
{
    return [
        FieldProgressbar::make('Awesomeness')
            ->options([
                'color' => '#FFEA82',
            ]),
    ];
}
```

### Animate Bar Color A -> B

```php
public function cards(NovaRequest $request)
{
    return [
        FieldProgressbar::make('Awesomeness')
            ->options([
                'fromColor' => '#FFEA82',
                'toColor' => '#40BF55',
                'animateColor' => true,
            ]),
    ];
}
```

Feel free to come with suggestions for improvements.

Packages based on this package: [nova-progressbar-field](https://github.com/signifly/nova-progressbar-field) by [Signifly](https://github.com/signifly)
