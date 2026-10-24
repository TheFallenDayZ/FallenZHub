# ☣️ FallenZ Hub — Community Field Hub

<p align="center">
  <img src="public/logo.png" alt="FallenZ Logo" width="180" />
</p>

<h3 align="center">THE ZONE IS LOST. STAY ALIVE.</h3>

<p align="center">
  Your central command for the FallenZ DayZ survival community.
</p>

<p align="center">
  <a href="https://www.fallenzhub.shop">🌐 Visit FallenZ Hub</a>
  ·
  <a href="https://discord.gg/Nmc64ZbFtk">💬 Join Our Discord</a>
</p>

---

## 🩸 Welcome to FallenZ

**FallenZ Hub** is the official digital home of the FallenZ DayZ community — a survival-focused platform built to bring our players, servers, collectibles, virtual economy, and community features together in one place.

Designed around the brutal atmosphere of DayZ, FallenZ Hub combines a dark, immersive interface with interactive systems that extend the survivor experience beyond the game itself.

Whether you're checking server information, building your survivor collection, competing in casino games, managing a territory, or preparing an in-game shop order, the Hub provides a central place to connect with the FallenZ world.

**This is more than a website. It's another part of the survival experience.**

> ⚠️ Every survivor has a story. Every decision has consequences. Welcome to the zone.

---

## 🎮 Built for the FallenZ Community

FallenZ Hub is designed around our DayZ community and its PlayStation survival servers, including:

* 🏜️ **NASDARA** — Survive the desert, establish your territory, and fight to stay alive.
* ❄️ **SAKHAL** — Prepare for a harsher environment and adapt to the conditions.
* ☣️ **Community Field Hub** — Access community features, updates, and survivor services from one location.

Server information and availability depend on the configured server records and connected Nitrado services.

---

## 🔥 Features & Systems

### 🌐 Community Dashboard

Your central overview of the FallenZ world.

* Community-focused homepage and navigation.
* Configured DayZ server roster.
* Live server status and player counts when Nitrado integration is available.
* Published community updates and announcements.
* Discord-connected member information.
* Quick access to the Hub's main features.

### 🔐 Discord Authentication

Your Discord account connects you to the FallenZ community experience.

* Discord OAuth sign-in.
* Guild-membership verification.
* Signed, HTTP-only session cookies.
* Role-based authorization for protected administration features.
* Member-specific wallet and collection information.
* Server-side authentication checks for protected operations.

Access to member-only information requires authentication. Administrative access depends on the configured Discord role and permissions.

### 🃏 FallenZ Card Market

Collect, trade, and complete your own collection of survival-themed cards.

The card system includes:

* A catalog of **280 survival-item cards**.
* Illustrated supply packs.
* Daily pack rewards.
* Persistent member collections.
* Duplicate-card credit handling.
* Card marketplace listings and transfers.
* Illustrated collections and completion rewards.
* Collection progress tracking.
* An administrative card and pack studio.

Collect cards, build your inventory, hunt for missing items, and work toward completing your favorite sets.

Card purchases, market transfers, and eligible rewards use the existing Discord bot wallet. Survivor Cards are virtual collectibles with no cash value.

### 🎰 FallenZ Casino

Take a break from the wasteland and test your luck using virtual FallenZ credits.

Available games include:

* Supply Slots
* Blackjack
* Infected Dice
* Scavenger Draw
* Zombie Roulette
* Fate's Coin

The casino uses server-side game logic and the existing Discord bot wallet for wagers and payouts.

**Important:** Credits are virtual-only. They cannot be purchased through the casino for real money or redeemed for cash or real-world value. Game availability and rules are determined by the implemented systems.

### 🏕️ Survivor Camp

Build your presence in the wasteland through a shared multiplayer territory experience.

Survivor Camp includes systems for:

* Territory control across a Nasdara-inspired world.
* Control points and named locations.
* Factions, crews, and player invitations.
* Timed supply missions and raids.
* Shared resource inventories.
* Food, wood, metal, cloth, medicine, and ammunition.
* Truck repairs and vehicle upgrades.
* Armor and window improvements.
* Persistent world and mission state.
* Live route overlays.

Your actions contribute to a shared world stored in MongoDB. Camp inventories also synchronize with the configured Discord bot inventory records.

Team up with other survivors, expand your influence, gather supplies, and build your foothold in the zone.

### 🛒 DayZ Field Shop

The Field Shop provides a web-based interface for browsing and placing eligible in-game item orders.

Features include:

* DayZ item catalog.
* Shopping cart.
* Map-based placement.
* Server selection.
* Discord-authenticated checkout.
* Virtual wallet payments.
* Persistent order records.
* Queue-based order publishing.

**Order delivery requirements:** The website stores eligible orders in a durable queue. A separately configured publishing worker must retrieve the queued orders and upload the combined `custom/shop.json` to the appropriate Nitrado server before the normal restart.

The website does not restart game servers automatically. Checkout should remain disabled until map coordinates, the publishing worker, and the delivery process have been tested successfully in a staging environment.

### 📰 Community Updates & Dispatches

Stay informed about changes across the FallenZ community.

* Publish updates through protected administration tools.
* Store announcements in MongoDB.
* Display published updates on the Hub.
* Upload update images.
* Optionally send announcements to Discord using a configured webhook.

Discord delivery can fail independently of website publication. Administrators can inspect delivery status when a webhook is configured.

### 🛠️ Administration Tools

Authorized administrators can manage important community content through protected pages.

Current administration areas include:

* **Server Studio:** Manage the public server roster and optional Nitrado service links.
* **Card Studio:** Manage card and pack content.
* **Shop Studio:** Manage the DayZ shop catalog, prices, and map calibration.
* **Community Updates:** Publish announcements through the protected update API.

Administrative access is controlled by the application's Discord configuration. Never expose administrator credentials, database connections, or API secrets in client-side code.

### 🧰 DayZ Tools

The Hub includes browser-based XML and JSON validation tools for working with DayZ-related configuration files.

These tools are intended to help survivors and server administrators inspect configuration data more conveniently.

**Development note:** Loadout editing, spawn-point editing, and types-file tools are not currently implemented. They should not be advertised as available until those features have been built and tested.

---

## 🧱 Technology Stack

FallenZ Hub is built using modern web technologies.

| Technology      | Purpose                                                |
| --------------- | ------------------------------------------------------ |
| Next.js 16      | Web application framework and API routes               |
| React 19        | Interactive user interface                             |
| TypeScript      | Type-safe application development                      |
| Tailwind CSS 4  | Styling infrastructure                                 |
| MongoDB         | Persistent application, game, market, and order data   |
| Discord OAuth2  | Community authentication                               |
| Discord Bot API | Member information and existing bot-wallet integration |
| Nitrado API     | DayZ server discovery and status integration           |
| Vercel          | Production hosting and deployment                      |
| Resend          | Optional newsletter contact integration                |

---

## 🗂️ Project Structure

The project uses the Next.js App Router.

```text
FallenFeeds-Web/
├── app/
│   ├── admin/
│   │   ├── cards/
│   │   ├── servers/
│   │   └── shop/
│   ├── api/
│   │   ├── admin/
│   │   ├── auth/
│   │   ├── cards/
│   │   ├── casino/
│   │   ├── members/
│   │   ├── servers/
│   │   ├── shop/
│   │   ├── survivor-camp/
│   │   ├── updates/
│   │   └── wallet/
│   ├── components/
│   │   ├── card-hub.tsx
│   │   ├── casino-hub.tsx
│   │   ├── dayz-shop.tsx
│   │   ├── hub-ui.tsx
│   │   └── survivor-camp.tsx
│   ├── shop/
│   ├── survivor-camp/
│   ├── globals.css
│   ├── layout.tsx
│   └── page.tsx
├── lib/
├── public/
├── scripts/
├── .env.example
├── package.json
├── README.md
└── tsconfig.json
```

*The tree above highlights the main application areas. Additional files and modules support authentication, database access, game logic, assets, and deployment.*

---

## 🚀 Run Locally

### Requirements

Before starting, install:

* Node.js compatible with the project's Next.js 16 requirements.
* npm.
* A MongoDB deployment that supports transactions for the game and economy systems.
* A Discord application and bot if you intend to enable Discord integration.

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
cd FallenFeeds-Web
```

Replace the repository URL and directory with your actual GitHub details.

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

Copy `.env.example` to `.env.local` and populate the required values.

```bash
cp .env.example .env.local
```

On Windows, you can copy the file manually or use PowerShell:

```powershell
Copy-Item .env.example .env.local
```

Do not commit `.env.local` to GitHub.

### 4. Start the development server

```bash
npm run dev
```

Open the following address in your browser:

```text
http://localhost:3000
```

### 5. Run quality checks

```bash
npm run lint
npm run format:check
npm run build
```

Run these checks before deploying changes to production.

---

## ⚙️ Environment Configuration

The application uses server-side environment variables for external services.

| Variable                      | Purpose                                       |
| ----------------------------- | --------------------------------------------- |
| `SITE_URL`                    | Canonical public website URL                  |
| `AUTH_SECRET`                 | Secret used to sign authentication sessions   |
| `DISCORD_CLIENT_ID`           | Discord OAuth application ID                  |
| `DISCORD_CLIENT_SECRET`       | Discord OAuth application secret              |
| `DISCORD_REDIRECT_URI`        | Registered Discord OAuth callback URL         |
| `DISCORD_BOT_TOKEN`           | Server-side Discord bot authentication        |
| `DISCORD_GUILD_ID`            | FallenZ Discord server ID                     |
| `DISCORD_ADMIN_ROLE_ID`       | Role ID used for administrative authorization |
| `MONGODB_URI`                 | MongoDB connection string                     |
| `MONGODB_DB`                  | MongoDB database name                         |
| `NITRADO_TOKEN`               | Optional Nitrado API token                    |
| `NITRADO_SERVER_ID`           | Optional specific Nitrado service ID          |
| `DAYZ_SHOP_WORKER_TOKEN`      | Secret shared with the external shop worker   |
| `DAYZ_SHOP_CHECKOUT_ENABLED`  | Enables or disables shop checkout             |
| `DISCORD_UPDATES_WEBHOOK_URL` | Optional Discord updates webhook              |
| `RESEND_API_KEY`              | Optional Resend newsletter API key            |

Consult `.env.example` and the deployment instructions in this repository for the complete configuration requirements.

**Never publish real secrets, OAuth credentials, database URLs, bot tokens, or worker tokens.** Environment variables must be configured in the hosting provider for the appropriate deployment environment.

---

## 🌍 Deployment on Vercel

FallenZ Hub is designed to deploy through GitHub and Vercel.

1. Push the project to your GitHub repository.
2. Import the repository into Vercel.
3. Configure the required production environment variables.
4. Set `SITE_URL` to the canonical HTTPS domain.
5. Configure the Discord OAuth redirect URI to match the deployed callback URL exactly.
6. Ensure MongoDB is reachable from the deployed application.
7. Verify the Discord bot permissions and Server Members Intent where required.
8. Deploy the project and inspect the build logs.
9. Test authentication, server status, member-only pages, and administrative permissions.
10. Verify the shop worker and other external integrations independently before enabling production transactions.

For example, if the public site uses `https://www.fallenzhub.shop`, the Discord callback can be configured as:

```text
https://www.fallenzhub.shop/api/auth/callback/discord
```

The callback URL in Vercel must match the URL registered in the Discord Developer Portal.

**Deployment safety:** Keep shop checkout disabled until the publishing worker, map calibration, and order delivery have been tested against a staging environment. Do not use a busy production game world for destructive integration tests.

---

## 🔒 Security & Data Integrity

FallenZ Hub handles authentication, virtual balances, collections, and persistent multiplayer state. Security and consistency are important parts of the design.

* Authentication sessions are signed and stored in HTTP-only cookies.
* Protected API routes validate authorization on the server.
* Discord membership and configured administrative roles govern access.
* MongoDB transactions protect related wallet and game operations.
* The existing Discord bot wallet is reused rather than creating a separate website wallet.
* Nitrado credentials remain server-side.
* Shop orders are queued for a separate publishing worker.
* Checkout is disabled by default.
* API routes are excluded from crawler indexing through the site's robots rules.

### Security guidelines

* Never commit `.env`, `.env.local`, or production secrets.
* Never expose private tokens through `NEXT_PUBLIC_*` environment variables.
* Use a strong `AUTH_SECRET` of at least 32 characters.
* Restrict MongoDB network access and database permissions.
* Use separate staging and production databases.
* Rotate credentials immediately if they are exposed.
* Test authorization boundaries before releasing new admin features.
* Keep third-party integrations and scheduled workers secured with separate secrets.

The application is intended to use a transaction-capable MongoDB deployment. Confirm database and integration requirements before running the full multiplayer economy in production.

---

## 🧪 Diagnostics & Testing

The repository includes commands for inspecting the economy schema and testing Survivor Camp workflows.

```bash
npm run inspect:economy
```

Inspect the optional value-free schema shape:

```bash
npm run inspect:economy -- --shape
```

Run the Survivor Camp integration test:

```bash
npm run test:survivor-camp
```

These diagnostic scripts require the appropriate local environment and, where applicable, a running application and database connection.

Run integration tests against staging whenever possible. The Survivor Camp test creates temporary synthetic records and attempts to remove its test data afterward; do not run it against a busy production world without reviewing the script and its effects first.

---

## 🛣️ Development Roadmap

FallenZ Hub is an evolving project. Future development may focus on:

* Further improvements to the mobile experience.
* More detailed server status and community dashboards.
* Expanded collectible cards, packs, and collection progression.
* Additional Survivor Camp missions and territory features.
* Better administration workflows and content management.
* Improved diagnostics for Discord, MongoDB, and Nitrado integrations.
* More robust shop-worker monitoring and delivery reporting.
* Additional DayZ configuration tools.
* Further performance, accessibility, and security improvements.

This roadmap represents potential development areas, not a promise that every feature is already implemented or scheduled for release.

---

## 🤝 Contributing

FallenZ Hub is built around the FallenZ community.

Before contributing code:

1. Create a feature branch.
2. Keep changes focused and clearly documented.
3. Avoid committing secrets, generated credentials, or private server information.
4. Run linting, formatting, and build checks.
5. Test changes against staging integrations where appropriate.
6. Document any new environment variables and deployment requirements.

For community-specific feature requests, server issues, or project discussions, use the official FallenZ Discord.

---

## 📜 Credits & Third-Party Assets

FallenZ Hub incorporates custom community branding, application code, and third-party integrations.

Some default card artwork references DayZ Wiki.gg image files. Artwork licensing may vary by file, so check the relevant source page and license terms before redistributing assets.

DayZ, Discord, Nitrado, MongoDB, Next.js, Vercel, and other referenced products remain the property of their respective owners. Mention of these services does not imply official endorsement.

---

## ☣️ Join the Fight

<p align="center">
  <strong>THE WASTELAND DOESN'T FORGIVE.</strong>
</p>

<p align="center">
  Explore the Hub. Build your collection. Rally your survivors. Claim your place in the zone.
</p>

<p align="center">
  <a href="https://www.fallenzhub.shop">🌐 FALLENZ HUB</a>
  <br />
  <a href="https://discord.gg/Nmc64ZbFtk">💬 JOIN THE COMMUNITY</a>
</p>

<p align="center">
  <em>FallenZ — The zone is lost. Stay alive.</em>
</p>

