# KANR — Dev-selected policy bank

EVALUATION PACKAGE FOR JOINT REVIEW. No challenge submission has been sent. Synthetic GPU/protocol screens passed; full hidden-runtime qualification and two weight-redistribution scopes remain unresolved below. This documentation release does not assert otherwise.

Team: Keshav Balakrishna, Abhijay Gangarapu, Nishan Mani, Rithik Satarla. Affiliation: Independent. Contact: nishanmanisd@gmail.com.

## Method
We use a frozen task-to-policy mapping across ten checkpoint configurations (nine public and one team continuation). Policy choices use development instances 311–320; scored instances 301–310 are not used to select policies. Each task uses one selected policy. Model inference uses RGB/depth/proprioception through the corresponding native serving adapter, without privileged simulator state. The final package preserves native precision, normalization, checkpoint parameters and model planning horizons.

The global response chunk size is 4 actions. Native Comet plans use 32 actions and winner-family plans 20. Serving retains the rest of each native plan internally; K=4 does not imply replanning every four actions. See frozen-routes.json and task-image-map.tsv. The strict per-model server rejects unsupported tasks rather than silently changing policy. Fallback metadata in the historical route does not authorize an untested replacement policy in these per-model containers.

## Results and provenance
Measured self-evaluation Q: 0.15605353674103672 across 1,000 canonical records (100 tasks, instances 301–310); 37 successes and 71 tasks with nonzero Q. This is not a hidden-run score or placement claim. Duplicate records were resolved by attempt chronology, not by choosing the best score. Original metric bytes and original MP4s are preserved.

Self-evaluation used Isaac 6. The organizers' hidden run uses Isaac 5.1; the version difference is disclosed, not assumed equivalent. Seven replay=0 episodes differ from native execution horizons; the existing results README documents these. No metrics were rescaled or silently rerun to improve reported Q.

## Runtime evidence and limits
All ten models passed actual RTX3090 24 GB startup/warmup and synthetic observation protocol checks, B1/B10, reset, chunk boundaries and idle reconnect, as UID/GID65532. Longest measured B10 query was 3.38 s. Sampled memory is not a true peak or hard-cap proof. See gpu-screen-evidence.json for per-model measurements.

These checks do not establish real simulator episode performance, end-to-end 1 FPS, exact 60 GB RAM hard-cap compliance, or TitanRTX/Turing compatibility. A stronger Landlock harness initially blocked CUDA thread-name writes under /proc, causing CUDA initialization failure. A corrected guard restores GPU detection and all ten models passed the corrected startup and synthetic protocol retest with application-root write and outbound TCP restrictions. Retained failures remain available. No failed test is reclassified as a pass. A tokenizer cache permissions crash was repaired by copying identical tokenizer bytes into a writable temporary cache; native model code/weights were not changed.

## Delivery
Each app image selects one frozen model. Each container lifetime serves one task ID; start a fresh container when changing tasks, with up to ten batched rollouts on one connection. All images inherit the same large native base containing all ten models, approximately126 GB compressed; they are not small single-weight images. Pull once per host to share cached layers. Exact published test-image digests are in task-image-map.tsv and were anonymously pulled and verified. Their labels remain UNQUALIFIED because full hidden qualification has not been established. Do not use the older canary route.

Policy port:8000/TCP. Readiness:/readyz after native model load and warmup. Native wrapper/client must preserve reset and observation batch semantics. Use the included original evaluation wrapper and robot configuration from the result archive. A lost action response is ambiguous: reset is required rather than blindly retrying the action. Fail-stop watchdogs do not guarantee an episode will survive a model or device failure.

## Attribution and licence scope
Credits and original notices for public checkpoints and native serving code are embedded in each app's CREDITS.md and THIRD_PARTY tree. Relevant sources include sunshk/openpi_comet, ymetz checkpoint derivatives, 2025 winner checkpoint families, JackLiu and Amy specialists; see source locks for exact repository revisions. Public access and a source-code licence are not blanket weight redistribution permission. Comet-parent and Amy weight redistribution scope remains unresolved; LICENCE_SCOPE_REVIEW.md records the evidence. Do not call this release licence-cleared until resolved.

## Organizer artifact links and final review

- [Canonical results ZIP](https://github.com/nishn304/KANR-BEHAVIOR-2026/releases/download/v1-review/standard.public.KANR.Independent.20261016.zip): REVIEW6, SHA256 `690a13fee1b2ef4aba0f927b1f0307a48e2e303a51df6a26863dac6047f29cc4`, 519781 bytes.
- [All original videos, one ZIP per task](https://github.com/nishn304/KANR-BEHAVIOR-2026/releases/tag/v1-review): 100 task ZIPs containing 1000 original MP4s; see [video-downloads.tsv](video-downloads.tsv) for individual URLs and SHA256s.
- [Immutable model image map](task-image-map.tsv) and [container instructions](RUN_INSTRUCTIONS.md). Use the assigned image separately for each task, never one fixed-policy image for all tasks.
- [Research website](https://policy-bank.vercel.app), [paper](https://policy-bank.vercel.app/paper.pdf), [research code](https://github.com/FungousLand1941/policy-bank). Research CLI defaults to a scripted demonstration, not a native evaluation model.

This release makes the evaluation artifacts accessible for organizer inspection; it is not a challenge-form submission or an acceptance receipt. Historical REVIEW4/5 assets remain for provenance; use the standards-named current results ZIP and REVIEW6 kit. The paper/site's old isolation-failure account predates the corrected tests described above; retain the original failures and consult the current runtime evidence here. No weights are bundled in this documentation/research repository; the separately published evaluation images contain weights, with the unresolved scopes described above.



The original CPU integrity job stopped on one missing generated bytecode cache. The explicit exact-file repair and independent106423-file comparison are documented in INTEGRITY_REPAIR.md; original failure evidence is retained. Both native model families passed an additional runtime recheck using the anonymously downloaded published application layers and exact repaired cache on the verified native base.

## October17 review5 update

The confirmed four-member identity is in TEAM.json. The REVIEW5 results archive changes only its README member list; reported metrics are unchanged. A fresh launch of the exact published pt12 image passed native load and the official reference client with synthetic batch1/batch10, reset and64-action sequences. The slowest observed WAN call was28.6s; this is not complete production qualification. The Amy tasks96/97 stage-table mismatch is documented in amy-stage-table-audit.json; the alternative spec remains a candidate and production routing is unchanged. Licence research is complete but the two weight-redistribution scope questions remain unresolved. No form has been submitted.
