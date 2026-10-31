---
name: filing-styles
description: >-
  Use when choosing or explaining how a workspace should be organized, or when
  building one of the six filing styles.
---
# Filing styles

Six ways to file a workspace. When asking, show each name with its "suits" line. Show a sample only if the owner asks, with their own sections swapped in. Each style says where the sections from question 2 go.

## Military

Suits people who want one fixed home per function and never want to hunt. Sections go inside `3-ops/`.

```
1-admin/      contracts, insurance, bookkeeping
2-intel/      research, competitors, reference
3-ops/        the daily work, schedules, SOPs
  <section>/
4-supply/     vendors, purchases, inventory
5-plans/      forward planning
6-comms/      outbound, drafts, correspondence
```

## By stage

Suits almost anyone producing repeatable work. Folders follow the work itself. Sections go inside `2-production/`.

```
1-intake/     what came in, unprocessed
2-production/ active work
  <section>/
3-delivery/   what went out
4-archive/    finished and quiet
```

## By client or project

Suits people whose work is a set of named jobs with the same shape each time. Sections are the folders repeated inside each client. One `NOTES.md` inside `clients/` covers them, with a row per section.

```
clients/
  acme/
    <section>/
    <section>/
  northwind/
    ...same folders inside each
```

## PARA

Suits people who think in terms of how active something is, not what it is. Sections go inside `2-areas/`.

```
1-projects/   has a deadline and an end
2-areas/      ongoing responsibility, no end
  <section>/
3-resources/  reference, might be useful later
4-archive/    done or dead
```

## Numbered index

Suits people who want to find by number and hate nested folders. Each section takes its own range.

```
10-19 admin
20-29 money
30-39 <section>
40-49 <section>
50-59 reference
```

## By date

Suits work that is naturally chronological: logs, journals, records, sessions. Sections sit at the top, with dates inside each.

```
<section>/
  2026/
    01/
      the items from January
    02/
```

## What stays the same

The three layers work under every style. Only the folder names and nesting change:

1. A map in the Bot's folder saying what lives where.
2. A router in the Bot's folder saying which files a given kind of task needs.
3. A short notes file for each section saying what to read for what.

If the owner already has folders, keep their structure and add the three layers on top. Reorganizing someone's files on the first day is the fastest way to lose them.
