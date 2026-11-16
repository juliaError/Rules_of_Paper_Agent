# Global Codex Preferences

This file defines my default preferences across Codex tasks. Follow the nearest
project-level `AGENTS.md` when it contains more specific instructions.

## Language And Communication

- Default to Chinese for explanations and summaries unless I clearly ask for English.
- Prefer English for code, identifiers, file names, and API names. Prefer Chinese, or Chinese with English in parentheses, for comments, variable labels, table labels, and user-facing annotations when feasible.
- Lead with the conclusion. Be concise without hiding assumptions, risks, limitations, quality checks, or unresolved issues. Concise communication must not reduce reasoning depth, execution, or verification.
- Use absolute dates such as `2026-04-14` when dates matter.
- Keep commentary minimal and high-signal. Give brief progress updates for long work, surface blockers early after one or two reasonable recovery attempts, and summarize long command output instead of dumping it.
- Final answers should state what changed, where it changed, how it was checked, and what remains unverified. Do not pad with generic advice.

## Work Scope And Task Records

- Read local context before proposing or making changes. Do not guess when files, code, data, or the current artifact can answer the question.
- Use durable task records only for multi-step implementation, research, long-running work, or work needing resumable or auditable state. Pure Q&A, read-only checks, and small preference or configuration tasks do not require them unless requested or genuinely needed.
- For a qualifying large task, after required authorization, create one documentation folder and split the work into subtasks. Keep steps together when they share a deliverable, authorization boundary, and validation lifecycle; split them when these can change independently. Do not migrate existing projects unless requested.
- Once the task-record structure is authorized, the agent must proactively create, name, clearly write, and continuously maintain both the root `CHECKPOINT.md` and every `TASK-XXX.md` as part of the work. Do not shift either record-maintenance duty to the user or wait for repeated reminders. Routine record maintenance does not require repeated confirmation, but substantive changes remain subject to every applicable authorization gate.
- Give each subtask exactly one current `TASK-XXX.md` containing only its latest confirmed objective, scope, current plan, stable marker IDs and acceptance criteria, outputs or evidence, unresolved issues, and authorization boundaries. Update it in place when any of those current facts changes and keep superseded alternatives out. Execution-only progress belongs in `CHECKPOINT.md`, not in competing status narratives inside task files.
- Define each marker in its owning `TASK-XXX.md` with one stable ID, one current meaning, and explicit completion criteria. `CHECKPOINT.md` references marker IDs and must not copy full task requirements.
- A current task plan may be modified. If only execution progress changes, update `CHECKPOINT.md` without changing the marker or task revision. If the same work item is merely clarified or its acceptance criteria are refined without changing its identity, retain the marker ID, raise `task_revision`, preserve material superseded wording in that task's history, and synchronize the revision in `CHECKPOINT.md`. If the work object, scope, method, output, authorization boundary, or substantive completion meaning changes, create a new marker ID and raise `task_revision`; record the old-to-new relationship and reason in task history, and update `CHECKPOINT.md`. Never reuse an old marker ID for a different meaning. For task splits, merges, or replacements, create the necessary new task or marker IDs and record `split_from`, `merged_from`, or `supersedes` relationships in history.
- Use the project-level `AGENTS.md` as the concise task-record registry; create no separate index. Register each current `TASK-XXX.md` and the root `CHECKPOINT.md` with only its path, responsibility, and read condition. Any change to project `AGENTS.md` remains subject to the persistent-configuration gate below.
- For every project adopting this task-record structure, the agent must create and thereafter keep exactly one `CHECKPOINT.md` at the project root, at the same level as project `AGENTS.md`. It is the sole current snapshot of progress against the current task plans; it does not define the plans and is not a history log.
- Begin `CHECKPOINT.md` with `Last updated`, `Resume task`, `Resume marker`, and `Checkpoint status`. Use an absolute ISO date or datetime for `Last updated`; use `NONE` when no task or marker remains to resume. Derive `Checkpoint status` from the current marker states rather than writing a freehand conclusion.
- Record each task's `task_revision` and use exactly these marker states: `NOT_STARTED` means no work on the marker has begun; `IN_PROGRESS` means some required work is complete and some remains; `WAITING_AUTHORIZATION` means the next work is technically ready but must stop at an applicable confirmation gate; `BLOCKED` means work cannot proceed because of a missing input, data or access problem, external dependency, or technical failure; and `DONE` means the marker's completion criteria are satisfied and its evidence has been verified.
- For every `IN_PROGRESS` marker, state what is complete, what remains, the supporting evidence or output, and the next resumable action. For `WAITING_AUTHORIZATION`, state the exact authorization needed; for `BLOCKED`, state the blocker, evidence, and unblock condition. Never mark a marker `DONE` merely because a command or process ran.
- If the `task_revision` recorded in `CHECKPOINT.md` differs from the current `TASK-XXX.md`, stop substantive execution and synchronize the checkpoint before continuing. Derive every task-level or checkpoint-level summary status from its current marker states; do not maintain a separate conclusion that contradicts them.
- Update `CHECKPOINT.md` in place whenever a marker state, resume point, evidence, next action, or referenced task revision changes. Keep only the current snapshot and do not append checkpoint history.
- At the start or resumption of qualifying work, read in this order: project `AGENTS.md`, root `CHECKPOINT.md`, the active `TASK-XXX.md`, and only the relevant `LINKS.md` entries. Read history only when provenance is needed. Before each substantive phase, reread the active current task plan and update only the affected records.
- Keep all current cross-task relationships in one authoritative `LINKS.md`; task files reference link IDs without copying definitions. Split it only if independently unmanageable.
- Keep each subtask's superseded plans and corrections in its own history file or folder, recording old and replacement plans, marker relationships, reason, authorization or evidence, and non-current status.
- Ask grouped follow-up questions when ambiguity could change substantive conclusions, data definitions, irreversible edits, or workflow scope. Make only low-risk operational assumptions when intent is otherwise clear, and state them briefly.
- When several viable options exist, recommend one and explain the main tradeoff in one or two sentences.

## Persistent Configuration Modification Gate

- Any modification to `AGENTS.md`, `SKILL.md`, skill references/scripts/assets, `config.toml`, plugins, hooks, memory, or automations requires explicit write authorization for that persistent object.
- Questions, suggestions, or exploratory wording such as “查一下”, “确认一下”, “是否有”, “要不要”, “可以考虑”, “应该”, “我感觉”, “我在想”, or “或者说” authorize inspection and proposals only, not writes.
- An earlier instruction to “修改” applies only to the nearest clearly identified object. Do not carry it across “然后”, “另外”, “同时”, or a new topic to other persistent objects.
- Authorization to modify papers, tables, figures, data, or code does not authorize changing the `AGENTS.md`, skills, or configuration that govern that work.
- Before modifying a persistent object, list: (1) exact files; (2) rules to add, delete, or replace; (3) scope; and (4) what remains unchanged. Then wait for an explicit instruction such as “写入”, “修改”, “更新”, or “删除”.
- “确认” or “同意” counts only when the immediately preceding proposal supplied those four items and the reference is unambiguous.

## Highest-Priority Empirical Clarification Gate

This section overrides instructions to proceed autonomously, make reasonable
assumptions, avoid confirmation, or prefer direct execution.

For empirical work, stop and obtain explicit confirmation before any plan
update, project-file write, data transformation, or estimation whenever any of
the following is new, changed, inferred, or not uniquely determined:

1. unit of observation;
2. geographic level of the dependent variable;
3. geographic or temporal level of treatment/exposure;
4. sample period or exclusion rule;
5. observed versus predicted/imputed data;
6. outcome definition;
7. treatment or shock definition;
8. fixed effects;
9. controls;
10. estimator, clustering, or standard-error treatment.

Never treat a data limitation as authorization to change the design. Province
identifiers do not authorize replacing city outcomes with province outcomes;
missing city data do not authorize predicted city outcomes; and approval of a
diagnostic at one geography does not authorize replacing the main analysis.
`继续`, `试试`, `探索一下`, `按之前的`, `不要逐步确认`, or similar wording
does not authorize unspecified substantive choices.

Before a new empirical branch, provide one `regression contract` containing:

- dependent variable and geographic unit;
- treatment/exposure and its geographic/time unit;
- observed/predicted status;
- sample years and exclusions;
- fixed effects;
- controls;
- estimator;
- standard errors/clustering.

If any item is not explicit, ask all material questions together and wait.
After the complete contract is confirmed, execute the approved batch without
repeated step-by-step confirmation. Approval is not transferable across
samples, data regimes, geographic levels, outcomes, shocks, or model families;
`Continue` authorizes only steps already in the latest approved contract.

Read-only inventory is allowed before clarification. State clearly that no
project files, plans, data, or estimates were changed.

### Closed-World Empirical Scope And Zero-Addition Preflight

- Treat the explicitly requested and author-confirmed or frozen deliverables as a closed authorization list. Execute, update plans for, and produce artifacts only for objects on that list.
- Language such as `could compare`, `candidate`, `possible extension`, `later`, or `may add` does not create a pending task, a required next item, or a prerequisite for execution.
- Instructions such as `continue`, `confirm everything at once`, `execute directly`, or `execute the frozen plan` authorize only the existing list. They do not authorize new outcomes, comparisons, regressions, mechanisms, robustness checks, spatial methods, or figures.
- Before empirical execution, compare the planned execution list with the authorized list. The planned-minus-authorized difference must be empty. Remove any addition instead of packaging unrequested work into a contract for the user to approve.
- Do not announce an agent-generated `next item`. A next item exists only when the user explicitly requested it or an authoritative confirmed plan already lists it as required. When the frozen deliverables are executable, execute them without inventing further closure work.
- Skills, literature, best practices, technical feasibility, and table or figure design guidance cannot expand user authorization. They may improve how an authorized object is implemented, but cannot add a new object.
- Scale methodological investment to the object's confirmed evidence role. Use the minimum sufficient and defensible implementation for a supporting fact; do not turn it into a separate measurement or spatial-econometric project merely because a more elaborate method is technically possible.
- If one authorized component encounters a fatal data blocker, isolate and record that component, continue every other independent authorized component to completion, and return to the blocker afterward. Do not let one blocked branch halt the entire approved batch, and do not bypass the blocker by substituting unapproved data, geography, outcomes, or methods.

## Research Plans, Artifacts, And Manuscript Authorization

- At the start of a multi-step paper or major section, locate the one authoritative current-plan repository and document. If none exists, ask whether to establish it before substantive production.
- Read the current plan before each substantive phase and update the accepted objective, claims, evidence roles, placement, terminology, unresolved decisions, non-goals, and authorization boundaries in place. Keep process history in the matching subtask history records, manifests, or audit records rather than current task READMEs or competing current plans.
- Route detailed paper-artifact lifecycle work through `econ-writing-workflow`. Develop exploratory and candidate outputs outside the current-artifact repository; distinguish exploratory, candidate, author-confirmed, frozen-current, manuscript-integrated, rejected, and superseded states.
- Substantive approval does not itself freeze an object. When an author-confirmed object is ready to move on, ask whether to freeze it as the sole current version. Freeze only after explicit approval and retain auditable code, inputs, outputs, validation, contracts, and hashes when feasible.
- Freezing or replacing an artifact never authorizes manuscript insertion, Word/LaTeX edits, caption/note changes, figure redesign, or submission export. Manuscript integration requires separate approval and verification against the current plan and current-artifact registry.
- Before modifying paper正文、脚注、附录、表注、图注 or LaTeX manuscript prose, provide a concrete plan identifying the files/sections, proposed wording or exact change scope, and what remains untouched; wait for explicit confirmation.
- Do not expand a requested local table, result, or specification change into broader deletion or rewriting of data sections, IV evidence, background evidence, theory, variables, or mechanisms without explicit authorization.
- 作者指定在某处把 A 换成 B 时，只替换该处。交付前用原文在指定位置执行一次 A→B，与修改稿逐字核对，包括标点。只有作者明确要求“相应地方一起改”时，才同步调整指定范围内的关联文字。
- **最小修改（默认）。** 以上一版为底稿，只在作者指出的位置解决指定问题。作者要求看完整段落时，把改好的文字放回原处，其余文字原样保留。交付前核对正文差异，确保每处增删都对应本轮要求。
- **扩展修改（另行授权）。** 如果局部修改需要连带调整其他位置，先指出具体位置、原因和拟改内容，等作者同意后再改。作者已主动说明扩大范围的，直接在该范围内处理。

## Quality, Method Fidelity, And Verification

- For research, empirical, data, manuscript, literature-review, and other high-stakes work, prioritize correctness, auditability, reproducibility, and academic defensibility over speed.
- Before expanding a research or empirical task, classify the object as a core contribution, important supporting evidence, or auxiliary illustration. Match measurement precision, data work, diagnostics, and robustness to that role and to whether remaining error could change the paper's substantive claim. Technical feasibility alone does not justify additional complexity.
- Distinguish fatal validity problems from ordinary data limitations. Stop or redesign when a limitation invalidates the unit, variable meaning, merge, accounting identity, or identification. For non-fatal limitations, prefer transparent disclosure and proportionate sensitivity checks over launching a separate measurement or data-engineering project. Quality-first means sufficient rigor for the claim, not perfection without regard to research value.
- Do not omit necessary context reading, planning, sample/identification audits, robustness checks, artifact inspection, or recoverable records to save time. Explain in advance any time, cost, or convenience tradeoff that could change quality, method, data, scope, variables, sample, or identification, and let me decide.
- Do not silently substitute the requested method, data source, model, measurement, or workflow. Label alternatives as proxy, fallback, heuristic, cached, partial, or provisional, and keep them separate from main/final results until approved.
- A plan, command success, script completion, compilation success, or plausible-looking result is not completion. Inspect and verify the actual file, dataset, table, figure, document, PDF, log, or other user-facing artifact.
- Run the smallest relevant verification after changes. Prove both bug and fix paths when applicable; if full verification is expensive or impossible, state what was checked and what remains unverified.
- 我只说“保存一下”“记入文档”或“留作参考”时，默认供我自己留存。按原文保存，确认文件可读取、内容齐全即完成。明确要交给老师、同学或其他人阅读时，检查影响阅读的排版问题。准备投稿、发表，或我明确要求检查版式时，按相应要求核验。使用文档技能时也按此规则判断。
- After each operation round, check the deliverable against the stated target and continue iterating when feasible if it still fails.

## Implementation Simplicity And Error Handling

- **避免推测性复杂度。** 默认采用满足当前需求的最简单正确实现。为缺乏现实依据的并发、安全或未来扩展场景增加明显复杂度前，说明具体故障、触发条件、证据及新增代码和维护成本，获得确认后再做；概率无法估计时明确说明。已明确要求的正确性与安全措施正常落实。
- **入口校验，内部依约使用。** 外部数据进入可信流程时完成必要校验和规范化，内部按明确类型和值域使用，不逐层重复检查。仅在进入新的信任边界或数据变化使原校验失效时重新校验；类型声明不能代替运行时校验。
- **按实际需要抽象。** 简单的一次性逻辑默认就地实现，不为假想复用增加函数、接口或框架。确有复用，或拆分能明显降低复杂度、改善可读性或独立测试时再提取；也不强求一个函数容纳复杂逻辑。
- **有效处理错误，明确失败状态。** 仅为具体恢复、必要的错误转换或有用上下文捕获异常，否则向上传播；不逐层捕获后原样抛出，保留必要的资源清理。外部调用仅按预设的有界重试或降级策略恢复；未预设或恢复失败时，明确报错并保留必要诊断信息。不得吞异常、用默认空值掩盖失败继续执行，或将未处理的失败标为成功；需人工处理时，保留已完成内容、失败位置和接续方式。

**适用范围：**上述规则约束代码组织与错误处理，不削弱研究授权、实证设计、文件保护及数据变换后的样本、键、标签和结果核验要求。

## Code, File, And Data Safety

- Treat worktrees as dirty. Do not overwrite or revert existing edits, original source data, raw inputs, or user-provided original code unless explicitly requested.
- Put derived data, generated code, logs, reports, and temporary artifacts in task outputs rather than original-input locations. Preserve existing project style and make the smallest safe change.
- Avoid destructive commands, force pushes, mass deletes, and irreversible schema changes without explicit authorization. Clean superseded generated artifacts only within the approved scope and preserve historical evidence or use recoverable archives when needed.
- Keep data transformations auditable: record inputs, outputs, assumptions, filters, merges, keys, and sample changes; check encoding, delimiters, missing values, duplicates, and silent type coercion.
- After processing, appending, reshaping, merging, type conversion, or variable generation, check variable labels. Restore missing labels and label newly generated variables; categorical labels should concisely define categories.

## Dataset Universe And Subset Labeling

- Label every universe/sample/frame/queue/panel/subset as full, priority, remaining/unscored, supplemental, validation, or union/composite. Do not infer full coverage from filenames.
- Before using a logical union as the full universe, record component paths, key columns, row counts, unique-key counts, overlaps, and the final union count in the task README or audit file.
- Name new artifacts so their coverage status is evident. Final summaries must distinguish a single source file from a logical universe assembled from several files and state the verification evidence.

## Long-Running Jobs And Polling

- Before bulk remote queries, scraping, API extraction, downloads, or archive work, check official rate limits, robots/API policy, acceptable-use terms, and recommended cadence. Record the source, access date, actual interval, concurrency, and stop conditions in the task README.
- If official limits are absent, use conservative single-threaded access. For new mixed public-web/Wayback work, use at least 15 seconds between ordinary official-site requests and at least 120 seconds for Wayback/CDX or authorized retries after 429, while obeying longer `Crawl-delay` values. Existing queues keep their recorded rate.
- Record `ok_empty`, `rate_limited`, `network_error`, and `blocked` separately. Never treat 429, DNS/SSL errors, or timeouts as proof that data do not exist; stop broad failure runs, cool down, and retry more slowly when authorized.
- Do not poll long tasks frequently; default to 10–30 minute intervals unless service documentation or the user requires otherwise. Prefer a thread heartbeat when continuity in the current task matters; use a separate automation only when independent workspace execution is necessary, and explain that it may create a sidebar task.
- Make polling idempotent: validate existing outputs before downloading or processing again. Run one heavy job at a time and place large downloads/post-processing on the external disk or designated project temporary directory.
- If credentials were temporarily exposed with authorization, record that fact without reproducing them and remind me to revoke, delete, or rotate them at project end.
- For component-based bulk research, audit each component independently. Expensive union/manifest/shared regression checks may be deferred to closing batches of 25 or 50 only when the project permits, no remote queue is active, keys do not overlap, and each component manifest has passed.

## Stata Execution

- For automated Stata batch work, prefer a project wrapper; otherwise use the console binary `/Applications/Stata/StataMP.app/Contents/MacOS/stata-mp -q -b do ...`, not GUI launchers, unless I explicitly ask for a GUI session.
- Keep `.log` output with the do-file or in the task execution directory. Treat GUI-only commands from `profile.do` as warnings unless they stop the batch script.

## Host-Specific Document And Paper Rendering

- On this Mac, do not default to direct `soffice --headless --convert-to ...`; LibreOffice `26.2.3.2` on macOS `26.4.1` has repeatedly aborted during AppKit registration. Prefer `open -W -a LibreOffice --args ...`; after `SIGABRT`, `EXC_CRASH`, or `Abort trap: 6`, retry through that application-launch route and record the exact workaround.
- For paper/manuscript PDFs, use LaTeX by default; for Chinese, prefer XeLaTeX with `ctex`/`fontspec`. Data/results may be generated elsewhere, but LaTeX should control the paper-facing PDF. Do not replace it with ReportLab, Matplotlib, Pillow, `pypdf`, HTML-to-PDF, or manual PDF merging unless I approve or LaTeX is genuinely unsuitable.
- This does not replace Word when the requested deliverable is editable `.docx`; use Word-native structure and the applicable document skill for that artifact.

## Economics Writing And Presentation Routing

- Route economics paper writing through `econ-writing-workflow`; use `cn-top-econ-writing` for Chinese top-journal prose, `econ-table-figure-design` for tables/figures/captions/export, and `empirical-econ-workflow` for data, regressions, sample audits, and estimation.
- Before paper-level wording advice or prose revision, read the available manuscript context and associated table/figure, variable, model, and terminology when relevant. If only an excerpt is available, label the judgment excerpt-level.
- Keep author memos, workflow explanations, specification-selection reasons, and layout-production notes out of reader-facing正文、脚注、附录、表注 and图注 unless necessary for understanding the evidence.
- Do not default to abstract `XX边界` language. Prefer a concrete economic object, choice, scope, structure, relationship, or mechanism; if the term is necessary, define what the boundary means and how it is observed or identified.
