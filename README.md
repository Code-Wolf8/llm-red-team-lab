# llm-red-team-lab

Reproducible prompt injection baselines for open LLMs, measured with [garak](https://github.com/NVIDIA/garak). Each scan is a separate entry with its setup, results, limitations, and exact commands, so runs can be repeated and compared.

Prompt injection is LLM01 in the [OWASP Top 10 for LLM Applications](https://genai.owasp.org/llm-top-10/). The goal here is simple: measure how often models can be hijacked, document it honestly, and track how that changes across models, probes, and repeat runs.

## Scans

| # | Date | Model | Probes | Attempts | Hijack rate | Write-up |
|---|---|---|---|---|---|---|
| 01 | 2026-10-02 | Llama 3.1 8B (Ollama) | garak `promptinject` | 2,304 | 50.0% | [scans/2026-10-02-llama3.1-8b-promptinject](scans/2026-10-02-llama3.1-8b-promptinject/README.md) |

## Key takeaways so far

- Plain "ignore the above" attacks hijacked Llama 3.1 8B about half the time in scan 01.
- The violent-text attack was resisted more often (29.2%) than the hateful and long-string attacks (about 60%).
- These are single-run baselines. Treat them as starting points, not verdicts.

## How each scan is documented

Every scan folder follows the same layout so results are easy to compare:

- **Summary** and **setup** (model, scanner version, hardware, probes)
- **Results** with counts and confidence intervals
- **Limitations**, stated plainly
- **Reproduce**, with the exact commands

## Planned scans

- Repeat of scan 01 to measure run-to-run variation
- Other garak probe families against the same model
- Other open models for comparison

## Notes

- Scans run on disposable cloud instances, not personal machines.
- Probe output can contain offensive text. Raw logs are published only after review.

## References

- [garak](https://github.com/NVIDIA/garak), LLM vulnerability scanner
- [OWASP Top 10 for LLM Applications](https://genai.owasp.org/llm-top-10/)
