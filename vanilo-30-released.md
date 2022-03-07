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
will be released with 3.1, in March 2022.

## Links Module

to be written

```php
Establish::a('variant')->link()
    ->basedOn('color') // The slug of the property
    ->between($iphone13Mem128GColorBlue)
    ->and($iphone13Mem128GColorRed, $iphone13Mem128GColorBlack, $iphone13Mem128GColorWhite);
```
