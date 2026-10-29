# Future RL experiment manifest (unfilled protocol)

No historical values are inferred. For each future run retain:

- source repository and exact commit; Python/package/OS/device versions; env implementation/version/wrappers; complete resolved config;
- algorithm/model version, all random seeds, train/evaluation environment seeds and deterministic settings;
- equal environment-step/compute budget, stopping rule, evaluation frequency, episode count and max length;
- raw per-episode rewards and learning curves for every seed, including failed runs; checkpoints and replay/evaluation command;
- independent fixed evaluation seeds, mean/dispersion/confidence intervals and sample-efficiency comparison;
- video-to-run/checkpoint identifier, rollout selection policy and hashes of retained artifacts.

Approval for training compute/provider access and publication is separate. A future filled manifest must distinguish actual measured values from planned settings. Selected videos alone do not support algorithm superiority.
