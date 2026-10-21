# MHAC Delivery — New Build Starter

A clean-slate starter for the new MHAC Delivery website. The old live website is not modified.

## Included
- `customer.html` — modern customer storefront with food-photo cards, cart, and checkout UI.
- `admin.html` — menu editor for stores, categories, foods, prices, choices, and photo URLs.
- `rider.html` — rider order workflow UI.
- `assets/app.css` — responsive white/red app styling.
- `assets/firebase-config.js` — Firebase config placeholder.
- `assets/app.js` — Firebase bootstrap and shared helpers.

## Before connecting Firebase
1. Create a **new** Firebase project.
2. Enable Authentication (Email/Password or Google, according to the final sign-in design).
3. Create a Firestore database and Firebase Storage.
4. Put the new project's web app config into `assets/firebase-config.js`.
5. Configure authorized domains for the new hosting domain.
6. Review and deploy the Firestore rules in `firestore.rules` only after testing.

## Important
This is a starting scaffold, not a finished production migration. It does not connect to the old Firebase project and does not contain the old menu or prices. The new order workflow, GPS/distance fees, chat, payment verification, and notification/background behavior must be implemented and tested before launch.

## Menu data model (proposed)
`settings/menu`:
```json
{
  "stores": [
    {
      "id": "store-id",
      "name": "Store name",
      "logoUrl": "",
      "published": true,
      "categories": [
        {
          "id": "category-id",
          "name": "Category",
          "foods": [
            {
              "id": "food-id",
              "name": "Food name",
              "price": 0,
              "photoUrl": "",
              "available": true,
              "choices": []
            }
          ]
        }
      ]
    }
  ]
}
```

Use `photoUrl` for the chosen image. Store food images in the new Firebase Storage bucket or use image URLs that you have permission to use. Photo search must be confirmed by the admin; search results can be mismatched or have usage restrictions.
