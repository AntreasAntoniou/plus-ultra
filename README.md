# Plus Ultra

Plus Ultra is an Agent Skill and a dependency-free Claude Code hook adapter for a strict workflow:
two blind read-only proposals, one arbiter-approved plan, one implementation, and a fresh
plan-blind reality check.

## Status by host

| Host | Status |
|---|---|
| Claude Code | Enforceable after the included hook is installed, configured, and verified |
| Codex | Convention-only; this repository does not ship or claim a verified Codex hook |
| Other agent hosts | Convention-only until an equivalent adapter is implemented and tested |

This distinction matters: instructions can encourage a workflow, while only a configured host
integration can block a tool call or stop a turn.

## Install the skill

```sh
npx skills add AntreasAntoniou/plus-ultra
```

Or copy/symlink the repository into the skills directory recognized by your agent host. The skill entry point is [`SKILL.md`](SKILL.md).

## Optional Claude Code enforcement

1. Put [`scripts/plusultra.py`](scripts/plusultra.py) on your `PATH` as `plusultra`.
2. Merge the three hook entries from
   [`examples/claude-settings.json`](examples/claude-settings.json) into your Claude Code settings.
3. Run `plusultra doctor` and confirm all three events report `ok`.

Do not replace an existing settings file wholesale; merge the hook entries with the hooks already
configured on your machine.

## Test

```sh
python3 -m unittest discover -s tests -v
python3 scripts/plusultra.py
```

## Security model

The adapter denies a useful set of obvious filesystem, Git, package-manager, container, and HTTP
mutations. Its shell recognition is heuristic. It cannot make arbitrary shell or interpreter code
safe, and it is not a sandbox. See [`SECURITY.md`](SECURITY.md).

Licensed under the [MIT License](LICENSE).
