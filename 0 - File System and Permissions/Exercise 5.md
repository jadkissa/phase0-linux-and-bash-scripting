# Exercise 5 — Sticky Bit, SetUID, SetGID (Research)

### Sticky Bit (`chmod +t`)

**What it does:** In a directory with sticky bit, only the file OWNER can delete or rename files — even if others have write permission.

**Symbol:** `t` at the end of permissions: `drwxrwxrwt`

**When to use:** Shared directories where users should only delete their own files (like `/tmp`)

**Example:**
```bash
mkdir shared
chmod +t shared
ls -ld shared   # Shows drwxrwxr-t