# WMScosmetics — Lucky Heart Cosmetics warehouse prototype

Lucky Heart Cosmetics-branded, responsive browser-based prototype for a **single-site cosmetics and chemical blending warehouse**. Visual branding is based on the owner-supplied logo and [Lucky Heart's website](https://luckyheart.com/).

## Demo features
- Dashboard for available raw stock, lots, manufacturing batches, and QA holds
- Raw material search by ingredient, SKU, supplier lot, or physical bin location
- Material receiving with quantity, supplier lot, expiry, bin and quarantine/released state
- Material picking that deducts quantities from a selected released lot
- Standard formulations and custom recipe creation with **percent-by-mass** validation
- Draft approval workflow and revision snapshot at manufacturing time
- Batch production: scales formula to target kilograms, allocates released ingredients FEFO by expiry, deducts stock and creates a finished batch in QA hold
- Manual material and finished-goods QA release actions
- Local activity ledger and demo reset

## Run locally
No Node.js or dependencies needed.
Serve the repository root over HTTP:
\`\`\`sh
python3 -m http.server 8000
\`\`\`
Then open http://localhost:8000.

## Deploy
The project is a static website. A Vercel project may deploy the repository root with **Framework Preset: Other**, no build command, and output directory set to the repository root.

## Important prototype boundaries
This app is a **demo only**. All example product names, recipes, lots and quantities are fictional. Data is saved solely in browser localStorage, per device/browser. It has no server database, cross-user synchronization, authentication, role enforcement, tamper-evident audit trail, safety verification, or ERPNext backend. No production inventory or proprietary chemical formulas should be entered into this public demo.

Demo formula approval and QA release are not identity-verified. Do not use the demo to control actual chemical storage, production, or shipment.

## ERPNext integration plan
Build a dedicated Frappe app with:
1. Ingredient/item master with CAS/INCI/SDS/COA references and container/lot tracking.
2. ERPNext Purchase Receipt + batch capture + quarantine/putaway workflow.
3. Warehouse location lookup and barcode-confirmed pick/transfer transactions.
4. Controlled formulation DocType with revision and approval workflow; approved BOM + Work Order generation.
5. Batch Production Record with measured actual quantities, lot genealogy, balance reconciliation and process details.
6. Quality Inspection + guarded release for incoming materials and manufactured lots.
7. ERPNext stock ledger as the **single authoritative source of truth**.

In production, stock deductions must be atomic, server-authorized transactions with concurrent inventory safeguards, not browser storage updates.

## Brand assets
The optimized Lucky Heart clover logo is stored at `assets/lucky-heart-logo.webp` and used in the sidebar, dashboard header and favicon.

## Project files
- \`index.html\` — page shell and application navigation
- \`styles.css\` — responsive UI system
- \`app.js\` — browser-based demo workflows and local storage
- \`vercel.json\` — static deployment configuration

Code license: none declared yet. Contact repository owner for reuse terms.
