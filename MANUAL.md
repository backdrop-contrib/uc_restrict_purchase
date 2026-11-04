# Restrict Purchase - manual

## On each product

*Product information* on the product's edit form has **Only these roles can
buy this product**. Users with any ticked role can buy it. Leave all
unticked to let anyone buy it. Saving the product with nothing ticked
removes the restriction.

Products saved by code (imports, bulk updates) keep their restriction
unless the code sets `$node->uc_restrict_purchase_roles`.

## Settings

*Store > Configuration > Products*, **Restrict purchase** tab:

| Setting | What it does |
|---|---|
| Roles ticked by default on new products | Pre-fills the roles on the add form for new products. Existing products are not changed. |
| Also hide the price | Hides the display, sell and list prices on the product page from users who cannot buy it. |
| Users who cannot buy the product see | **A message**, or **a button** with the message as help text below it. |
| Message | For example "Only full members can purchase these items." HTML is allowed. Also shown when an add to cart is refused. |
| Button label / Button link | For example "Log in to purchase" and `user/login`, or "Join" and your join page. A path on this site gets `?destination=` so the user returns to the product. Full URLs must start with http:// or https://. |
| Show the button to anonymous users only | On by default: a logged-in user without the role sees only the message (a login button is no use to them). Untick when the button leads to a join page. |
| On the product page, show the message or button in place of | Its position on the product page: the Add to cart button, the sell price or the display price. |

## Where it applies

- Product page: Add to cart (and the prices, if set) replaced.
- Catalog and Views "Add to cart" / "Buy it now" buttons: replaced by the
  message or button.
- Any add to cart (forms, `cart/add/...` links): refused with the message.
- The cart and checkout: an item the user can no longer buy (added before the
  product was restricted, or before the user lost the role, e.g. when a
  membership expires) is removed, with "<product> has been removed from your
  cart." and the message.

## Limits

- Prices shown in Views fields are not hidden.

## Styling

The block is a `div.uc-restrict-purchase` holding
`a.button.uc-restrict-purchase-button` and
`div.uc-restrict-purchase-message.description`.

## For developers

`uc_restrict_purchase_allowed($node, $account = NULL)` returns whether an
account (default: the current user) may buy a loaded product.
