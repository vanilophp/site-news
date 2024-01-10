---
title: Vanilo 3.5 Released
excerpt: Vanilo 3.5 has been released with shipping and fulfillment features. See what's new.
date: 2023-02-23
tags: [Releases, News, 'Vanilo 3']
featured: false
---
Vanilo 3.5 has been released with Shippable and Fulfillment features.

## Fulfillment Status

Orders have a generic status like pending, processing, canceled, completed, but in reality,
the lifecycle of an order has more details. The payment status of an order is being tracked
by the payment(s) assigned to an order.

In e-commerce, **"fulfillment"** refers to the entire process of receiving, processing, packing,
and shipping orders to customers. In Vanilo 3.5, the `FulfillmentStatus` has been added to be able
to track this process.

It's important to note each order item can have its very own fulfillment status in case of partial deliveries.

Therefore, the most important difference between the order and the fulfillment status is that the `OrderStatus`
applies to a single order, whereas the `FulfillmentStatus` applies both to an order **AND** to all of its items
separately.

Depending on your requirements you may or may not want to apply fulfillment status to items, but beginning with
Vanilo 3.5, this is possible.

These are the available fulfillment statuses:

- `scheduled`: Typically used by subscription orders that have a scheduled status until the fulfillment date is reached.
- `unfulfilled`: A fresh order/item is unfulfilled by **default**.
- `on_hold`: An item is on hold when there's a reservation but the transaction has not been confirmed/paid yet. Processing should not begin until the order/transaction is confirmed.     */
- `awaiting`: The item has been picked, processed, and packaged, and is ready for delivery. It needs a pickup by the delivery personnel
- `partially_fulfilled`: Only some parts of the subject have been handed over to a delivery personnel
- `ready_for_pickup`: The item has been prepared and can be picked up from the specified location _(added in v3.6)_ 
- `fulfilled`: The item has been handed over to a delivery personnel

## Shipping Features

Added the `reference_number` field to the Shipment model, that is typically used by logistics companies before a shipment
gets a tracking number from the last mile carrier.

Vanilo 3.5 contains the `Shippable` many-to-many, polymorphic relationship. It allows all the following scenarios:

- shipping one order in one shipment
- shipping one order in multiple shipments
- shipping multiple orders in one shipment

To support these modes, the `Shipment::orders` and `Order::shipments` Collection properties have been added to their
respective Foundation models.
