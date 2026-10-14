# RIZQ — honey, nuts, mustard oil & gur (WhatsApp ordering)

Mobile-first shop for Bangladesh. Customers add items to the cart, fill in the checkout form, and a ready-made order message opens in WhatsApp. Cash on delivery.

## Files
```
index.html           the shop (all styling and logic inside)
admin.html           private admin panel (products, photos, stock)
firebase-config.js   your Firebase + Cloudinary keys (see ADMIN-SETUP.md)
```

## Settings (top of the `<script>` in index.html)
```js
var WA_NUMBER="8801903770516";   // country code, no +
var RATE={dhaka:70,outside:130}; // delivery charge
var FREE_OVER=1500;              // free delivery above this subtotal
```
Categories are the `CATS` list in index.html **and** in admin.html. Add a new one in both places (and `BN`/`ART` in index.html).

## Products
- Normal way: `admin.html` (setup in ADMIN-SETUP.md).
- Without admin: edit the `PRODUCTS` list in index.html. It is the fallback when Firebase is not set up. Use `stock:false` for “Notify me”.

## Deploy (GitHub Pages)
Upload the three files to the repo root, then **Settings → Pages → Deploy from branch → main / root**.

## Notes
- Orders arrive only as WhatsApp messages, so keep that chat as your order log.
- Stock does not reduce automatically; mark items out of stock in the admin panel.
- Keep the `admin.html` link private.
