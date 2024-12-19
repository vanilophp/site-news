---
title: Vanilo 3.7 Released
excerpt: Vanilo 3.7 has shipped with the Tax module, adjustable order & cart items, a series of new domain events, and the fresh `ProductSearch` class. See what's new.
date: 2023-04-07
tags: [Releases, News, 'Vanilo 3']
featured: false
---

Vanilo v3.7 brings more ways to manage your orders, items, and taxes while offering better customization hooks,
smarter search, richer shipment details, and stronger compatibility with modern SQL setups.

## The New Tax Module

Vanilo 3.7 introduced the dedicated Tax module which has Tax Categories and Tax Rates and a `SimpleTax` adjuster for
straightforward percentage-based tax calculations. You can now assign a `tax_category_id` directly to products,
master products, and variants.

The `DetailedAmount` DTO now includes `fromKeyValuePairs` and `getDetail()` methods, offering clearer insights into how
prices, taxes, and adjustments add up.

### Adjustable Items in Cart & Order

Foundation's cart and order items are now adjustable, playing nicely with the new tax calculations
(and other custom adjustments) to keep totals accurate and flexible.

## Order & Item Enhancements

- **OrderProcessingStarted** Event: monitor order lifecycle events more precisely.
- **New Order Item Events**: Get notified about shipping, pickup readiness, and more via `OrderItemShipped`, `OrderItemPickedUp`, `OrderItemsIsReadyForDelivery`, `OrderItemsIsReadyForPickup`, and `OrderItemHasBeenPutOnHold`.

### Hook Into Order Creation with Custom Logic

We've made `OrderFactory::callHook` protected, so extending or customizing order creation is easier than before.
Optional hooks for order item creation now let you add custom logic at just the right moment.

## Fulfillment & Delivery

The `shipments` table now has the `carrier_cost`, `label_url`, and `label_base64` fields. You can link shipments to
order items (and vice versa) for more granular control over fulfillment.

It's all about fine-tuning the shipping process in a flexible, data-rich way.

## Product Search Evolution

We've introduced an experimental `ProductSearch` to eventually replace `ProductFinder`. This new class can handle both
product and master product searches. Plus, it comes with a helper to fetch products by slug effortlessly
- `findBySlugOrFail()` - and includes a static `findBySlug()` method for more flexible querying.

## Compatibility & Other Noteworthy Updates

- **MySQL 8.0 Testing**: Vanilo now officially tests against MySQL 8.0, alongside the old faithful MySQL 5.7.
- **Payment Requests**: A `getRemoteId` method has been added to `NullRequest` to line up with a future `PaymentRequest` interface version.
- **Admin Panel Changes**: Emission of the new `OrderProcessingStarted` event from the admin panel and a fix for linking master products on the order item list improve both functionality and UX.
- The `is_master_product_variant()` Helper: Quickly check if a given object is a master product variant.
