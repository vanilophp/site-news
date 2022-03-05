---
title: Vanilo 3.0 Released
excerpt: Vanilo 3.0 has been released with Shipments, Variants and many other features. See what's new.
date: 2022-03-05
tags: [Releases, News, 'Vanilo 3']
---
Vanilo 3.0 has been released with the following features:

To be written shortly. Testing for now.

![product variant links](img/_variant_links.png)

```php
Establish::a('variant')->link()
    ->basedOn('color') // The slug of the property
    ->between($iphone13Mem128GColorBlue)
    ->and($iphone13Mem128GColorRed, $iphone13Mem128GColorBlack, $iphone13Mem128GColorWhite);
```
