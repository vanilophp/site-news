---
title: Vanilo 3.4 Released
excerpt: Vanilo 3.4 has been released with configurable cart & order items. See what's new.
date: 2023-01-25
tags: [Releases, News, 'Vanilo 3']
featured: true
---
Vanilo 3.4 has been released with first-party configurable product support for cart & order items.

## Configurable Items

Products that the user can customize are common in the E-commerce. Typical examples are:

- Burger with extra chilli and cheese,
- Mugs with custom text and picture,
- Event tickets with the attendees' names,

just to name a few.

The configuration is the property of the cart/order item and not the product itself, therefore
the configuration data has to be stored along with those items.

To store the configuration with a cart item use the following code:

```php
use Vanilo\Cart\Facades\Cart;

Cart::addItem($product1, 1, ['attributes' => ['configuration' => ['mug_text' => 'I love pizza']]]);
```

## Other Configurables

Besides the `CartItem` and `OrderItem` models, the following ones have also become configurable:

- `Carrier`,
- `Shipment`,
- `ShippingMethod`,
- `PaymentMethod`.

These models used to be configurable even in earlier versions of Vanilo, but with this release,
their configuration has been made standard and uniform.

## Find By SKU

With this release, both the `MasterProdcutVariant` and `Product` models have a static `findBySku($sku)` method.
    
