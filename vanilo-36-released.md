---
title: Vanilo 3.6 Released
excerpt: Vanilo 3.6 has been released with Laravel 10 support and tons features. See what's new.
date: 2023-03-07
tags: [Releases, News, 'Vanilo 3']
featured: true
---
Vanilo 3.6 has been released with Laravel 10 support, new checkout, order and adjustment features. 

## Laravel 10

Beginning with v3.6, Vanilo supports both Laravel 9 and Laravel 10.

## New Domain Events

The following new events have been added:

- `CartCreated`,
- `CartUpdated`,
- `CartDeleted`,
- `CartDeleting`,
- `ShippingMethodSelected` (on checkout)

## Checkout & Shipping Improvements

### Zone Support

Added Zone support to shipping methods. It means that shipping methods can be optionally restricted to
[geographic zones](https://konekt.dev/address/2.x/zones).

If the `zone_id` field is NULL, it means that the shipping method is unrestricted, and is available
in every geographic zone:

```php
$shippingMethod->zone_id;
// NULL
$shippingMethod->isNotZoneRestricted();
// true
```

If a shipping method is zone restricted, then it has a [Zone](https://konekt.dev/address/2.x/zones#matching-zones):

```php
if ($shippingMethod->isZoneRestricted())
{
    if (!$shippingMethod->zone->isCountryPartOfIt('UK')) {
        // reject the checkout
    }
}
```

To simplify finding available shipping methods for areas, the `ShippingMethod::forZone($singleZone)` and the
`ShippingMethod::forZones($multipleZones)` query scopes have been added.

It can be used to retrieve the available shipping methods for a country:

```php
$netherlandZones = Zones::withShippingScope()->theCountryBelongsTo('NL');
$availableShippingMethodsForNetherland = match($netherlandZones->isEmpty()) {
    true => ShippingMethod::whereNull('zone_id')->get(),
    false => ShippingMethod::where(fn ($query) => $query->forZones($netherlandZones)->orWhereNull('zone_id'),
};
```

> For detailed usage of zones see the [Zones Documentation](https://konekt.dev/address/2.x/zones)

### Shipping Fee Calculation

Shipping Fee calculator support has been added. The Foundation module contains the `flat fee` calculator, but you
can implement your own ones by implementing the `ShippingFeeCalculator` interface and registering the calculator:

```php
ShippingFeeCalculators::register('canada_post', CanadaPostShippingFeeCalculator::class);
```

Additionally, a listener has been added to the Foundation, that calculates the shipping fee on checkout shipping method change.

Added the `shippingAdjustmentsTotal()`, `taxAdjustmentsTotal()` and `promotionAdjustmentsTotal()` methods to the
Adjustable Cart model in foundation.

### Checkout Extensions

The following fields are now regular fields of the checkout:

- `shipping_method_id`
- `payment_method_id`
- `ship_to_billing_address`
- `notes`

The `vanilo.checkout.default.weight_unit` config key has been added, which defaults to 'kg'.

The following methods have been added to the Checkout implementations:

- `getShipToBillingAddress()`
- `setShipToBillingAddress()`
- `getShippingMethodId()`
- `setShippingMethodId()`
- `getPaymentMethodId()`
- `setPaymentMethodId()`
- `getShippingAmount()`
- `setShippingAmount()`
- `getTaxesAmount()`
- `setTaxesAmount()`
- `getNotes()`
- `setNotes()`

## Status Extensions

The order status enum has been extended with the `processing` value, and the fulfillment status
got the new `ready_for_pickup` value. 

## New Order Features

It is possible to hook into the OrderFactory creation, by passing callable(s) to the createFromDataArray method:

```php
class B2BOrderFactory extends OrderFactory
{
    public function createFromB2BOrderRequest(Request $request): Order
    {
        return $this->createFromDataArray(
            $request->input('order'),
            $request->input('items'),
            \Closure::fromCallable([$this, 'myOrderHook'])
        );    
    }
    
    protected function myOrderHook(Order $order, array $data, array $items): void
    {
        // This method gets called once all the order data is prepared but before
        // the order gets saved into the database. Here you can manipulate the
        // order object, and also access the source $data and $items arrays    
    }
}
```

The `payable_remote_id` field (along with getter/setter methods) has been added to the Foundation Order model.
