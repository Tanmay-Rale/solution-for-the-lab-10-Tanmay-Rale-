# ELEC5308 Lab 10 — Deep Reinforcement Learning on highway-env

## Files

- `lab10_drl_highway_SOLVED.ipynb` — corrected submission notebook.
- `requirements.txt` — Python dependencies.

## Run order

1. Open `lab10_drl_highway_SOLVED.ipynb`.
2. Run the notebook from top to bottom.
3. The diagnostics cell must print `ALL CHECKS PASSED`.
4. The mandatory training run uses exactly 20,000 timesteps (the lab maximum).
5. Training creates:
   - `artifacts/dqn_highway.zip`
   - `artifacts/monitor.csv`
6. Evaluation creates:
   - `artifacts/training_curve.png`
   - `artifacts/rollout.gif`
   - `artifacts/rollout.mp4` (or fallback `.avi` if MP4 encoding is unavailable)
   - `artifacts/results.json`

## Important

Do not fabricate evaluation results. Run the notebook in the target Python environment so
the model and metrics are genuinely produced.

Keep the two diagnostics markers unchanged:

`AUTOGRADER_EXTRACT_START: diagnostics`

`AUTOGRADER_EXTRACT_END: diagnostics`

## Git

After the notebook finishes successfully:

```bash
git add lab10_drl_highway_SOLVED.ipynb requirements.txt artifacts/
git commit -m "Complete Lab 10 DQN highway training and evaluation"
git push
```

If the course requires the original notebook filename, rename the solved notebook to the
course-supplied filename before committing.
