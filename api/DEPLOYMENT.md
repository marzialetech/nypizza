# NY Pizza API (Stripe Checkout) - Deployment

## Prerequisites

- [Stripe account](https://dashboard.stripe.com) (test mode for development)
- [Cloudflare account](https://dash.cloudflare.com)
- Node.js 18+

## Setup

1. **Install dependencies**
   ```bash
   cd api && npm install
   ```

2. **Set Stripe secret key** (test mode)
   ```bash
   npx wrangler secret put STRIPE_SECRET_KEY
   ```
   Use your test key: `sk_test_...` from [Stripe Dashboard → Developers → API keys](https://dashboard.stripe.com/test/apikeys)

3. **Deploy**
   ```bash
   npm run deploy
   ```

4. **Configure CORS** (optional)  
   Edit `wrangler.toml` and set `CORS_ORIGIN` to your site URL (e.g. `https://nypizza.marziale.tech`). For local dev, you may need to use `*` or add your dev URL.

## Custom domain

To use `api.nypizza.marziale.tech`:

1. Deploy the worker
2. In Cloudflare Dashboard → Workers & Pages → nypizza-api → Settings → Domains & Routes
3. Add custom domain: `api.nypizza.marziale.tech`
4. Add DNS CNAME: `api.nypizza.marziale.tech` → `nypizza-api.<your-subdomain>.workers.dev`

Then update `API_BASE` in `index.html` to `https://api.nypizza.marziale.tech`.

## Local development

```bash
npm run dev
```

The worker runs at `http://localhost:8787`. Update `API_BASE` in index.html to `http://localhost:8787` when testing locally (or use a config that switches based on hostname).
