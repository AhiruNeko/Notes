## 4 Tasks Evaluation

### Paper results: Seeds={42, 43, 44, 45, 46}, horizon=receding horiaon=5, goal offset steps=25, budget=50

| **Method** | tworooms | pusht | reacher | cube |
|---|---:|---:|---:|---:|
| CEM | 82.0 ± 2.0| 89.3 ± 6.4% | 68.0 ± 9.2% | 73.3 ± 9.0% |
| iCEM | 88.0 ± 2.0% | 84.7 ± 3.1% | 67.3 ± 11.4% | 76.0 ± 7.2% |
| MPPI | 71.3 ± 6.4% | 60.7 ± 4.2% | 42.7 ± 4.6% | 49.4 ± 9.5%|
| LeFlow | 100.0 ± 0.00% | 95.2 ± 3.0% | 86.8 ± 4.8% | 100.0 ± 0.0% |

### Seeds={42, 43, 44, 45, 46, 47, 48, 49, 50, 51}, horizon=receding horiaon=5, goal offset steps=25, budget=50

| Tasks | LeFlow SR | new LeFlow SR | SR increase | LeFlow time | new LeFlow time | time reduced |
|---|---:|---:|---:|---:|---:|---:|
| PushT | 95.40 ± 2.99% | **96.80 ± 2.70%** | **+1.40 pp** | 23.704 ± 0.669 | 23.915 ± 1.826 | -0.89% |
| TwoRooms | 99.60 ± 0.84% | **100.00 ± 0.00%** | **+0.40 pp** | 17.941 ± 2.417 | 16.421 ± 2.808 | 8.47% |
| Cube | 100.00 ± 0.00% | **100.00 ± 0.00%** | **+0.00 pp** | 87.167 ± 2.309 | 83.466 ± 3.787 | 4.25% |
| Reacher | 86.00 ± 4.42% | **87.40 ± 4.33%** | **+1.40 pp** | 42.552 ± 0.790 | 43.060 ± 1.382 | -1.19% |

### Seeds={42, 43, 44, 45, 46, 47, 48, 49, 50, 51}, horizon=receding horiaon=10, goal offset steps=50, budget=100

| Tasks | LeFlow SR | new LeFlow SR | SR increase | LeFlow time | new LeFlow time | time reduced |
|---|---:|---:|---:|---:|---:|---:|
| PushT | 82.60 ± 4.62% | **88.80 ± 4.13%** | **+6.20 pp** | 31.936 ± 0.821 | 30.724 ± 0.813 | 3.80% |
| TwoRooms | 98.60 ± 1.35% | **100.00 ± 0.00%** | **+1.40 pp** | 26.355 ± 2.275 | 22.061 ± 2.810 | 16.29% |
| Cube | 96.60 ± 2.84% | **98.20 ± 1.75%** | **+1.60 pp** | 79.170 ± 4.943 | 76.926 ± 5.731 | 2.83% |
| Reacher | 84.40 ± 5.64% | **87.80 ± 4.47%** | **+3.40 pp** | 55.319 ± 1.144 | 54.501 ± 1.418 | 1.48% |

## Ablations

![](./arch.svg)

### Ablation 1: No local conditions

**Model:**

- **Input:** $z_0, z_g, p_{1:H}$

### Ablation 2: No local conditions + no planner path

**Model:**

- **Input:** $z_0, z_g$

### Results

| Model | Full MSE ↓ | Final MSE ↓ | Success Rate | Full MSE Decrase | Final MSE Decrease | Success Rate Increase |
|---|---:|---:|---:|---:|---:|---:|
| Normal | **0.08840** | **0.21192** | **88.80 ± 4.13%** | +23.79% | +29.20% | +6.20 pp |
| No Local | 0.11933 | 0.27312 | 87.00 ± 6.06% | −2.87% | +8.76% | +4.40 pp |
| No Planner Path + No Local | 0.13344 | 0.27744 | 81.00 ± 3.56% | −15.03% | +7.31% | −1.60 pp |
| LeWM | 0.11600 | 0.29933 | 82.60 ± 4.62% | 0 | 0 | 0 |

![](./pusht_ablation_mse.svg)

![](pusht_ablation_success.svg)