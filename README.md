# New York Pizzeria & Restaurant of Lowville

Website for New York Pizzeria & Restaurant of Lowville. A minimal, no-scroll single-page site with menu, hours, and Stripe checkout.

## Live site

- **Custom domain:** [https://nypizza.marziale.tech](https://nypizza.marziale.tech)
- **GitHub Pages (fallback):** [https://marzialetech.github.io/nypizza/](https://marzialetech.github.io/nypizza/)

## Local development

Open `index.html` in a browser or serve with any static file server.

## Stripe checkout (test mode)

The Order page includes a full menu with add-to-cart and Stripe Checkout. To enable:

1. **Deploy the API worker** (see `api/DEPLOYMENT.md`):
   ```bash
   cd api && npm install && npx wrangler secret put STRIPE_SECRET_KEY
   ```
   Use your Stripe test key (`sk_test_...`) from [dashboard.stripe.com](https://dashboard.stripe.com/test/apikeys).

2. **Deploy the worker:**
   ```bash
   npm run deploy
   ```

3. **Configure the API URL** in `index.html` if using a custom domain (default: `nypizza-api.marziale.tech`).

4. **Local testing:** Run `npm run dev` in the `api` folder. The frontend auto-uses `localhost:8787` when opened from localhost.

**Note:** Chicken Wings are not in the order menu (call for pricing). All other menu items are available.
