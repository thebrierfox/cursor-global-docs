# cursor-global-docs

This repository contains global documentation packs for Cursor usage tailored for Kyle Million (~K¹). These markdown files are intended to be indexed by Cursor’s external docs feature, providing a persistent source of truth for how Cursor agents should think about themselves, follow structured workflows, and route documentation queries.

## Contents

- **docs/20251124_K1_Cursor_GlobalPack_v1.md** – Defines the mental model of Cursor, confusion detection triggers, and safety protocols when operating on Kyle’s projects.
- **docs/20251124_K1_Cursor_Workflows_v1.md** – A collection of reusable playbooks for common tasks like error cleanup, new feature implementation, large refactors, documentation synthesis, and more.
- **docs/20251124_K1_Cursor_DocIndex_v1.md** – An index and routing layer that helps agents decide which document to consult and when to fall back to official docs or project-local packs.

## Usage

Add this repository’s `docs/` directory as an external documentation source in Cursor (Settings → Indexing & Docs → Docs). This will allow Cursor agents to reference these files automatically when they need to understand Cursor’s capabilities, follow pre-defined workflows, or determine which documentation source to consult.

For project-specific behavior, create additional knowledge pack files within the respective repositories (e.g., `docs/2025MMDD_K1_<project>_CursorPack_v1.md`) and instruct agents to use them in combination with these global docs.
