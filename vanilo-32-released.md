---
title: Vanilo 3.2 Released
excerpt: Vanilo 3.2 has been released with the session-based checkout store. See what's new.
date: 2022-12-08
tags: [Releases, News, 'Vanilo 3']
featured: false
---
Vanilo 3.2 has been released with the persistent, session-based checkout store and other improvements.

## Minimum Requirements

The requirements of Vanilo 3.2 are the same a v3.1, except for the Concord requirement which has been changed from v1.11
to v1.12+.

## Breaking Changes

There are NO BREAKING CHANGES in this release. We stick to [Semantic Versioning](https://semver.org).

## Checkout Improvements

The default checkout driver is the "request" store, which holds the entered data only during the request/validation cycle.
This means, that if the shopper navigates away from the checkout page, the data they entered goes away.

To solve this problem, the "session" checkout driver has been finalized with this version, which stores the data in the session.
Therefore, method and property calls that are sent to the `Checkout` facade, are now proxied down to the underlying
checkout driver, a behavior well known in the Laravel framework.

To use the session driver in the checkout, set the `vanilo.checkout.store.driver` config to `session`:

```php
// config/vanilo.php
return [
    'checkout' => [
        'store' => [
            'driver' => 'session'
        ]
    ]
];
```

> See: https://vanilo.io/docs/3.x/checkout

## Other Improvements

- Added the `is_active` flag to shipping methods
- Added the `is_master_product()` template helper function
- Added the `Cart::fresh()` method to the Cart facade that reloads the underlying cart model from the database

> Detailed Changelog: https://vanilo.io/docs/3.x/releases#32
