# 💜 Finance-Buddy
### Budgeting app with an approval-gated emergency fund and mandatory bill submission.

A personal finance web app that enforces strict rule for money management instead of just suggesting it. A user's monthly income is automatically divided in buckets like Daily expenses, Savings, Emergency funds or any other saving specified for any expense in future(Buying laptop, Buying car) according to the plan accepted by user from multiple suggestion given by AI Financial Assistant after analyzing pocket money or salary of user. The Daily expenses bucket is freely spendable, but the emergency fund and savings is locked: it can be accessed after permission of parent, the user raises a request stating the amount, category, and reason. Their manager/parent reviews and approves or rejects it, and funds are released only on approval. The user must then upload a bill or receipt as proof, and any unspent amount is flagged for return before the request can be closed.

The funds being saved for specific item or event aren't permitted to withdraw till the completion of target set i.e. only the full amount needed for particular item can be withdrawable after saving it completely, user can't spend that fund before reaching the decided saving amount. 

In India this is a common mistake made by 70% of people that they only start savings only after they get job, suffers a financial burden after emergency or after the burden of responsibilities. By making this platform we want our youth to be aware of money managing. It helps students and teenagers to start saving money from an early age with their parents have an eye on their expenses.

The goal is to solve a common problem with budgeting apps — that the emergency fund is the first thing people raid for non-emergencies. By adding a human approval step and a proof-of-spend requirement, the money stays reserved for what it was meant for.

---

## ✨ Features

- **Automatic 3-way allocation** — every deposit a parent funds is split 50% Everyday / 20% Emergency / 30% Savings
- **Approval-gated withdrawals** — children submit an amount + reason; parents approve or reject before funds move
- **Proof-of-spend loop** — approved requests expect a bill/receipt upload, with unspent balances flagged for return
- **Role-based accounts** — Parent and Child roles with separate views and permissions
- **Token-based sessions** — signed, expiring auth tokens (HMAC), no third-party auth service required
- **Persistent storage** — data survives restarts via a local SQLite database
- **Zero external dependencies** — runs on Node's built-in `http` and `node:sqlite` modules only
- **Full family experience** — dashboard, kids wallet, chores & allowance, savings goals, family activity/ledger, AI Financial Academy, and an Emergency Vault

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Runtime | Node.js 22.5+ (uses built-in `node:sqlite`) |
| Server | Native `node:http` — no Express, no framework |
| Database | SQLite (file-based, auto-created at `data/finance-buddy.sqlite`) |
| Auth | Custom HMAC-signed session tokens + `scrypt` password hashing |
| Frontend | Static HTML/CSS + `client.js` for API integration |
| Config | `.env.example` documents supported environment variables |

This project deliberately avoids external npm packages — everything needed (HTTP server, database, hashing, sessions) ships in Node.js itself.

---

## 📂 Project Structure

```
FinanceBuddy/
├── server.js              # HTTP server, REST API, and SQLite schema/logic
├── client.js              # Frontend integration layer, injected into every page
├── package.json           # npm scripts (start / dev)
├── .env.example           # Supported environment variables
├── data/                  # SQLite database (auto-created, gitignored)
└── public/                # Static frontend pages served as-is
    ├── lending.html
    ├── login.html / register.html
    ├── dashboard.html         # Parent view
    ├── kids.html / child.html  # Child wallet / purchase review
    ├── allownance.html          # Chores & allowance hub
    ├── savinggoals.html          # Family activity & approvals
    ├── savinggoals1.html          # Savings goals & milestones
    ├── learning.html              # AI Financial Academy
    ├── emergency.html              # Emergency Vault
    └── *.css
```

---

## 🚀 Run Locally

**Requirements:** Node.js **22.5+** (for built-in SQLite support)

```bash
git clone https://github.com/dhruvpatel09cg/Finance-Buddy.git
cd Finance-Buddy
npm start
```

Then open **[http://localhost:3000](http://localhost:3000)**.

For auto-restart on file changes during development:

```bash
npm run dev
```

On first run, the SQLite database is created automatically at `data/finance-buddy.sqlite` (excluded from Git). Copy `.env.example` to `.env` and set `SESSION_SECRET` to a long random value before deploying anywhere beyond localhost.

---

## 🧭 How to Use It

1. **Register** as a Parent or Child at `/register`
2. **Sign in** at `/login`
3. As a **Parent**: fund a child's wallet from `/dashboard` — the amount is auto-split 50/20/30 across Everyday/Emergency/Savings
4. As a **Child**: view your wallet at `/kids`, and raise a request from `/goals` or `/child` when you need to draw from Savings or Emergency
5. As a **Parent**: review pending requests from `/activity` and approve or reject
6. Explore chores (`/allowance`), lessons (`/learning`), and the locked reserve (`/emergency`)

---

## 🔌 API Overview

| Method | Route | Description |
|---|---|---|
| `POST` | `/api/auth/register` | Create a Parent or Child account |
| `POST` | `/api/auth/login` | Sign in and receive a session token |
| `GET` | `/api/me` | Get the current authenticated user |
| `GET` | `/api/dashboard` | Balances, pending approval, and goal progress |
| `POST` | `/api/funds` | *(Parent only)* Fund a wallet — auto-split 50/20/30 |
| `POST` | `/api/approvals` | *(Child only)* Request a withdrawal (amount + reason) |
| `POST` | `/api/approvals/:id/review` | *(Parent only)* Approve or reject a pending request |
| `POST` | `/api/events` | Log an in-app action (used by allowance/goal/academy/AI-plan screens) |

All authenticated routes expect an `Authorization: Bearer <token>` header, using the token returned by login/register.

### Page Routes
`/`, `/login`, `/register`, `/dashboard`, `/kids`, `/child`, `/allowance`, `/goals`, `/activity`, `/learning`, `/emergency`

---

## 🗺️ Roadmap

- [ ] File upload handling for bill/receipt proof-of-spend
- [ ] Automated flagging + refund flow for unspent approved amounts
- [ ] Real AI model integration for allocation recommendations (currently rule-based 50/20/30)
- [ ] Push/SMS notifications for approvals and declines
- [ ] Multi-child support per parent account

---

## 🏆 Built For

This project was built as a submission for **[Hackathon Name]**, under the **Fintech / Financial Literacy** track.

## 👥 Team

- Dhruv Patel — [GitHub](https://github.com/dhruvpatel09cg)
- Aditya Katariya
- Om Vaniya
- Kashyap Katariya

## 📄 License

Open source, available under the [MIT License](LICENSE).

---

<p align="center">Made with 💜 to help families build smarter money habits, together.</p>
