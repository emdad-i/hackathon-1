# hackathon-1

Self organised hackathon between four friends. Goal: build something real, fast.

## Dev setup

See **[developer_setup/README.md](developer_setup/README.md)** — VS Code, GitHub, Discord, and OpenCode. About 15 minutes, macOS and Windows.

## Tech stack

- **Backend:** FastAPI (Python), managed with uv
- **Frontend:** React + Vite, Tailwind CSS
- **Database + Auth:** Supabase (hosted Postgres)
- **CI:** GitHub Actions

That's it. No extra services unless they save us a day.

## How we work

Ship first, polish later. Pick the boring option, keep the diff small, and don't get blocked on tooling — ask in Discord `#help` and keep moving.

- **GitHub** (`hackathon-1`) — code, commits, and tickets.
- **Discord** — everything else.
- **OpenCode** — AI pair programmer on **DeepSeek V4.1 Flash (free)**; no key needed, `.opencode/opencode.jsonc` is configured.

## Roles

Four owners. Each one has final say in their area and is who you ask when stuck — but anyone can ship anywhere.

| Role | Drives (final say) | Consulted on |
| --- | --- | --- |
| **Backend Lead** | API shape, FastAPI routers, Pydantic models, error handling | Endpoint naming, perf, background jobs |
| **Frontend Lead** | React structure, routing, Tailwind/design consistency, UX polish, demo script | Loading/empty states, accessibility |
| **Data & Auth Lead** | Supabase schema, migrations, RLS policies, auth flows | Table design, indexing, secret handling |
| **Architecture / Platform Lead** | Stack and dependency choices, repo layout, FE↔BE API contract, env/config, CI and deploys | Schema, auth approach, build-vs-buy, ticket triage |

- **Decide in 10 minutes, default to boring.** If nobody objects within the hour, the call stands.
- **Adding a dependency is fine; the Platform Lead can veto the same day**, not after we've built on it.
- **Own the contract, not the implementation** — the Lead writes the API shape, Backend builds it.
