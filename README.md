# Waqar Accounting V5 Cloud

V5 keeps the V4 accounting/inventory experience and adds a cloud-ready architecture:

- Supabase email/password authentication
- Workspace + Admin/role model
- Cloud JSON data sync for the existing accounting database
- Users & Roles screen
- Theme color settings
- Local fallback when cloud is not configured
- Existing customers, suppliers, products, inventory, sales, purchases, expenses, invoices, accounts, ledger and reports remain available

## 1. Run locally first
Open `index.html`. It works in Local Mode without Supabase. The browser will load the Supabase client from jsDelivr when an internet connection is available, but no cloud credentials are required for Local Mode.

## 2. Enable cloud
1. Create a Supabase project.
2. Open Supabase SQL Editor.
3. Run **supabase-schema.sql** completely.
4. In Supabase Authentication, enable Email/Password.
5. Get the Project URL and **Publishable Key** from the project's Connect/API Keys area.
6. Open V5 → Cloud Setup and enter those two values.
7. The app reloads and shows the Login screen.
8. Create the first account. V5 creates a workspace and makes that first account Admin.

Supabase's current browser client is `@supabase/supabase-js` v2 via CDN. Use a publishable key in browser code; do not expose a secret/service-role key. Row Level Security is enabled by the supplied schema.

## 3. Adding users
Create additional accounts in Supabase Authentication. When a user signs in, their profile is created. The workspace membership/role can then be managed from V5 → Users & Roles after the membership is added to the workspace. For production, use a small server-side/Edge Function invitation flow rather than putting an admin secret in the browser.

## Important
This package is **cloud-ready**, not a hosted SaaS by itself. A real cloud deployment still needs a Supabase project and a web host such as GitHub Pages, Cloudflare Pages, Netlify or Vercel. The browser app never contains a Supabase secret key.
