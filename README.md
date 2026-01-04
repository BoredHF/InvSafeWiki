# InvSafe

**Undo-safe inventory recovery for Minecraft servers**

InvSafe provides deterministic, reversible inventory restores without rollbacks, databases, or guesswork.

---

## Core Principle

**Every restore is reversible.**

Before any restore, InvSafe automatically captures a safety snapshot.  
If a restore is incorrect, it can be undone safely.

All inventory changes are inspectable before and after application.

---

## Typical Workflow

1. An incident occurs  
2. Snapshot history is reviewed  
3. Inventory differences are inspected  
4. A restore is applied  
5. The restore can be undone if needed  

---

## What InvSafe Covers

- Inventory wipes  
- Post-crash item loss  
- Plugin-related corruption  
- Disputed item-loss claims  
- Unsafe or incorrect restores  

---

## Key Systems

### Snapshot System
- Automatic snapshots on **death (pre-drop)**, **join**, and **quit**
- Manual snapshots via command
- Timestamped, ordered, per-player retention
- Configurable FIFO retention

### Undo-Safe Restore System
- Restore from any retained snapshot
- Supports online and offline players
- Automatic `PRE_RESTORE` snapshot before every restore
- All restores are undoable

### Inspection & History
- Read-only inventory previews
- Ordered snapshot timeline (newest → oldest)
- Snapshot metadata: timestamp, trigger, optional label or note

### Diff Tooling
- Snapshot ↔ snapshot comparison
- Per-slot item differences
- XP delta reporting
- Optional NBT-aware diffs
- Exportable diff reports

---

## Outcomes

- Recover inventories without rollbacks  
- Undo restores safely  
- Resolve disputes with objective evidence  

---

## Characteristics

- Deterministic snapshot ordering  
- Undo-safe by design  
- Audit-ready  
- YAML-based storage  
- Async I/O  
- Admin-only (no gameplay impact)

---

## Requirements

- Paper / Spigot **1.13+**
- **Java 17**

---

## Storage

Snapshots are stored per player:

plugins/InvSafe/data/<uuid>.yml

Optional compression:
```yml
storage.compression: gzip
```
