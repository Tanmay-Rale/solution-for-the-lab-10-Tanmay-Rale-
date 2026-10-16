# Lab 10 — Deep Reinforcement Learning on `highway-env`

**ELEC5308: Intelligent Information Engineering Practice** 


> **This notebook is fully self-contained.** Every helper function (environment setup, training
> wrappers, evaluation, GIF/MP4 recording, plotting, results I/O) is defined directly in the cells
> below — there is no separate Python package to install or path to configure. The **only** install
> you need is the one `%pip install` cell at the top, for the external RL libraries themselves
> (`gymnasium`, `highway-env`, `stable-baselines3`, `torch`).


> ⚠️ **Mandatory task time budget: 30 minutes.** The "Mandatory Task" section (Steps 2–5 below) is
> designed to fit that budget on a CPU laptop. "Optional Extensions" at the end is **ungraded**
> take-home material — do not start it until the mandatory task's artefacts are saved.

> ✍️ **AI Journal reminder:** log any significant Copilot/ChatGPT/Claude interaction you use while
> completing this notebook, per the course AI Usage Policy.


### Mandatory task submission checklist

- [ ] `run_diagnostics_self_check()` prints `ALL CHECKS PASSED`
- [ ] `artifacts/dqn_highway.zip` saved
- [ ] `artifacts/training_curve.png` saved (reward **and** secondary signal visible)
- [ ] `artifacts/rollout.gif` (and/or `.mp4`) saved
- [ ] `artifacts/results.json` saved
- [ ] Notebook committed (with the `AUTOGRADER_EXTRACT_START/END` markers around the `diagnostics`
      cell left intact — do not delete or rename them), PR opened + reviewed + merged, submitted via
      Gradescope (see lab sheet §5, Phase 5–6)

---
## OPTIONAL EXTENSIONS (ungraded — take home)

Not autograded, not required for the mandatory 40 marks. Pick any that interest you — several map
directly onto techniques you may want for your **Assignment 2** RL track.

1. **PPO on continuous control** — Use `train_ppo(...)` (defined above) on `racetrack-v0` (continuous
   steering/throttle). Compare PPO's clipped-objective stability (slide 42) against your DQN's
   training curve.
2. **Potential-based reward shaping on `parking-v0`** — Implement the `shaping` cell above
   (`run_shaping_self_check()`), wrap `parking-v0`'s sparse reward with `shape_reward(...)`, and show
   it trains faster than the unshaped baseline.
3. **Reward hacking, deliberately** — Edit a copy of `MANDATORY_ENV_CONFIG` so one reward term
   dominates (e.g. set `collision_reward=0`). Train briefly, and show how your secondary diagnostic
   signal (not reward!) reveals the degenerate behaviour (slides 53–55).
4. **Double DQN ablation** — Compare `target_update_interval` settings, or wrap SB3's Double-DQN-style
   target handling explicitly; plot overestimation of Q-values vs. true return (slide 28).
5. **State-of-the-art extensions (for your Assignment 2 proposal):**
   - *Dueling / Prioritized Experience Replay* via `sb3-contrib`'s `QRDQN`, comparing sample efficiency.
   - *Recurrent policies* (`sb3-contrib`'s `RecurrentPPO`) on a partially-observable scenario
     (reduced `vehicles_count` + occlusion) to handle non-Markovian observations.
   - *Multi-agent-flavoured scenarios* — `intersection-v0` or `roundabout-v0` with reward shaping
     for safe merging.
   - *Self-play / curriculum* — progressively increase `vehicles_count` across training stages,
     echoing the self-play scaling result referenced on lecture slide 44.
