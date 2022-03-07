---
title: Vanilo 3.0 Released
excerpt: Vanilo 3.0 has been released with Shipments, Variants and many other features. See what's new.
date: 2022-02-28
tags: [Releases, News, 'Vanilo 3']
featured: true
---
Vanilo 3.0 has been released with many changes, including breaking ones.

## Minimum Requirements

Vanilo supported many different versions of PHP and Laravel beginning with PHP 7.0 and Laravel 5.5.

Being constrained by the compatibilities of these dependencies, the codebase has an increased
complexity and it can only rely on the features present in the lowest supported version.

Fortunately, Laravel has changed its release policy and major versions, thus breaking changes are less frequent.
Vanilo being a Laravel plugin will now align its releases with Laravel major releases.

It means that Vanilo 3 is the counterpart of Laravel 9, ie. it only supports Laravel 9 and no earlier
Laravel versions. As a consequence it has the same dependencies, including PHP: 8.0 - 8.1.

## Monorepo

Vanilo has been both a set of independent components (cart, products, orders, etc) and
a framework that glues those components together into a unified E-commerce system.

When we began Vanilo, every module went into a separate repository and the framework
required them as external composer dependencies. During the years, it turned out to
be very ineffective for us to maintain the code spread into many repositories, slowing
down the progress and putting more cognitive load on the people.

Beginning with Vanilo 3.0, we have moved every component into the framework. The
standalone modules are still available at the very same locations, but technically
they have become the read-only subtree split of the main repository.

This is very similar to Laravel's individual components like [illuminate/support](https://github.com/illuminate/support)
or [illuminate/auth](https://github.com/illuminate/auth).

This change possibly doesn't affect your application, still it was a
significant internal change. We already saw the benefits of it during
the works of Vanilo 3.0

## Admin Has Been Removed

We learned during the years, that many of the application using Vanilo were not
using its own admin. Still being present required extra steps and caused extra
code loaded. Therefore in Vanilo 3.0 the admin package has been removed from
Vanilo Core (the framework) and it is available as a separate composer package: `vanilo/admin`.

## Product Variants

The top most wanted feature has been **Product Variants**
[for years](https://github.com/vanilophp/framework/issues/62). The topic is
quite complex and there are two major approaches of the implementation.

The Vanilo 3 Documentation has been extended with a
[Product Variants section](https://vanilo.io/docs/3.x/product-variants),
explaining the details of this topic.

Vanilo will support both product variant "schools" via:

- the [Links Module](https://vanilo.io/docs/3.x/links), and
- the [Master Products Module](https://vanilo.io/docs/3.x/master-products).

The Links module is part of the 3.0 release, whereas the Master Products module
will only be released with 3.1, in March 2022.

> For detailed description of the Links Module, see the [Links Documentation](https://vanilo.io/docs/3.x/links).

## Shipments

Vanilo 3.0 has another brand-new module, the **Shipment Module**.

As of v3.0 the module supports the handling of shipments. Each `Shipment` can have a 
`Carrier` assigned. Carriers have name and configuration attributes, and can be set inactive.

Besides the carrier, shipments have tracking number, a shipping [address](https://vanilo.io/docs/3.x/addresses),
a status enum, comment, configuration, dimensions and weight and can be marked as trackable/non-trackable.

The handling of shipping fees is handled by the upcoming
[Adjustments](https://vanilo.io/docs/3.x/adjustments) module. 

> For detailed description of the Shipment Module, see the [Shipping Documentation](https://vanilo.io/docs/3.x/shipping).

## New Product Features

The base product model has several new fields (all of them are optional):

- `original_price`: for very simple promotions,
- Dimensions: `width`, `height` and `length`, and
- `weight`.

## Breaking Changes

The most important difference is that the `Vanilo\Framework` namespace
has been renamed to `Vanilo\Foundation`.

In order to maintain the compatibility with existing codebases, a namespace
alias has been created. This alias will be removed in Vanilo 4.

As a consequence of the namespace change, the corresponding `vanilo.framework.*`
config values have been renamed to `vanilo.foundation.*.`.

Apart from these changes, the `Buyable` and the `Property` interfaces have changed.

> For a complete list of BCs and upgrade instructions see the [Upgrade Guide](https://vanilo.io/docs/3.x/upgrade)

If you have issues or questions regarding the Vanilo 3 upgrade, feel free to [open an issue at Github](https://github.com/vanilophp/framework/issues).

Wish you all a smooth upgrade! 🎉
