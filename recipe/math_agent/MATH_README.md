## Setup and Execution Process

### 1. Environment Setup
```bash
bash prepare_all_science.sh
```

### 2. Start Sandbox
```bash
cd sandbox
uvicorn sandbox_api:app --host 127.0.0.1 --port 12345 --workers 4
```

### 3. Run Training Script
1. Change `PATH_PREFIX` to the ARLArena project path in the bash file 
2. Execute training:
```bash
bash examples/math_trainer/4B/train_grpo.sh
```

### 4. Run Evaluation Script
1. Change `PATH_PREFIX` to the ARLArena project path in the bash file 
2. Use the same RUN_NAME(line63) as training
3. Execute evaluation:
```bash
bash examples/math_trainer/4B/infer.sh
```

## Important Hyperparameter

- `MAX_TURNS`: Max number of tool-use turns permitted in a single trajectory.
- `TRAIN_BATCH_SIZE`: Total batch size used for rollouts.
- `ROLLOUT_N`: Rollout count generated per prompt during sampling.
- `MAX_PROMPT_LENGTH`: Max total response token length per trajectory (sum across all turns).
- `MAX_RESPONSE_LENGTH`: Max response token length per turn.
- `PPO_MINI_BATCH_SIZE`: Batch size for policy optimization updates.
- `REMOVE_CLIP`: If true, drop over-long generated trajectories.
- `REMOVE_EXTRA_VOID_TURN`: If true, treat trajectories with invalid actions as void turns and mask them in loss calculation; see (https://arxiv.org/pdf/2509.02479).
- `REJECTION_SAMPLE`: If true, enable rejection sampling for rollouts.
- `OVERSAMPLE`: Oversampling ratio per training epoch (with rejection sampling).

