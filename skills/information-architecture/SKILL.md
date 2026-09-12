---
name: information-architecture
last_reviewed: 2026-09-06
group: Interface
description: >-
  Structure navigation, hierarchy and content models, and hand engineering an implementable spec.
  Use when structuring app navigation, sitemaps, hierarchy, or taxonomies.
---

# information-architecture

## Core Philosophy
Information Architecture (IA) is the structural engineering of shared information environments. Beautiful visual components cannot rescue a software product if users cannot find what they need or understand where they are. Professional IA bridges user mental models with business ontologies: organizing navigation hierarchies, establishing intuitive taxonomy structures, validating sitemaps through quantitative tree testing, and enforcing a maximum 3-click depth to core utility.

---

## 4-Step Information Architecture Engineering

### Step 1: User Mental Models & Content Modeling
1. **User Mental Models vs System Architecture**:
   - Software engineers organize by technical subsystem (e.g. `auth_service`, `billing_worker`).
   - Users organize by intent and job-to-be-done (e.g. `Projects`, `Team Access`, `Invoices`).
   - IA must strictly reflect user mental models, never internal engineering microservice divisions.
2. **Ontology & Object-Oriented UX (OOUX)**:
   - Identify the primary core objects of the application (e.g. in GitHub: *Repositories, Issues, Pull Requests, Releases*).
   - Map object relationships, metadata attributes, and nested hierarchies before designing navigation menus.

### Step 2: Card Sorting & Quantitative Tree Testing
1. **Open & Closed Card Sorts**:
   - *Open Card Sort (Discovery)*: Users group 40 content cards into categories and label the groups themselves (uncovers natural mental clusters).
   - *Closed Card Sort (Validation)*: Users sort cards into your proposed navigation categories (tests category naming clarity).
2. **Tree Testing (Reverse Card Sort)**:
   - Strip all visual UI and test pure text hierarchy:
     - Task: *"Find where to download last month's PDF billing invoice."*
     - Benchmark: Target $\ge 80\%$ direct task success without backtracking.

### Step 3: Navigation Systems & The 3-Click Rule
1. **The Navigation Topology**:
   - *Global Navigation (Top or Left Rail)*: Maximum 5–7 primary navigation items (Miller's Law).
   - *Contextual / Local Navigation*: In-page sub-tabs, filters, and breadcrumb trails.
   - *Utility Navigation*: Profile settings, notifications, documentation, team switcher.
2. **Click Depth Constraint**:
   - Any core action or high-frequency dashboard must be accessible within **$\le 3$ clicks** from any point in the application.
3. **Breadcrumb Trails**:
   - Mandatory for hierarchies deeper than 2 levels: `Organization > Project Alpha > Production Cluster > Node 04`.

### Step 4: Taxonomic URL Routing & Engineering Hand-Off
1. **Predictable RESTful URL Architecture**:
   - URLs should mirror the IA hierarchy cleanly:
     `/orgs/:org_id/projects/:project_id/settings/api-keys`
   - URLs must be shareable, bookmarkable, and human-readable.

---

## Deliverable Format: Information Architecture Specification (`IA-SPEC.md`)

```markdown
# Information Architecture Specification: [Application Name]

## 1. Core Object Taxonomy & Content Model
- **Primary Domain Objects**: Workspaces, Clusters, Deployments, Audit Logs
- **Hierarchy Tree**:
  ```
  App Root
  ├── Workspaces
  │   ├── Dashboard (Overview telemetry)
  │   ├── Clusters (List & Creation)
  │   │   └── [Cluster Detail]
  │   │       ├── Nodes
  │   │       ├── Deployments
  │   │       └── Networking
  │   └── Settings
  │       ├── Team Members & Roles
  │       ├── API Keys
  │       └── Invoices & Billing
  └── Documentation & Help
  ```

## 2. Navigation Structure & Tree Test Benchmarks
| Task | Target Path | Tree Test Success Rate | Directness Score |
|---|---|---|---|
| Revoke API Key | Settings > API Keys > Revoke | 94% | 88% |
| View Cluster p99 Latency | Clusters > [Cluster] > Telemetry | 89% | 82% |

## 3. URL Routing Taxonomy
- `/w/:workspace_slug` -> Workspace Dashboard
- `/w/:workspace_slug/clusters/:cluster_id` -> Cluster Overview
- `/w/:workspace_slug/settings/members` -> Team Management
```

---

## Worked Example: Overhauling a Bloated B2B Navigation

- **Problem**: SaaS dashboard had 18 items in the sidebar; users spent 4 minutes searching for audit log exports.
- **Research**: Conducted open card sort with 35 enterprise users. Grouped 18 items into 4 top-level buckets: *Operations, Monitoring, Security, Administration*.
- **Impact**: Tree test task completion time dropped from 3.8 minutes to 24 seconds.

---

## Verification Checklist

- [ ] Global navigation contains strictly 5–7 top-level categories.
- [ ] Hierarchy validated via quantitative tree testing with $\ge 80\%$ success rate.
- [ ] Critical tasks are achievable within $\le 3$ clicks from the root.
- [ ] Breadcrumb trails implemented on all deep views ($> 2$ levels).
- [ ] URL routing structure mirrors the information architecture hierarchically.

---

## Anti-Patterns

- **Org Chart Mirroring**: Structuring navigation based on internal company departments rather than user tasks.
- **Nested Accordion Hell**: Creating menus that expand 5 levels deep inside a narrow sidebar.
- **Vague Category Labels**: Naming navigation items "Miscellaneous", "Resources", or "Tools".
