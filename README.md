# Kalenski™ | The ONE AND ONLY Card Empire®

Premium single-seller Yu-Gi-Oh! card marketplace. React + Vite, desktop-only, black & gold glassmorphism theme.

## Setup

```bash
npm install
npm run dev
```

Open the printed local URL (usually http://localhost:5173).

## Logging in

There are no passwords. Enter any username to create an account (role `Customer`).
Enter **`Kalenski`** as the username to log in as the platform admin (role `ADMIN`) — this account is seeded automatically on first run.

## What's implemented

- **Marketplace**: search, category filter, condition filter, sorting (newest/oldest/price/alphabetical), wishlist, out-of-stock hiding, card detail modal.
- **Cart & Checkout**: quantity editing, order placement, stock deduction on acceptance.
- **Accounts**: username-only auth, roles (`Customer`, `Stammkunde`, `VIP`, `POTM`, `ADMIN`), avatar/theme/privacy/notification settings.
- **Orders**: full status workflow (New Order → Accepted/Declined → In Progress → Completed → Archived) with status history.
- **Private chat**: auto-created when an order is accepted, linked to the order, live messages, timestamps, archiving.
- **Reviews**: post-completion 1–5 star review with comment; average rating and review list.
- **Events**: admin creates events (title, prize, rules, date), customers join, admin picks a winner.
- **Notifications**: order accepted/declined, new chat message, review request, low stock, out of stock, new event — with an in-header bell and unread counter.
- **Admin panel**: card CRUD, order management, chat access, event management, and a statistics dashboard (customers, cards listed/sold, revenue, open/completed orders, most popular cards, average rating).

## Data layer

Everything currently persists to `localStorage` (see `src/context/AppContext.jsx`), organized as clearly separated resources (`users`, `cards`, `orders`, `chats`, `reviews`, `events`, `notifications`, `carts`) so it can be swapped for Supabase/Firebase/MySQL later without touching the UI layer — every component only talks to the `useApp()` context, never to `localStorage` directly.

## Notes / next steps

- Image URLs are plain strings today (seeded with placeholder card art) — wire up real upload/storage when moving off `localStorage`.
- The chat and notifications system is fully local-first; swapping in a real backend would mean replacing the `AppContext` persistence calls with API calls, and the rest of the app is unaffected.
