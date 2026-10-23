## Submit a recorded AtMem run for maintainer review

We would like to submit **AtMem 2.3.10b1 + Hermes + GPT-5.6 Luna** as a
**self-tested / unverified** DolphinBench result. This PR adds a run descriptor
and public evidence links only; it does not modify official results, benchmark
tasks, grading, website code, or the leaderboard.

| Persona | Passed | Total | Accuracy |
| --- | ---: | ---: | ---: |
| Morgan | 135 | 200 | 67.5% |
| Alex | 123 | 200 | 61.5% |
| Riley | 132 | 200 | 66.0% |
| **Total** | **390** | **600** | **65.0%** |

- Public dataset, task viewer and methodology: https://huggingface.co/datasets/atmem/atmem-2.3.10b1-dolphinbench
- Immutable evidence revision: `5ef528c499aa26b765fff9d8ed8f2c2e6ee52912`
- [Submission ZIP](https://huggingface.co/datasets/atmem/atmem-2.3.10b1-dolphinbench/resolve/5ef528c499aa26b765fff9d8ed8f2c2e6ee52912/submission.zip)
- [Validation summary](https://huggingface.co/datasets/atmem/atmem-2.3.10b1-dolphinbench/blob/5ef528c499aa26b765fff9d8ed8f2c2e6ee52912/validation.json)
- ZIP SHA-256: `78788ad3455d04407c037706d3ff129d56eafff89beaac101f2a461cb58d7538`

### Execution

The ZIP contains exactly `ingestion.json` and `tests.json`, with 13,539
chronological ingestion records, all 600 task interactions including failures,
API-reported usage, tool traces and recorded judge responses. The unchanged
upstream validator reproduces 390 passes without model calls. Pinned benchmark
revision: `81cb6f8405b40a9e76089cef650806a80af06ea2`.

Reader: `openai/gpt-5.6-luna`, high reasoning, 60 turns, 1,050,000-token
configured context, through the Hermes subscription/OAuth bridge. Judge:
`gpt-5.6-sol`, medium reasoning, 8,000-token cap, through OpenRouter with
Azure-only routing (not a direct Azure endpoint). Memory remains frozen and
separate per persona, with a fresh conversation and app state for each task.
Median recorded task latency is 85.78 seconds.

### Provenance and acceptance questions

- The run reused original chronological source-ingestion state from an earlier
  AtMem artifact, retaining its original receipts/timings and verifying the same
  frozen checkpoints with installed 2.3.10b1. The 600 test interactions were
  newly executed for this condition. Earlier public-task subsets informed
  development; this is not an unseen holdout or independent reproduction.
- For Morgan/129, a failed restart truncated the separate backend log. Its
  complete native wire conversation was recovered without reader replay, using
  the official transcript-based grading path. The dataset marks this exception;
  we do not claim independent backend attestation for that task.
- Recorded judge messages were projected with upstream `clean_message` for the
  public schema. Original grades, verdicts, answer text, usage and timings were
  not edited. Byte-identical native/state relocation and APFS ZIP staging are
  documented in the dataset's recovery metadata.
- Ingestion and reader incremental API cash are recorded as zero because
  ingestion is local and the reader uses subscription capacity. Subscription,
  hardware and energy costs are **not** represented as free. Paid judging is
  separate: $3.346938 completed charges plus $0.276770 uncertain timeout bound.

Please review whether this configuration and provenance are eligible for a
self-submitted listing, and whether you require any additional evidence or
transport/ingestion changes. We are not requesting an independently verified
label or claiming a matched advantage over another memory system.

The website's ZIP-upload channel remains separate; this PR is the explicit
maintainer-review submission and does not assert that a website upload or
listing has already been accepted.


## Stable release promotion

The tested build **2.3.10b1** was promoted to [stable AtMem 2.3.10](https://github.com/aetna000/atmem/releases/tag/v2.3.10). The qualification checked all 370 shipped product files: only two explicit version constants changed; retrieval, storage, governance, prompts, defaults, dependencies and companion/bridge implementation remain unchanged. [Qualification](https://github.com/aetna000/atmem/blob/4729197781904bb292ffd0a9c1ec498bab92b5d0/docs/releases/v2.3.10-qualification.md); [publication checks](https://github.com/aetna000/atmem/actions/runs/39901666310).

This remains the original **2.3.10b1, 390/600** recorded run, not a new stable-version benchmark. Original task records, ZIP and evidence revision are unchanged.
