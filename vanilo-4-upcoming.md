---
title: Vanilo 4.0 - When? What?
excerpt: A look at what's coming to Vanilo 4. And when.
date: 2024-01-10
tags: [Releases, News, 'Vanilo 4']
featured: true
---

> Vanilo 4 is not yet final, the list of features below may change!

Vanilo 4.0 will be released **shortly after the Laravel 11** release, which is officially **Q1 2024**,
[some sources claim](https://benjamincrozat.com/laravel-11) that it is _February 6th, 2024_.

We also expect that Laravel 11 will come out in February 2024, which means Vanilo 4 is expected to be released in February 2024.

Vanilo 4 is a major version and will contain breaking changes.

## Preface

Vanilo 4 was originally scheduled for 2023, but we ended up adding [Laravel 10 support](/news/vanilo-36-released)
and tons of features to the Vanilo 3.x series.

Basically, the life span of Vanilo 3 has been extended, and most of the Vanilo 4 features were added to
[v3.5 ](/news/vanilo-35-released), [v3.6](/news/vanilo-36-released) and [v3.7](/news/vanilo-37-released)
but **without any breaking changes**.

The last v3 release (as of writing) is 3.8.2, which supports Laravel 9-10 and PHP 8.0 - 8.3 versions.

## Behind the Scenes

On the 24th May, 2023 (right after releasing v3.8.0) the work on Vanilo 4 has started.

Our Saas offering, [Vanilo Cloud](https://vanilo.cloud) has been running on Vanilo 4 since June 2023, which means
that Vanilo 4 is battle tested and production ready from the beginning.

## Laravel 11 Support

Vanilo 4 will support Laravel 11, and _most probably_ Laravel 10. Why "most probably"?
Because Laravel 11 is not yet final, and we can't yet tell if there will be any breaking changes in Laravel 11
that would heavily affect Vanilo.

Especially the upcoming `$casts` -> `casts()` changes of Eloquent models can cause surprises if Laravel decides to
drop the old way (based on the `$casts` property) of defining attribute casts. So far, Vanilo 4 dev versions work well
with Laravel 11 dev versions.

If we'll have to decide whether Vanilo 4 should be compatible Laravel 10 or with Laravel 11, and there will be no easy
way to support both, then we'll opt for Laravel 11 and drop Laravel 10 support.

But, our aim is to support both Laravel 10 and 11 if possible.

## Breaking Changes

V4 contains quite several breaking changes, and the discarding of deprecated features.

First of all, Vanilo 4 is PHP 8.2+ and Laravel 10+ only.

Most of the breaking changes are related to the interfaces. Argument and return types have been added where
it was missing, and new methods have been added.

The `Framework` namespace aliases for Vanilo v2 compatibility have been deleted.

The minimum Enum version is now v4.1.

The list of all breaking changes will be added to the upcoming upgrade guide of Vanilo 4.

## New Features

- Orders and channels now have a `currency` field
- The `payment_method_id` can now be explicitly saved for the order (earlier, it could be obtained via `$order->payments->first()->payment_method_id`)
- Added the `Channelable` behavior to Foundation Product, MasterProduct, PaymentMethod, ShippingMethod and Taxonomy classes
- The ProductSearch class now has `withImages`, `withChannels` methods
- Added the `Stockable` interface, and it is implemented by the `Product` and `MasterProductVariant` models
- Added `isZoneRestricted()` & `isNotZoneRestricted()` helper methods to the `ShippingMethod` class
