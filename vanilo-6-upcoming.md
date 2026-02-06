---
title: Vanilo 6.0 - Development Started
excerpt: What to expect in Vanilo 6, and when.
date: 2026-02-06
tags: [Releases, News, 'Vanilo 6']
featured: true
---

On the 5th of February 2026, the development of Vanilo 6 has started.

Vanilo 6.0 will be released **within a few weeks after the Laravel 13** release, which is officially **Q1 2026**.
We expect that Laravel 13 will come out in February 2026, which means Vanilo 6 is expected to be released in February - March 2026.

Vanilo 6 is a major version, and it will contain **breaking changes**.

## Preface

This release will pack several features and logical, structural changes.

## Laravel 12 & 13 Support

It will support Laravel 12 & 13, PHP 8.4 and 8.5.

## Non-Product Line Items

Currently, cart/order items can only represent buyables, i.e. products.

Shipping, other fees and taxes are being handled as adjustments.

However, this makes tax calculation on shipping fees impossible.
Vanilo 6 will introduce a `type` field for cart/order items, which will allow for non-product items, like:

- Shipping fees (with tax handling support);
- Handling/packaging/gift wrap fees;
- Environmental/recycling fees (e.g., electronics, batteries, tires);
- Bottle/container deposits;
- Tips, service gratuities;
- Charity, donation.

The adjustment-based approach will remain in a backwards-compatible way, and it will be up to you to
opt-in to the new approach.

The non-product items will be capable of being taxed, individually discounted, tied to other items, and included in the order total.

## Payments

The Vanilo Payment module was originally designed for offsite payments, but many of the gateways are now rather working
in an API fashion. The transition to this is already underway with the "experimental" `TransactionHandler` interface.

This release will add more support for API-based payment gateways.

## Possible Changes on the Radar - Still TBD

There are several changes in our backlog, that will be **possibly** included in Vanilo 6, but they are not definitive yet:

- Using the `ShipTo` interface instead of the shipping address model - it adds more data points and is an extension of the `Customer` interface
- The order factory works, but it's a mess - a possible cleanup is planned.
- Improving the Order's total vs. payable amount. Eg. when we have a 100% giftcard adjustment, then the total is X, but the payable is 0.
- Configuration schema improvements
- A possible introduction of an `Identifiable` interface. Structurally would make sense, on the other hand it is an intrusion into the Laravel Framework's domain, since we're using Eloquent models most of the time.
