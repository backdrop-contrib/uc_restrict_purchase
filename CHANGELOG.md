# Changelog

## 1.x-1.0.0-beta3 (unreleased)

## 1.x-1.0.0-beta2 (2026-11-04)

Git tag: `1.x-1.0.0-beta2`.

### Added
- Items the user may no longer buy (restricted after adding, or role lost) are removed from the cart with a message.

## 1.x-1.0.0-beta1 (2026-11-03)

Git tag: `1.x-1.0.0-beta1`.

Port of the Drupal 7 module Ubercart Price Visibility (uc_price_visibility),
renamed because it restricts purchase, not just prices.

### Added
- Per-product roles allowed to buy the product; none ticked means anyone can.
- Message, or a button (label + link, returns to the product) with the message as help text.
- Option to show the button to anonymous users only.
- Add to cart refused for users without a role, covering cart links and Views buttons.
- Catalog and Views Add to cart / Buy it now buttons replaced too.
- Option to hide prices (display, sell, list) on the product page.

### Changed (from Drupal 7)
- Settings in config (`uc_restrict_purchase.settings`), roles by machine name.
- A product with no roles is unrestricted (Drupal 7: hidden from everyone).
- Message filtered with filter_xss_admin.
