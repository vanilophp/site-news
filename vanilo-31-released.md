---
title: Vanilo 3.1 Released
excerpt: Vanilo 3.1 has been released with Master Products, Adjustments and PHP 8.2 support. See what's new.
date: 2022-11-07
tags: [Releases, News, 'Vanilo 3']
featured: true
---
Vanilo 3.1 has been released with the long awaited master products feature, and the new adjustments module.

## Minimum Requirements

The requirements of Vanilo 3.1 are almost identical with v3.0. The minimum Laravel version is v9.2,
ie. v9.0 and v9.1 are no longer supported. Still, everyone is encouraged to update their project
to the latest (v9.38 as of writing) Laravel version as it adds many great features and improvements
to your application

## Breaking Changes

There are NO BREAKING CHANGES in this release. We stick to [Semantic Versioning](https://semver.org).

## Master Products

One of the top requested features has been the
[Product Variants](https://vanilo.io/docs/3.x/product-variants),
which has been around since v3.0, but the master product implementation
has just been added with v3.1.

See the [Master Products Documentation](https://vanilo.io/docs/3.x/master-products) for more details.

## Adjustments

Vanilo 3.1 has another brand-new module, the **Adjustments Module**.

The Adjustments concept is a generic, all-rounder that serves as a base for:

- Price discounts,
- Shipping fees,
- Tax handling,
- "Paying" with credits, coupons, etc.

Adjustments can be applied to any eloquent model, but typically they're applied
to the total price of an order/cart, or to an order/cart item or to an order’s shipment.

> For detailed description of the Module, see the [Adjustments Documentation](https://vanilo.io/docs/3.x/adjustments).

## Various Features

- The channel can be assigned to orders
- Channels are now `Sluggable`
- Shipping methods
- Added [Enum v4.0](https://vanilo.io/news/enum-v4-released) support

## Roadmap Changes

Up until the v3.1 release, Vanilo used to have versions with features scheduled ahead.
Frankly speaking, we rarely met those deadlines. As another undesired side effect,
the promise of those releases has also made additional features to be kept back,
thus slowing the entire release pace down.

As of v3.1 (Nov 7, 2022), the roadmap and the release policy have changed as follows:

- the roadmap no longer contains version numbers and release dates
- the roadmap contains the scheduled features in priority order
- the release frequency will be higher (new version every 2-3 weeks; similar to Laravel's cycles)
- releases will be smaller
- minor changes and improvements will be released faster

> If you have issues or questions regarding the Vanilo 3 upgrade, feel free to [open an issue at Github](https://github.com/vanilophp/framework/issues).
