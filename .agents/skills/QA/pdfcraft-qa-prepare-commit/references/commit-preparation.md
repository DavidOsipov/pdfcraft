# Staged-candidate preparation

Apply [task contract](contract.md). Prepare coherent candidate under existing user authority; no publication, commit, installation or broader product-repair grant. Preparation may already authorize staging and confirmed in-scope fixes; never request same permission twice. Tests-only: retain valid regression and report finding; no silent production fix.

## Scope and deliberate staging

Resolve repository root, active index, object format, HEAD/baseline, merge/rebase state. Unborn branch: record it; define empty-tree baseline explicitly. Unresolved index conflicts/unsupported in-progress operation: stop. Read applicable instructions, staged manifests/tests, build scripts, hooks and production changes.

Inspect staged versus baseline, working versus index, and untracked inputs separately. Disable external diff/textconv for source evidence. Review renames, deletions, binary/generated files, lock/config changes and required new fixtures. `git diff --cached --check` checks whitespace/conflict markers, not bugs. Before selection, record existing staged paths, modes, blob IDs and owned hunks. Sources: [Git diff](https://git-scm.com/docs/git-diff), [Git ls-files](https://git-scm.com/docs/git-ls-files).

Select literal paths; mixed files need reviewed interactive hunks/index patches. Stage whole file only when every change belongs. No blanket `git add -A`, reset, stash, clean or source checkout for convenience. Avoid later `commit -a` or path-specific commit shortcuts; they may record another candidate. Preserve/report unrelated staging; testing grants no inclusion authority. If outside intended commit, reconcile scope before whole-index readiness. Sources: [Git add](https://git-scm.com/docs/git-add), [Git commit](https://git-scm.com/docs/git-commit).

Use argv arrays, literal pathspecs, supported NUL-delimited input. Keep opaque manifest path bytes; split metadata at first TAB, not whitespace. Check platform name/case mapping; never replace undecodable characters silently. Leading dash, newline or pathspec metacharacter must not alter selection. Never stage private documents, credentials, corpus dumps or transient reports merely for test discovery.

## Freeze and materialize the complete index

Reviewed recipe, not unattended script/universal exporter. Use compatible installed Git and new owned destinations. Needs no product commit, source reset, stash or new dependency. Full index includes unchanged dependencies and staged additions/deletions; changed-path copying is insufficient.

1. Supported ordinary index: copy resolved active index privately. Compare digest before/after capture; abort on change, index lock or inconsistent entries. Per child set `GIT_INDEX_FILE` to copy; never run `read-tree` against user's index. Run `write-tree` without `--missing-ok`. Record complete tree ID, object format, baseline HEAD, logical mode/blob/stage/path manifest, staged patch digest and relevant configuration. `write-tree` creates objects and may refresh cache metadata; logical preservation does not promise unchanged Git bytes. Sources: [Git environment](https://git-scm.com/docs/git), [write-tree](https://git-scm.com/docs/git-write-tree).
2. Second alternate-index path must not exist; zero-byte index is invalid. Run `read-tree --no-sparse-checkout <tree>` without working-tree update/submodule recursion. Compare full entries with recursive `ls-tree --full-tree -z <tree>`. Identify intent-to-add: writing tree does not stage those files. Unmerged entries, missing objects or unsupported split/sparse dependencies block export. Never reconfigure user's index for convenience. Sources: [read-tree](https://git-scm.com/docs/git-read-tree), [index format](https://git-scm.com/docs/index-format).
3. Before checkout review effective tree and repository-local/global attributes, filter drivers, EOL/encoding/LFS conversion and Git configuration. Using fresh alternate index, run `git --attr-source=<tree> checkout-index --all --ignore-skip-worktree-bits --prefix=<absolute-new-empty-directory>/` from source root. Keep trailing slash. No forced overwrite/source-index update. `--all` alone may omit skip-worktree entries. Attribute-source selection does not neutralize external precedence or filter execution; unreviewed filters block checkout. Sources: [checkout-index](https://git-scm.com/docs/git-checkout-index), [attributes](https://git-scm.com/docs/gitattributes).
4. Verify every path/mode; reject missing/extra files before tests. Compare plain export with raw `cat-file blob` bytes. Approved checkout transformations need verified representation/configuration; record policy with receipt. Link-text file is not actual symlink. Gitlinks name submodule commits, not files. Unsupported modes, escaping links, unavailable required submodule content, path collisions or missing external inputs block dependent execution. No automatic fetch, submodule update or filter installation. Sources: [cat-file](https://git-scm.com/docs/git-cat-file), [submodules](https://git-scm.com/docs/gitsubmodules).
5. Run reviewed checks inside materialization with source-repository `GIT_*` pointers removed and owned outputs/caches. Compare tracked source/configuration/fixture-input digests before/after execution, separately from declared generated outputs. Formatter/hook/test rewriting inputs invalidates later pass for original tree. Reconcile authorized changes, restage when needed, validate fresh materialization. Export is no execution sandbox: builds may write elsewhere, access credentials or launch children. Use approved isolation/resource controls. Required Git metadata, local path dependencies or generated inputs need verified faithful environment; otherwise block check. Never fake inputs or substitute dirty-tree execution.

`git archive <tree>` may succeed while `export-ignore` omits tests. Commit/tag archives may also transform files through `export-subst`; bare tree lacks substitution commit context. Every alternative exporter must prove complete composition, representations and required dependencies against same manifest. Sources: [Git archive](https://git-scm.com/docs/git-archive), [archive attributes](https://git-scm.com/docs/gitattributes#_creating_an_archive).

Capture is optimistic against ordinary writers. Before/after hashes/tree checks detect demonstrated drift, not atomicity or intermediate changes. Never hide limitation with improvised index-locking/commit subsystem.

## Investigate a plausible bug before repairing it

Trace changed contract through callers, state transitions, parsing bounds, error/rollback paths and resource ownership. Rank hypotheses by actual change/impact, not checklist count. Record violating input, expected facts, reachability and alternatives. Distinguish introduced regression, pre-existing defect, invalid test, environment/resource failure and unresolved specification.

Before confirmed repair, demonstrate intended pre-fix RED in owned environment. Fixture-open failure before seam, missing import/compiler, zero selected tests, unrelated panic or generic timeout is no hypothesis proof. Include accepted control; rejecting every input makes oracle useless. Falsified hypothesis: retain counterevidence, avoid speculative production edit. Ambiguous expectation needs contract decision, not guessed value.

Apply smallest already-authorized fix; obtain GREEN with unchanged expectation. Stage required deterministic regression. Existing working-copy repair: stage only intended hunk/inputs, then verify new candidate. For causal evidence use authorized isolated pre-fix/reverted-fix copy; never undo user's work. Never accept snapshot, suppress gate or change expectation merely to match output. Native selection, doctests and unavailable runtime handling: [Rust workflow](rust-workflow.md).

## Optional adversarial exploration

Use properties/fuzzer for concrete relevant domain missed by named tests. Start with small accepted synthetic input and independent expected facts; vary named boundary, grammar rule or state transition. Example: page indices around zero/count; rejection preserves valid session graph/history, accepted operations retain explicit page identities. Confirm fixture opens and intended edit is reached. Earlier malformed-byte parser rejection tests another property.

Use approved existing tools or short deterministic table; no proptest/cargo-fuzz/toolchain addition merely for this skill. Same-parser round trip, generated expected output or no-crash assertion alone cannot prove semantics. Keep healthy/plausible violating controls; account for rejected/eligible/executed cases.

Before launch cap cases, sequence length, bytes/depth, shrinking, workers, process-tree deadline, memory/output retention; assign cleanup. Retain exact original failure and minimized input, seed, generator/build/version/options, source/fixture hashes and failure mechanism. Replay concrete input alone from fresh state; seed alone is insufficient. Corpus minimization differs from failure-input minimization. Classify timeout, launch error, reset failure and cleanup separately. Follow [generation controls](generative.md); no automatic full workspace mutation/overnight campaign.

## Close each cycle against current evidence

After authorized repair, stage reviewed hunks, capture new tree, repeat relevant audit/validation. Retain earlier findings/first failures. Reuse evidence only with explicit unaffected-source/configuration/fixture/boundary argument. Changed tree inherits no blanket pass. Preserve required current gates without imposing every expensive technique on every change. Missing required execution stays incomplete.

Set cycle/time budget; initial cap can be three repair cycles within task budget. Stop when complete; exhaustion: report unresolved work/next action. Never iterate until AI invents no further concerns. Authorized useful separate review receives frozen inputs and task/contract, not author's persuasive narrative. Agreement proves neither runtime behavior nor statistical independence. Resolve material findings with reachable test, source argument or retained uncertainty.

Review configured hooks/approved formatting effects. Hooks may change index; Git may reread it before commit. Index-changing tool/hook expires affected results: rematerialize and validate final selection. Never hide failed gate with `--no-verify`. Preparation cannot guarantee later commit contents under other flags/hooks. Sources: [Git hooks](https://git-scm.com/docs/githooks), [Git's v2.56 commit handling](https://github.com/git/git/blob/v2.56.0/builtin/commit.c).

Immediately before report compare current logical index/tree and baseline HEAD against validated receipt. Record tools/config/fixtures and materialization identity. Changed: receipt stale. Metadata-only refresh need not invalidate unchanged logical content. Later changes expire readiness checkpoint; no atomic future-commit promise.

| Readiness receipt | Required content |
| --- | --- |
| Selection | Intended change/authorized hunks; pre-existing staging, exclusions, ownership conflicts |
| Identity | Baseline/HEAD, object format, complete staged tree/manifest, patch, materialization/config/fixture identities |
| Findings | Hypotheses, confirmed cause, counterevidence, RED/fix/GREEN links, unresolved severity/owner |
| Execution | Exact commands/cwd/toolchain/features, actual named tests, first failures/retries/skips, bounded exploration, cleanup |
| Decision | Ready within scope; not ready for confirmed blockers; incomplete for missing evidence; remaining work/expiry |

Use [evidence guidance](evidence.md). Bounded preparation needs no new committed metadata file. Stop before commit/push/PR unless separately requested. Skill credit is not operator Git identity; never change Git user settings or attribute unrelated product work to David.

## Research basis

Original method informed by inspected workflows: [Sentry's commit skill](https://github.com/getsentry/skills/blob/f57ada2d0b640406ea7e25b11d636c530e77c58b/skills/commit/SKILL.md), [Superpowers' fresh-evidence guidance](https://github.com/obra/superpowers/blob/bb92a77741419a4ab5f06e711a283343f1ada0c3/skills/verification-before-completion/SKILL.md), and [Trail of Bits' property-testing guidance](https://github.com/trailofbits/skills/blob/5c99c03fb8a9ea568432ecbcba5d86e9f4ac2bf0/plugins/property-based-testing/skills/property-based-testing/SKILL.md). No redistribution of their text/code/templates; separate licences retained. Sample cannot establish exhaustive Internet absence. Documentation/synthetic Git controls support mechanics, not PdfCraft execution, automatic activation or bug-free results.
