# Business Management Suite

A database-backed Next.js/TypeScript business management application for invoices, purchases, inventory, customers, suppliers, payments, expenses, taxes, receivables, payables, reporting, PDF invoices, WhatsApp sharing, roles, permissions and audit history.

## Run

```bash
npm install
npx prisma generate
npx prisma db push
npm run db:seed
npm run dev
```

Default demo user seed: `admin@example.com` / `admin123`.

## Architecture

- Next.js App Router API routes implement CRUD under `/api/:resource` and `/api/:resource/:id`.
- Prisma models define relational business data with preserved transaction snapshots.
- Business workflows in `lib/business.ts` use transactions for invoices, purchases, stock movements, payment recalculation and audit logs.
- PDF invoice generation is available at `/api/invoices/:id/pdf`.
- WhatsApp sharing workflow is available at `/api/invoices/:id/whatsapp` and records communication history.
- Reports are dynamically calculated from database records at `/api/reports/:type`.
