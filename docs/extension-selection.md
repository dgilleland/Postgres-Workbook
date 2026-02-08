# VS Code Extensions

> I notice that there are two well-used VSCode extensions for Postgres with verified publishers.
>
> - One by "database-client.com"
> - One by "Microsoft"
>
> Can you dig into the background of the "database-client.com" extension? I'm curious about the origins and the current management, particularly in regards to any connections to China.

Here’s what’s publicly known about the **“database-client.com” PostgreSQL VS Code extension**—its origins, ownership signals, and whether there are China links.

---

## What extension we’re talking about

The extension typically appears as:

* **“Database Client” / “PostgreSQL – Database Client”**
* Publisher shown as **database-client.com**
* Marketplace ID tied to the GitHub project `cweijan/vscode-database-client`

It supports multiple DBs (Postgres, MySQL, SQLite, Redis, etc.) and includes telemetry and cloud-connected features. ([Visual Studio Marketplace][1])

---

## Origin & maintainer background

### Primary developer identity

* The extension’s codebase is maintained under the GitHub account **“cweijan.”** ([GitHub][2])
* That account hosts:

  * `vscode-database-client`
  * related tooling like JDBC adapters and VSCode extensions. ([GitHub][2])

The maintainer name is commonly associated with **Weijan Chen**, and the repository activity and naming patterns strongly indicate an individual-led project rather than a large company.

### Project structure signals

* Marketplace listing links to a project site and docs hosted at **database-client.com**. ([Visual Studio Marketplace][3])
* Documentation notes the extension **collects anonymous usage telemetry** sent to “Database Client server.” ([Visual Studio Marketplace][3])

This is typical for indie/commercialized open-source tooling but indicates:

* a backend service exists
* likely run by the maintainer or small team

---

## Connections to China (evidence vs signals)

### Direct indicators

* Marketplace and docs include **Chinese-language documentation (“中文文档”)**. ([Visual Studio Marketplace][3])
* Maintainer name and GitHub ecosystem suggest a **Chinese developer origin** (common inference in community discussions; not officially stated in the sources).

### What is *not* publicly established

No credible public source indicates:

* state ownership
* corporate ties to a Chinese tech firm
* regulatory affiliation or mandated data routing

There’s no documentation showing where telemetry servers are physically hosted.

### What can be reasonably inferred

From open signals:

* Likely **independent developer or small team, Chinese origin**
* Uses:

  * GitHub open-source model
  * standalone website + telemetry backend

This pattern is common among global VSCode extensions (many are solo-maintained).

---

## Governance & current management model

Based on repository + marketplace signals:

* **Ownership:** appears individual-led (GitHub maintainer + website)
* **Funding model:** unclear (likely free extension; may monetize via services later)
* **Infra:** custom backend (telemetry, possibly cloud-hosted)
* **Community:** open-source contributions exist but core repo controlled by maintainer

There’s no sign of:

* Microsoft partnership
* foundation governance
* enterprise vendor backing

---

## Security & risk considerations (practical view)

This matters more than nationality:

**Known behaviors**

* Sends telemetry (configurable / disableable). ([Visual Studio Marketplace][3])
* Connects to databases and can run queries, exports, backups.

**Risk profile (typical for DB extensions):**

* Has access to:

  * DB connection strings
  * query data
  * schema metadata
* Trust level similar to:

  * any SQL GUI
  * DataGrip / DBeaver plugins

**Best-practice checks**

* Disable telemetry if sensitive:

  * `"database-client.telemetry.usesOnlineServices": false`
* Inspect source:

  * repo is public
* Use network monitoring if handling prod data

---

## Comparison vs Microsoft PostgreSQL extension

**Microsoft extension**

* Corporate governance
* Azure integrations
* enterprise telemetry policies

**database-client.com**

* indie origin
* broader DB support
* faster iteration, fewer formal controls

This is a typical OSS vs vendor tradeoff.

---

## Bottom line

**What we know**

* Created and maintained by an independent developer (GitHub: cweijan).
* Likely Chinese origin based on language/docs + maintainer identity signals.
* Operates a backend for telemetry.
* No verified evidence of state/corporate ties or data exfiltration.

**What remains unknown**

* Exact company structure behind database-client.com
* server hosting location
* formal privacy governance

---

## If you’re evaluating it from a security / compliance angle

Tell me:

* personal use vs enterprise
* prod data vs local dev
* regulated environment (SOC2, HIPAA, etc.)

I can give a much sharper risk assessment (and whether you should default to Microsoft’s extension or not).

[1]: https://marketplace.visualstudio.com/items?itemName=cweijan.vscode-database-client2&utm_source=chatgpt.com "Database Client"
[2]: https://github.com/cweijan?utm_source=chatgpt.com "Weijan Chen cweijan"
[3]: https://marketplace.visualstudio.com/items?itemName=cweijan.vscode-postgresql-client2&utm_source=chatgpt.com "PostgreSQL - Database Client"

----

> There are a couple of other extensions that do not have the blue author verification badge, but they have evidence of large usage in the community. Those are by
>
> - Christ Kolkman (1.2M installations)
> - Matheus Teixeira (1M installations)
>
> Can you tell me about those: What they offer and how they differ?

----

Here’s a clear breakdown of the two high-install PostgreSQL/SQL-related VS Code extensions you mentioned — what they do, how they’re built, and how they differ from each other (and from the Microsoft + database-client ones).

---

# 1) Chris Kolkman — “PostgreSQL”

| ![Image](https://raw.githubusercontent.com/Sang-Buster/Picgo-Github/main/img/Blog_img/VSCode-PostgreSQL/pgSQL%20%281%29.png) | ![Image](https://neon.com/_next/image?dpl=dpl_3NqBtEJ3VUDxtNqPZXKpDq7ycAHD\&q=85\&url=https%3A%2F%2Flh7-rt.googleusercontent.com%2Fdocsz%2FAD_4nXevxqp6xyOCi6nnuGXWQtEtuL8O_WjkGVyXTfeASINbBu4FbRy0HPKHwidqLiNQ_qDNzRE4QIu9girlGimrKRFYBLlHYXJ8NiEnZ9qZIAxFe1EAo1fxBJEIkHDxbr2P91wTTeaBuw%3Fkey%3DCKEVDXfmm-8ATNSVeLVVDQ\&w=1200) | ![Image](https://learn.microsoft.com/en-us/azure/postgresql/developer/vs-code-extension/media/vs-code-connect/portal-connect-3.png) |
|--|--|--|

### What it is

* Extension name: **PostgreSQL**
* Publisher: **Chris Kolkman**
* ~1.2M installs
* Positioning: lightweight PostgreSQL management + editing tool

It’s one of the earliest VSCode Postgres extensions and focuses primarily on PostgreSQL specifically (not multi-database).

### Core capabilities

* Connect to PostgreSQL instances
* Run SQL queries
* Browse schemas/tables
* Basic management from VSCode UI
* Syntax support for Postgres file types like `.pgsql` and `.psql` ([Stack Overflow][1])

Marketplace and tutorials consistently describe it as a **PostgreSQL management tool integrated into the editor** with credential-based connections and query execution. ([Visual Studio Marketplace][2])

### Design philosophy

* Focused: **Postgres-only**
* Minimal dependencies
* Simple UI
* “Old-school” VSCode extension model (pre language-server ecosystem)

### Limitations compared to newer tools

* Slower update cadence
* Less extensible
* Fewer advanced dev features (linting, drivers, multi-DB)
* Mostly “viewer + query runner”

This is why some people still use it primarily for:

* syntax highlighting
* quick local connections
* simple database browsing

---

# 2) Matheus Teixeira — “SQLTools”

![Image](https://learn.microsoft.com/en-us/sql/tools/visual-studio-code-extensions/mssql/media/mssql-extension-visual-studio-code/query-results-vscode.png?view=sql-server-ver17) | ![Image](https://raw.githubusercontent.com/mtxr/vscode-sqltools/master/docs/assets/auto-open-session.gif) | ![Image](https://user-images.githubusercontent.com/31692408/60165825-f9eb8e00-983a-11e9-9a2d-98887f1189ec.png) |
|--|--|--|

### What it is

* Extension: **SQLTools**
* Publisher: **Matheus Teixeira**
* ~1M installs
* Not Postgres-specific — it’s a **framework + ecosystem**

SQLTools is best thought of as a **database client platform inside VSCode**, not just a single DB extension.

It connects to databases and displays results directly in the editor environment. ([Visual Studio Marketplace][3])

### Core architecture

* Main extension = UI + query runner
* Drivers installed separately:

  * PostgreSQL
  * MySQL
  * MSSQL
  * SQLite
  * etc.

This modular approach is a major difference vs Kolkman’s.

### Core capabilities

* Query editor + results grid
* Saved connections
* Credential handling
* Multi-database support via drivers
* Extensions ecosystem
* Database explorer panel

Typical flow:

* install SQLTools
* install Postgres driver
* add connection
* run queries + browse results

(You often see tutorials describing installing SQLTools first, then DB drivers.) ([Stack Overflow][4])

### Design philosophy

* Platform-style
* extensible
* DB-agnostic
* more developer-tooling-oriented

---

# How they differ (important)

| Dimension    | Chris Kolkman        | Matheus Teixeira         |
| ------------ | -------------------- | ------------------------ |
| Scope        | PostgreSQL only      | Multi-database framework |
| Architecture | Single extension     | Core + drivers           |
| Primary use  | Simple DB management | Dev workflow + tooling   |
| Query UI     | Basic                | More advanced            |
| Ecosystem    | Limited              | Growing plugin ecosystem |
| Complexity   | Lightweight          | Heavier but flexible     |
| Audience     | Postgres users       | General SQL developers   |

**Simplified:**

* Kolkman → “Postgres inside VSCode”
* SQLTools → “DB client platform inside VSCode”

---

# Where they sit relative to Microsoft + database-client

Think of the ecosystem like this:

### Lightweight / focused

* Chris Kolkman PostgreSQL

### Modular dev tooling

* SQLTools

### Full DB GUI inside VSCode

* database-client.com

### Enterprise / cloud integrated

* Microsoft PostgreSQL extension

Each targets a different philosophy:

| Tool            | Strategy                        |
| --------------- | ------------------------------- |
| Kolkman         | simple + stable                 |
| SQLTools        | extensible developer tooling    |
| database-client | full desktop-client replacement |
| Microsoft       | enterprise + Azure              |

---

# Maintainer & project signals

### Chris Kolkman

* Solo-maintained
* older extension lineage
* conservative scope
* slower releases

### Matheus Teixeira

* active open-source ecosystem
* multiple contributors
* GitHub-driven plugin architecture
* community DB driver contributions

SQLTools behaves more like an OSS platform vs a single utility extension.

---

# Practical decision guide

### Choose Kolkman if:

* Postgres only
* minimal features needed
* want lightweight, stable

### Choose SQLTools if:

* use multiple DBs
* want extensibility
* dev workflow focus
* prefer plugin architecture

### Choose database-client if:

* want pgAdmin/DBeaver-like GUI inside VSCode

### Choose Microsoft if:

* Azure/Postgres cloud work
* enterprise environment
* corporate governance required

---

# Security / trust note (important)

Neither Kolkman nor SQLTools has:

* corporate backing like Microsoft
* verification badge
* formal security audits

But:

* both are widely used OSS
* SQLTools especially has strong community scrutiny

Risk profile:

* similar to installing DBeaver or any DB GUI

---

## If your real question is “which one should I trust most”

That depends on what you optimize for:

* OSS transparency → SQLTools
* simplicity → Kolkman
* enterprise governance → Microsoft
* features/UI → database-client

---

## Want the deeper comparison?

I can break these 4 into a **serious engineering comparison**:

* telemetry behavior
* credential storage
* network calls
* extension permissions
* update patterns
* maintainer geography
* security posture

That’s usually what teams actually need when deciding what’s allowed in their dev environment.

[1]: https://stackoverflow.com/questions/78376349/better-syntax-highlighting-for-postgresql-in-vs-code?utm_source=chatgpt.com "Better syntax highlighting for PostgreSQL in VS Code"
[2]: https://marketplace.visualstudio.com/items?itemName=ckolkman.vscode-postgres&utm_source=chatgpt.com "PostgreSQL"
[3]: https://marketplace.visualstudio.com/items?itemName=mtxr.sqltools&utm_source=chatgpt.com "SQLTools"
[4]: https://stackoverflow.com/questions/70805916/debugging-t-sql-in-vs-code?utm_source=chatgpt.com "Debugging T-SQL in VS Code"

----

> Yes, continue a breakdown of the four options in terms of the "serious engineering comparison" points you listed.

----

## Comparison

Below is a **practical engineering-level comparison** of the four VS Code Postgres options:

* Microsoft PostgreSQL extension
* database-client.com
* SQLTools (Matheus Teixeira)
* PostgreSQL (Chris Kolkman)

I’m focusing specifically on the factors teams actually evaluate for internal approval: telemetry, credential handling, network behavior, permissions, maintenance, and governance.

---

# 1) Telemetry behavior

## Microsoft PostgreSQL

**Telemetry:** Yes (standard Microsoft developer telemetry)

* Uses Microsoft data collection policies
* Typically:

  * usage metrics
  * crash reports
  * feature engagement
* Governed by Microsoft privacy & enterprise agreements
* Often configurable via VS Code telemetry settings

**Risk profile:** lowest compliance risk for enterprises
**Reason:** documented, audited, and predictable

---

## database-client.com

**Telemetry:** Yes (explicit in extension settings/docs)

* Sends:

  * usage metrics
  * feature activity
* To: “Database Client server” (custom backend)
* Can be disabled via config

**Unknowns**

* server hosting location
* data retention policies
* organizational structure operating backend

**Risk profile:** medium
**Reason:** indie telemetry backend vs corporate governance

---

## SQLTools

**Telemetry:** Minimal / optional

* Primarily OSS
* Focused on:

  * local functionality
  * drivers run client-side
* No strong evidence of centralized telemetry pipelines

Drivers may add:

* logging
* optional telemetry depending on DB ecosystem

**Risk profile:** low–medium
**Reason:** decentralized, OSS, less centralized data flow

---

## Chris Kolkman PostgreSQL

**Telemetry:** minimal or none historically

* Older extension design
* Local query execution model
* No major telemetry backend signals

**Risk profile:** low (but also less actively monitored)

---

# 2) Credential storage & handling

This is one of the most important technical differences.

## Microsoft

* Uses VS Code secure storage APIs
* Integrates with:

  * OS credential vault
  * Azure auth flows
* Enterprise patterns

**Strength:** strong security model
**Tradeoff:** cloud tie-ins

---

## database-client.com

* Stores connection configs locally
* May:

  * encrypt
  * or store plain config depending on setup
* Cloud features may involve remote services

**Concern area**

* backend-connected features increase attack surface
* unclear key management model

---

## SQLTools

* Uses:

  * VS Code SecretStorage API
  * driver-level credential passing
* Modular architecture:

  * each driver handles auth

**Strength**

* transparent OSS
* inspectable

**Weakness**

* security varies by driver

---

## Kolkman

* Simple local credential storage
* No complex auth flows
* No platform abstraction

**Strength:** minimal attack surface
**Weakness:** fewer enterprise protections

---

# 3) Network behavior

## Microsoft

Network calls to:

* Azure
* extension telemetry endpoints
* update services

Predictable, documented.

---

## database-client.com

Network activity includes:

* telemetry backend
* optional cloud features
* possible driver downloads
* extension services

**This is the most network-active of the four.**

---

## SQLTools

Network calls:

* only when connecting to DB
* drivers may call:

  * npm repos
  * DB services

No central cloud platform.

---

## Kolkman

Primarily:

* DB connections only

Very little external traffic.

---

# 4) Extension permissions & attack surface

| Extension       | Complexity | Attack surface              |
| --------------- | ---------- | --------------------------- |
| Microsoft       | High       | enterprise-grade but large  |
| database-client | High       | includes backend + multi-db |
| SQLTools        | Medium     | modular drivers             |
| Kolkman         | Low        | simple Postgres-only        |

Rule of thumb:

* More features → more code → more risk

database-client has the **largest functional footprint**.

---

# 5) Update cadence & maintainer activity

## Microsoft

* consistent releases
* corporate lifecycle support

## database-client

* active indie development
* rapid feature shipping
* depends on maintainer availability

## SQLTools

* active OSS
* contributor-driven
* steady driver updates

## Kolkman

* slower updates
* mature/stable but less evolving

---

# 6) Governance & ownership model

This is where enterprise teams care most.

| Extension       | Governance                   |
| --------------- | ---------------------------- |
| Microsoft       | Corporate, audited           |
| database-client | Indie developer / small team |
| SQLTools        | OSS community project        |
| Kolkman         | Solo maintainer              |

database-client is the only one with:

* custom backend infra
* unknown org structure
* semi-commercial trajectory

---

# 7) Maintainer geography signals

No extension explicitly publishes geography.

Observed signals:

* Microsoft → US corporate
* database-client → strong Chinese-language signals, Chinese maintainer identity likely
* SQLTools → Brazilian maintainer, global OSS contributors
* Kolkman → Western individual developer

Important:
**Nationality ≠ risk.**
The real differentiator is:

* governance
* infra
* telemetry
* code transparency

---

# 8) Real-world risk scenarios

### Scenario A — personal dev

Best choices:

* SQLTools
* Kolkman
* database-client if you want UI

### Scenario B — startup handling prod data

Best:

* SQLTools
* Microsoft

### Scenario C — enterprise / regulated

Best:

* Microsoft only
* SQLTools sometimes approved

database-client usually triggers security review because:

* remote telemetry server
* unclear governance

### Scenario D — air-gapped / secure env

Best:

* Kolkman
* SQLTools (offline drivers)

Worst fit:

* database-client

---

# 9) Architectural philosophy comparison

This is the deeper difference.

| Tool            | Philosophy              |
| --------------- | ----------------------- |
| Microsoft       | enterprise integration  |
| database-client | VSCode as full DB GUI   |
| SQLTools        | extensible dev platform |
| Kolkman         | simple editor add-on    |

They’re not actually competing head-to-head:
they solve different layers of the workflow.

---

# 10) Engineering recommendation matrix

If I were writing internal guidance:

### Lowest risk

* Microsoft
* Kolkman

### Best OSS balance

* SQLTools

### Most powerful but highest scrutiny

* database-client

---

# Bottom line

**database-client**

* richest features
* largest attack surface
* telemetry backend

**SQLTools**

* best engineering middle ground
* transparent architecture
* strong dev tooling

**Kolkman**

* simplest
* least moving parts
* lowest operational complexity

**Microsoft**

* safest for compliance
* strongest governance
* Azure-aligned

---

## The question most teams eventually ask

Not “which is best?” but:

**“Which one should we allow in our dev environment policy?”**

That answer depends heavily on:

1. production DB access vs local only
2. company size
3. compliance regime (SOC2, ISO, HIPAA, etc.)
4. threat model (IP theft vs account compromise vs supply chain)

If you tell me:

* solo dev / startup / big company
* data sensitivity level
* cloud vs on-prem

I can give you a **clear recommendation** (the kind security teams actually sign off on).
