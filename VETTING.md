# Skill Vetting Checklist

All skills must pass every critical check before being merged into this repo. Medium-risk items require documented justification. Any high-risk item is grounds for rejection.

Full security framework: `knowledge/architecture/SKILL-SECURITY-FRAMEWORK.md` in KOOKY-OS.

---

## Critical checks (all must pass)

### 1. Source legitimacy
- [ ] Repository is public and has a LICENSE file (MIT or Apache 2.0 preferred)
- [ ] Last commit is within 6 months (not abandoned)
- [ ] Repository owner has credible history (> 5 public repos, or known org)

### 2. No dynamic code execution
- [ ] No `eval()`, `Function()`, or equivalent runtime code evaluation
- [ ] No shell command execution (`exec`, `spawn`, `child_process`, `subprocess`) unless the skill's explicit purpose is a sandboxed script

```bash
grep -ri "eval\|Function(\|exec\|spawn\|child_process\|subprocess" skills/<name>/
```

### 3. No credential access
- [ ] Does not read environment variables containing secrets (`API_KEY`, `TOKEN`, `SECRET`, `PASSWORD`)
- [ ] Does not read files outside the workspace

```bash
grep -ri "api.key\|secret\|token\|password\|process\.env\|os\.environ" skills/<name>/
```

### 4. Network calls are documented and scoped
- [ ] Every external URL in the skill is listed in SKILL.md under `requires` or in a `# Network` comment
- [ ] No calls to unknown or hardcoded third-party domains that are not part of the skill's stated purpose

```bash
grep -ri "fetch\|requests\.\|http\|curl\|wget" skills/<name>/
```

### 5. Filesystem access is workspace-only
- [ ] Writes only to `/workspace` or a temp dir
- [ ] No directory traversal (`../`) that could escape the workspace

```bash
grep -ri "fs\.write\|open(.*w\|path\.join.*\.\." skills/<name>/
```

### 6. Dependencies are minimal and audited
- [ ] Dependency count is below 30
- [ ] `npm audit` (or equivalent) shows no critical vulnerabilities

---

## Risk matrix reference

| Factor | Low (approve) | Medium (justify) | High (reject) |
|--------|---------------|-----------------|---------------|
| Install count | > 1000 | 100-1000 | < 100 |
| Code size | < 200 lines | 200-1000 | > 1000 |
| Dependencies | 0-10 | 11-30 | > 30 |
| Network calls | None | Known APIs only | Unknown URLs |
| Filesystem | Workspace only | System read | System write |

If all factors are Low, approve with monitoring. One or two Medium factors require a written justification in the PR. Any High factor is a rejection unless there is an exceptional documented reason.

---

## Sandbox test (recommended before merging)

```bash
docker run -it --rm \
  --name skill-test \
  --network none \
  -v /tmp/skill-test:/workspace \
  ubuntu:22.04 \
  bash -c "cd /workspace && ./run.sh"
```

Monitor for unexpected network connections, file access outside `/workspace`, and abnormal CPU/memory usage.

---

## PR review sign-off

Before merging, the reviewer must leave a comment confirming:

```
Vetting complete:
- Source legitimacy: pass
- No dynamic execution: pass
- No credential access: pass
- Network calls documented: pass / N/A
- Filesystem scoped: pass
- Dependencies audited: pass
Trust level: official | curated | community
```
