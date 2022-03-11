---
title: Enum 4.0 Released
excerpt: The Enum component received a major upgrade that contains a breaking change. You may need to stick with version 3.
date: 2022-03-11
tags: [Releases, News, 'Konekt Components']
---
Enum 4.0 has been released on the 10th of March 2022.

At the moment of writing, Vanilo 3.0 is not supporting Enum v4, but most
likely the upcoming v3.1 release will allow using v4 enums as well.

It is important to note, that it is **NOT necessary to upgrade** to Enum v4,
and **Vanilo will keep supporting v3 Enums** for good.

Unless you're a strict type absolutist, or you're having issues with your numeric
Enums, there is no need to upgrade to V4. However if you would like to, here's a
list of things to consider about it.

Enum v4 contains some housekeeping changes like dropping support for older PHP versions,
and one significant change: **All the values of the enums are now strictly typed.**

Since enums typically have string values, the upgrade won't break things, for the
vast majority of the cases.

## Numeric Enums

**If you use numeric enum values** you must pay attention to initialize them using
variables of the actual type.

In PHP `0 == null` is true. You must do a strict comparison (===) to distinguish between `0` and `null`:

```php
0 == null
//=> true
0 === null
//=> false
```

Enum 3.0 and earlier did a loose comparison at checking the values.
As a consequence, when there was an enum with both NULL and 0 values,
the `0` value did NOT work:

```php
class Flag extends \Konekt\Enum\Enum {
    const NONE = null;
    const YES = 1;
    const NO = 0;
}

// Enum v3 and below:
Flag::create(0)->value()
// => null

// Enum v4:
Flag::create(0)->value()
// => 0
```

This can be considered a bug, but the entire Enum is now doing a strict type checking,
therefore v4 introduces fundamental behavior change.

### String Not Equals Integer

Having such an enum in v4:

```php
class OrderStatus extends \Konekt\Enum\Enum {
    public const ORDERED = 1;
    public const SHIPPED = 2;
    public const CANCELLED = -1;
}
```

Can't be created like that:

```php
$shipped = new OrderStatus("1");
// throws UnexpectedValueException in v4
```

Due to the loose checking, it worked in v3 without problems, but throws an Exception in v4.

Therefore, when creating numeric enums from database, form requests, etc.
you must pay attention to converting the values to integers. Eg.:

```php
public function createOrderAction(Request $request) { 
    $order = new Order();
    $order->status = OrderStatus::create(intval($request->status));
    $order->save();
}
```

## PHP 8.0

The minimum requirement of Enum v4 is PHP 8.0

> For the complete upgrade guide read the [Enum's Upgrade Documentation](https://konekt.dev/enum/4.x/upgrade#from-v3-to-v4).
