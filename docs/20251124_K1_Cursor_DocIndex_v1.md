# Cursor Doc Index v1
**File:** 20251124_K1_Cursor_DocIndex_v1.md  
**Owner:** ~K¹  
**Purpose:** Act as a map of Kyle’s Cursor-related documentation sources so AI models can quickly locate the right reference.

This file is meant to be indexed by Cursor’s Docs feature.

---

## 1. Internal docs in this repo

These are the core documents in the `cursor-global-docs` repository:

1. **Global Pack**
   - File: `20251124_K1_Cursor_GlobalPack_v1.md`
   - Role: Mental model of Cursor, confusion detection, safety rules.

2. **Workflows Pack**
   - File: `20251124_K1_Cursor_Workflows_v1.md`
   - Role: Named, reusable playbooks for common tasks.

3. **Doc Index (this file)**
   - File: `20251124_K1_Cursor_DocIndex_v1.md`
   - Role: Routing layer; tells the AI which doc to use for what.

When you, the AI, need:

- **“How should I behave in Cursor?”** → Read the **Global Pack**.  
- **“What specific steps do I take to do X?”** → Read the **Workflows Pack**.  
- **“Where are the docs located?”** → Start here.

---

## 2. External documentation sources (to be added in Cursor)

The following URLs should be added in **Cursor → Settings → Indexing & Docs → Docs** as external docs sources (if Kyle hasn’t already done so):

1. **Cursor official docs**
   - Root: `https://cursor.com/docs`
   - Use for:
     - Exact Cursor behavior.
     - Features, modes, models.
     - Indexing & docs configuration.
     - Rules & Commands details.

2. **(Example) Framework / library docs**
   - These vary per project. Possible examples:
     - `https://react.dev/reference`
     - `https://nextjs.org/docs`
     - `https://nodejs.org/api/`
     - `https://www.prisma.io/docs`
     - etc.

For each project, Kyle may configure the relevant set of external docs based on its stack. You must:

- Prefer **official docs** (Cursor + framework) for low-level or API-level questions.
- Use the **Global Pack** and **project-local packs** for behavior, policies, and workflows.

---

## 3. How to choose the right doc source

When a question arises, select doc sources using this decision tree:

1. **Is the question about Cursor itself?**
   - Yes →  
     - Start with: **Global Pack**  
     - Then: Cursor official docs (`https://cursor.com/docs`)

2. **Is the question about how to behave or what steps to follow in Kyle’s environment?**
   - Yes →  
     - Start with: **Global Pack**  
     - If repo-specific → search for **project-local packs**

3. **Is the question about a specific codebase / framework / library?**
   - Yes →  
     - Start with: project-local docs (if any).  
     - Then: external framework docs configured in Cursor.  
     - Use Workflows Pack when there is a relevant workflow.

4. **Is the question a “how do I perform X workflow?”**
   - Yes →  
     - Start with: **Workflows Pack**  
     - Consult external docs if the steps require stack-specific knowledge.

---

## 4. Priority and conflict resolution

When multiple sources disagree:

1. **Safety always wins**  
   - Choose the course of action that minimizes risk and is easiest to undo.

2. **For product behavior (Cursor / framework)**  
   - Prefer current, official docs over old notes.

3. **For Kyle’s preferences within his repos**  
   - Prefer project-local packs over generic/global advice.

4. **For workflows**  
   - Use the Workflows Pack as a baseline and adapt based on newer information, but do not silently discard it; explain deviations.

---

## 5. How to update or extend this index

When Kyle adds new docs:

- For example, a new pack: `2026MMDD_K1_Cursor_SecurityPack_v1.md`:
  1. Add it to this index with:
     - Name, file path, purpose.
  2. Note when it should be preferred over existing packs.

You, the AI, should treat newly added entries here as valid routing information once they appear in this file and are indexed.
