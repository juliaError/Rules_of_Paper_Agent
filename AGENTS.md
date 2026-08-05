# Global Codex Preferences

This file defines my default preferences for Codex across tasks.
If a repository contains its own `AGENTS.md`, follow the repository guidance first and use this file as the fallback.

## Language And Style

- Default to Chinese for explanations and summaries unless I clearly ask for English.
- Prefer English for code, variable names, function names, file names, and API identifiers unless there is a strong reason not to.
- Prefer Chinese, or Chinese with English in parentheses, for code comments, variable labels, column labels, table labels, and user-facing annotations when feasible.
- Start with the conclusion, then give the minimum necessary explanation. This is a presentation rule only; it must not be used to reduce the depth, duration, planning, execution, or verification of the underlying work.
- Be concise in user-facing communication, but do not hide important assumptions, risks, limitations, intermediate quality checks, or unresolved issues.
- When dates matter, use absolute dates such as `2026-04-14` instead of only saying "today" or "yesterday".

## Working Style

- Read local context before proposing or making changes. Do not guess when the codebase or files can answer the question.
- For every task, create or update a task README file that records the final objective and every step completed so far.
- Before starting each concrete step, read the task README first and confirm the current objective and workflow from it.
- When the workflow changes, record the versioned process clearly in the README, such as what `v1` did, what `v2` changed, and why, so earlier approaches remain traceable.
- Keep the README current as the task evolves so it can be used to resume work, audit decisions, and confirm the latest agreed process.
- Prefer doing the work directly only after the empirical or substantive task contract is complete and unambiguous, unless I explicitly ask for brainstorming, comparison, or design discussion only. This preference is subordinate to the `Highest-Priority Empirical Clarification Gate` below.
- For any unclear, underspecified, or ambiguous instruction, scope, data definition, variable definition, identification choice, destructive action, or output requirement, do not resolve it by guessing. State what is unclear, explain why it matters, and let the user make the final decision before proceeding.
- Only make low-risk operational assumptions when the user's intent is clear and the assumption does not affect substantive conclusions, data definitions, irreversible edits, or workflow scope; state those assumptions briefly.
- Ask follow-up questions whenever ambiguity has real downstream consequences and cannot be resolved from local context.
- When there are several viable options, recommend one clearly and explain the tradeoff in one or two sentences.

## Persistent Configuration Modification Gate

- 对 `AGENTS.md`、`SKILL.md`、skill 的 references/scripts/assets、
  `config.toml`、插件、hook、memory 和 automation 的任何修改，
  必须取得针对该持久对象的明确写入授权。

- “查一下”“确认一下”“是否有”“要不要”“可以考虑”“应该”
  “我感觉”“我在想”“或者说”等疑问、建议或试探性表达，
  只授权检查、分析和提出方案，不授权写入或修改。

- 一条消息中较早出现的“修改一下”“进行一些修改”，只适用于
  与它最近且明确指向的对象；不得跨过“然后”“另外”“同时”等
  转折或新增事项，把修改授权延伸到 AGENTS、skills 或其他持久配置。

- 对论文、表格、图形或代码的修改授权，不自动授权修改指导这些工作的
  AGENTS、skills 或全局配置。

- 修改任何持久配置前，必须先向用户列明：
  1. 准备修改的准确文件；
  2. 准备增加、删除或替换的规则；
  3. 适用范围；
  4. 保持不变的内容。
  然后等待用户明确说“写入”“修改”“更新”“删除”或同等明确指令。

- “确认”或“同意”只有在上一轮已经给出上述具体修改方案、且指代没有
  歧义时，才构成持久配置修改授权。

## Highest-Priority Empirical Clarification Gate

This section overrides all instructions to proceed autonomously, make reasonable
assumptions, avoid repeated confirmations, or prefer direct execution.

For empirical and research tasks, Codex must stop and obtain explicit user
confirmation before any plan update, project-file write, data transformation,
or estimation whenever any of the following is new, changed, inferred, or not
uniquely determined:

1. unit of observation;
2. geographic level of the dependent variable;
3. geographic or temporal level of the treatment/exposure;
4. sample period or exclusion rule;
5. observed versus predicted/imputed data;
6. outcome definition;
7. treatment or shock definition;
8. fixed effects;
9. controls;
10. estimator, clustering, or standard-error treatment.

Codex must never treat a data limitation as authorization to change the research
design. For example:

- Province identifiers in CFPS do not authorize aggregating city outcomes to
  provinces.
- Missing post-2017 city customs data do not authorize substituting predicted
  city outcomes.
- Approval of a province-level diagnostic does not authorize replacing a
  city-level main analysis.
- `继续`, `试试`, `探索一下`, `按之前的`, or `不要逐步确认` do not
  authorize unspecified substantive choices.

Before starting a new empirical branch, Codex must provide a one-block
`regression contract` containing:

- dependent variable and geographic unit;
- treatment/exposure and its geographic/time unit;
- observed/predicted status;
- sample years and exclusions;
- fixed effects;
- controls;
- estimator;
- standard errors/clustering.

If any item is not explicit, Codex must ask all material questions together and
wait for the user's response. Once the complete contract is confirmed, Codex
should execute the whole approved batch without repeated step-by-step
confirmation.

Previous approval is not transferable across samples, data regimes, geographic
levels, outcomes, shocks, or model families. `Continue` authorizes only the next
steps already contained in the latest explicitly approved contract.

Read-only inventory is allowed before clarification. Codex must state clearly
that no project files, plans, data, or estimates have been changed.

## Research Plan And Artifact State Management

- At the start of a multi-step paper or major paper section, first check
  whether the project has one authoritative current-plan repository and
  current-plan document. If it is missing, proactively ask me whether to
  establish it before substantive production. The repository may be a
  dedicated folder or one clearly identified authoritative document, but it
  must be the single source of truth for the latest accepted plan.
- Read the authoritative current plan before each substantive phase. Keep in
  it the latest objective, claim sequence, admitted evidence and paper roles,
  main-text/appendix placement, terminology, unresolved decisions, explicit
  non-goals, and authorization boundaries.
- When I approve, reject, narrow, or replace a plan, update the authoritative
  current plan in place during the same task. Do not leave competing or
  superseded plans looking current. Preserve process history in task READMEs,
  manifests, or audit records rather than parallel current-plan files.
- Develop exploratory and candidate outputs outside the current-artifact
  repository. Distinguish exploratory, candidate, author-confirmed,
  frozen-current, manuscript-integrated, rejected, and superseded artifacts.
  Do not present a candidate as current or infer manuscript integration from
  substantive approval.
- When I substantively approve a table, figure, map, measure, sample,
  specification, model, or other paper object and the workflow is about to
  move on, proactively ask whether to freeze it as the sole current version if
  I have not already made that decision. Do not freeze an object merely because
  it looks complete, passed validation, or received favorable feedback.
- After explicit freeze approval, keep one canonical current version and an
  auditable record of its generating code, inputs, outputs, validation,
  substantive measure/sample/display contract, and hashes when feasible. If an
  approved revision replaces it, update the stable current identity and remove
  the superseded copy from the current-state repository rather than
  accumulating competing `v2`, `final2`, or `latest` variants.
- After a freeze or approved replacement, update the authoritative current
  plan with the artifact's stable ID, current paper role, and placement.
- Preserve superseded provenance in task READMEs, manifests, or audit packages
  outside the current-state repository. Removing an item from the current
  repository does not authorize deletion of historical evidence.
- Freezing an artifact does not authorize inserting it into a manuscript,
  editing Word/LaTeX prose, changing captions or notes, or exporting a
  submission file. Treat manuscript integration as a separate approval and
  verify it against both the authoritative current plan and the current-
  artifact repository.

## Quality-First Research Work

- For research, empirical, data, manuscript, literature-review, and other high-stakes analytical tasks, default to quality-first rather than latency-first. Optimize for correctness, auditability, reproducibility, and academic defensibility even when this requires more time, tool calls, intermediate artifacts, or verification rounds.
- Never omit necessary context reading, explicit planning, data or sample audits, identification checks, robustness checks, artifact inspection, or recoverable records merely to shorten response time, reduce computational effort, or finish the task sooner.
- Requirements to be concise apply to communication, not to reasoning depth or execution completeness. Concise reporting does not authorize shallow analysis, abbreviated execution, weaker verification, or skipped steps.
- If the rigorous workflow will take substantial time, divide it into explicit stages and checkpoints, keep the task README current, preserve resumable state, and continue against substantive acceptance criteria. Do not silently replace the full workflow with a quick approximation.
- Any time, cost, speed, or convenience tradeoff that could materially reduce research quality or change the requested method, data, scope, variable definition, sample, identification strategy, or output must be explained in advance and decided by the user.
- A plan, command success, script completion, compilation success, or a plausible-looking result is not sufficient evidence of task completion. Completion requires verification of the substantive artifact and the relevant research-quality gates.

## Code And File Safety

- Do not overwrite or revert my existing edits unless I explicitly ask for that.
- Treat the workspace as potentially dirty at all times.
- Do not modify original source data, raw inputs, or user-provided original code. Treat them as immutable unless I explicitly ask otherwise.
- Write derived datasets, generated code, logs, reports, and temporary artifacts to separate task outputs rather than mixing them into original inputs.
- Once a task step has been updated or a newer result has been verified, prefer updating, overwriting, archiving, or deleting superseded generated artifacts, logs, and temporary files so the working state stays clean.
- Avoid destructive commands such as `git reset --hard`, mass deletes, force pushes, or irreversible schema changes unless I explicitly request them.
- Before editing, identify the smallest safe change that solves the problem.
- Preserve the existing project style unless I ask for a refactor.

## Verification

- After making changes, run the smallest relevant verification you can.
- If full verification is expensive or impossible, say what you checked and what remains unverified.
- For bug fixes, prioritize proving the bug path and the fix path.
- For data or research workflows, emphasize reproducibility, clear paths, and deterministic scripts where possible.
- After each concrete operation round, self-check whether the current deliverable actually meets the user's stated target or complaint.
- Treat command success, script completion, or compilation success as insufficient on their own; verify the resulting artifact itself.
- The relevant artifact may be a file, dataset, table, figure, document, PDF, log, rendered page, or other user-facing output.
- If the artifact still does not meet the target, continue iterating when feasible instead of reporting completion.

## Communication During Work

- Keep commentary minimal and high-signal. Do not send optional or filler commentary. Still ask necessary clarification questions, surface blockers, and give brief progress updates for long-running work.
- Give short progress updates while working so I know what you are checking or changing.
- Surface blockers early, but try one or two reasonable recovery steps yourself before stopping.
- If a command output is long, summarize the key lines instead of dumping everything.


## Long-Running Jobs And Polling

- 对任何批量远程查询、网页抓取、API extract、Internet Archive / Wayback / CDX 查询、下载队列或第三方服务调用，启动前必须先查官方文档中的 rate limit、robots/API policy、acceptable-use 条款或推荐调用节奏；若官方未给明确数字，按保守低速单线程执行，并在任务 README 中记录查询到的规则、访问日期、实际请求间隔、并发数和停止条件。
- 远程 API 或 archive 查询默认不得把“请求失败、429、DNS/SSL/timeout”直接解释为“数据不存在”。必须将 `ok_empty`、`rate_limited`、`network_error`、`blocked` 等状态分开记录；遇到 429 或大面积网络错误时，停止批量任务，冷却后再低速重试。
- 对需要长时间等待的远程任务、API extract、下载队列、模型任务或批处理任务，不要高频轮询；默认至少间隔 10-30 分钟，除非服务文档或用户明确要求更频繁。
- 对提醒、监控、继续当前任务、稍后检查状态、低频轮询等自动化请求，若可以绑定当前对话，优先创建 thread heartbeat，让结果回到同一条对话；只有当任务必须脱离当前线程独立运行、需要 workspace/worktree 环境、需要无人值守执行本地脚本，或用户明确要求独立任务时，才创建 cron/workspace automation。创建 cron/workspace automation 前应说明它可能在侧栏产生独立任务/对话。
- 对预计耗时较长且不需要持续占用本地 CPU 的任务，优先创建 thread heartbeat、自动化或记录可恢复的轮询命令，而不是在当前会话中空等或反复手动刷新。
- 轮询脚本必须幂等：先检查目标输出是否已存在且通过基本验收，再决定是否下载、处理或跳过；避免重复下载大文件。
- 大文件下载和长时间后处理应写入外置盘或项目指定临时目录，不写系统盘；一次只跑一个重任务。
- 如果凭据被用户授权临时暴露在命令或日志中，必须在任务 README 或项目记录中标记，并在项目结束时提醒用户撤销、删除或轮换凭据。
- 对混合普通官网与 Internet Archive / Wayback / CDX 的批量公开网页研究任务，默认采用分层限速：普通官方站点全局单线程、每请求至少15秒、timeout 60秒，并服从更高的robots `Crawl-delay`；Wayback/CDX和曾出现429的授权重试每请求至少120秒。已启动队列保持其原先记录的速率，后续新队列才可切换；所有包必须记录请求间隔、并发、robots策略和精确访问终态。
- 批量研究工作中，单校来源与组件审计必须独立完成；若项目允许，可把昂贵的累计union、全量manifest和共享回归测试延后至25或50个已审计组件的关闭批次。批次并入前必须确认没有活跃远程队列、组件键不重叠且均已通过独立manifest核验；不得借批处理降低人物、来源、日期、实体或访问错误的验证标准。


## Method Fidelity

- Do not silently substitute the user's requested method, data source, model, measurement procedure, or workflow with a different approach.
- If the requested approach is slow, costly, unavailable, partially infeasible, or would require a fallback, stop and explain the issue before changing methods.
- Clearly distinguish requested methods from actual methods in outputs and summaries. Mark partial, proxy, heuristic, cached, or fallback results as provisional.
- Do not present a proxy, fallback, approximation, or engineering shortcut as if it were the requested result.
- For research or data tasks, keep alternative-method outputs separate or explicitly labeled, and do not use them as main variables or final results without user approval.

## Dataset Universe And Subset Labeling

- For every artifact called a `universe`, `sample`, `frame`, `queue`, `panel`, `subset`, or similar, explicitly label whether it is the full universe, a priority sample, a remaining/unscored subset, an incremental supplement, a validation sample, or a union/composite of multiple files.
- Never call a component file the full universe unless verified by manifest/audit/key counts. Do not infer full coverage from filenames alone.
- If the full universe is a union or composite, record the component file paths, key columns, row counts, unique-key counts, overlaps, and final union count in the task README and/or audit file before using it downstream.
- When creating new artifacts, choose names and manifest fields that encode `full`, `priority`, `unscored`, `remaining`, `supplemental`, or `union` clearly enough that future work will not confuse them.
- In final summaries, distinguish “single source file” from “logical universe assembled from multiple files”; report the evidence used to verify the distinction.

## Research And Data Tasks

- When working on empirical, statistical, or data-processing tasks, prioritize correctness over elegance.
- Keep transformations auditable: note key inputs, outputs, assumptions, filters, merges, and generated files.
- Flag anything that may affect identification, sample construction, variable definitions, units, or time windows.
- Be careful with encoding, delimiters, missing values, duplicate keys, and silent type coercion.
- After data processing, appending, reshaping, merges, type conversion, or new-variable generation, always check whether variable labels were lost or left blank. If labels are missing, restore them before treating the output as complete.
- For newly generated variables, add variable labels by default. If a generated variable is categorical, the label should briefly state the meaning of each category, but remain concise enough to avoid Stata label-length problems.

## Stata Execution

- When running Stata in batch from Codex, default to the command-line console binary rather than the GUI launcher.
- Do not use GUI entry points such as `StataMP` or `xstata` for automated runs unless the user explicitly asks for a GUI session.
- Prefer a project-provided wrapper such as `scripts/run_stata_batch.sh` when one exists.
- If no wrapper exists, prefer `/Applications/Stata/StataMP.app/Contents/MacOS/stata-mp -q -b do ...`.
- Keep `.log` output alongside the do-file or inside the task execution directory so runs remain auditable.
- If console mode surfaces GUI-only startup commands from `profile.do`, treat them as a configuration warning unless they stop the actual batch script from finishing.

## LibreOffice Execution

- On this Mac, do not use direct `soffice --headless --convert-to ...` from Codex/terminal as the default DOCX/PDF rendering path. LibreOffice `26.2.3.2` on macOS `26.4.1` has repeatedly crashed there during AppKit / `NSApplication` registration with `Abort trap: 6`.
- For LibreOffice-based document conversion or rendering, prefer the macOS application launch path, such as `open -W -a LibreOffice --args ...`, so LaunchServices starts LibreOffice as a normal app.
- If direct `soffice` is attempted and fails with `SIGABRT`, `EXC_CRASH`, or `Abort trap: 6`, retry using the `open -W -a LibreOffice --args ...` route before treating the DOCX, PDF, profile, or source document as broken.
- Record any LibreOffice crash workaround and the exact conversion command in the task README so rendering remains reproducible.

## Paper PDF Rendering

- When rendering paper or manuscript content to PDF, use LaTeX as the default
  first choice. For Chinese content, prefer XeLaTeX with an appropriate
  `ctex`/`fontspec` setup.
- Keep data and result generation separate from document rendering:
  Python/R/Stata may generate table data, figures, and intermediate inputs, while
  LaTeX should normally control the paper-facing PDF layout.
- Do not substitute ReportLab, Matplotlib, Pillow, `pypdf`, HTML-to-PDF, or a
  manually merged multipage PDF workflow as the primary paper-PDF renderer merely
  because upstream inputs were generated in those tools.
- Use a different primary PDF-rendering toolchain only when the user explicitly
  requests it or LaTeX is genuinely unsuitable or unavailable. Explain the reason
  before changing methods.
- This rule does not replace Word when the requested final deliverable is an
  editable `.docx`; use Word-native manuscript and table structures for the final
  Word artifact, and use LaTeX preferentially when a paper-facing PDF must be
  rendered.


## Paper Writing And Empirical Presentation

- Before modifying any paper manuscript file, first provide a concrete modification plan in the conversation and wait for my explicit confirmation. The plan must identify the files or sections to be changed, the proposed wording or exact change scope, and what will be left untouched. This applies to paper正文、脚注、附录、表注、图注 and LaTeX manuscript prose even when the substantive direction seems clear.
- Do not expand a requested table, RD result, or local specification change into broader deletions or rewrites of data sections, IV evidence, appendix background evidence, theory framing, variable inventories, or mechanism claims unless I explicitly authorize that scope. If the boundary is unclear, stop and ask before changing those parts.
- When writing an economics paper, do not treat tables and figures as a formatting afterthought; table selection, sample comparability, and figure admission are part of the empirical design.
- For every main regression and every important robustness regression that may enter the main text, always perform and record a post-estimation sample audit:
  - explain why `N` changes across columns,
  - identify whether the loss comes from controls, fixed effects, singleton/separation drops, or sample construction,
  - state whether the remaining sample still matches the intended identification population.
- In main-text tables, prefer specifications that are theory-consistent, statistically credible, and clearly interpretable.
- Specifications that are not significant and do not add clear identification value should usually be moved to an appendix, audit table, or brief robustness discussion instead of staying in the main text.
- Main-text tables should follow Chinese top-journal norms:
- If正文或表注 needs to explain what has been controlled, absorbed, omitted, or moved elsewhere, name the concrete objects as clearly as possible rather than using vague placeholders such as `其他已控制项`, `相应控制变量`, or `相关设定`. If the explanation is only about presentation, prefer saying it once near the first relevant table instead of repeating it in every table note.
  - include a clear title, panel structure when relevant, and notes for fixed effects, controls, clustering, and sample;
  - explicitly state the dependent variable in the table header when needed;
  - present coefficients and parenthesized standard errors as separate rows;
  - place fixed effects, controls, observations, and `R^2`/pseudo `R^2` below the coefficient block rather than at the top of the table;
  - do not add standalone p-value rows to main-text tables unless there is a strong substantive reason;
  - vertical tables should usually have at least 4 substantive columns per panel, commonly 3–6;
  - wide horizontal tables should usually be used only when there are at least 7 columns and the comparison truly needs that layout.
- If Word output matters, do not rely on bare pandoc defaults; use a `reference.docx`/equivalent style chain so fonts, headings, table borders, captions, and paragraph spacing are consistent with a paper rather than a draft.
- Main-text figures must directly support the paper's narrative.
- Use Chinese titles, axis labels, legends, and figure notes for paper-facing charts whenever feasible.
- If a figure is visually ambiguous or may appear to contradict the paper's story, do not put it in the main text.
- For high-frequency pre-COVID figures used to support a reform narrative, prefer windows ending no later than `2019-12`; if the story requires the non-common-control group to grow faster after the reform than the common-control group, the figure must show that clearly, either in raw form or in a transparently residualized version. If neither supports the story, omit the figure from the main text.
- Before giving wording advice for an economics paper or revising any paper prose, read the relevant manuscript context rather than relying only on the user's pasted sentence. At minimum, check the surrounding paragraphs and, where relevant, the associated figure/table title, note, variable definition, model specification, and terminology already used in the paper. If the manuscript cannot be checked, state clearly that the judgment is based only on the provided excerpt and do not present it as a manuscript-level recommendation.
- When revising a draft paper, prioritize this order:
  1. sample audit and regression selection,
  2. figure admission and redesign,
  3. prose polishing,
  4. final export.

- Main-text prose must not become an author memo. Do not write internal workflow explanations such as why a specification was dropped, why a figure was replaced, why a layout changed, or how the draft was reorganized into正文段落. Keep those points in task READMEs, specification-audit files, appendix discussion, or table/figure notes only when strictly necessary for reader understanding.
- In economics writing, do not use abstract `XX边界` expressions by default, such as turning an empirical object into a vague “boundary” concept. Unless the author explicitly asks for it, the target journal or top-journal examples clearly use that term, or the object is already a recognized theoretical concept, rewrite it as a concrete economic object, choice, scope, structure, relationship, or mechanism. If `XX边界` must be retained, first state what the boundary means and how it is observed or identified.


## Output Preferences

- In final answers, summarize what changed, where it changed, and how it was checked.
- When useful, include exact file paths, commands, or next steps so the work is easy to continue.
- Do not pad the answer with generic advice.
