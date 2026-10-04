# EvoMem-VLA

## State-Evolution Memory for Long-Horizon Robot Manipulation

[Project Page & Videos](https://yuhengna.github.io/EvoMem-VLA/)

**Yuheng Na, Zhide Zhong†, Junjie He, Junfeng Li, Haodong Yan, Jiaan Wang, Jiaguan Zhu, Yangyang Zheng, Tianyu Huang, Haoang Li***

† Project lead · * Corresponding author

### Release status

This is the official code repository for EvoMem-VLA. **Code and checkpoints are coming soon.** The final implementation, installation instructions, and training and evaluation entry points will be added here. The paper link will be added after the arXiv release.

### Overview

EvoMem-VLA constructs **state-evolution memory** by explicitly encoding and retaining observed changes between historical states. It pairs visual state evidence with conditional delta tokens so that the policy can use remembered interaction changes for action generation.

- **Conditional delta tokenization:** ordered frame pairs are encoded into directional, source-conditioned delta tokens.
- **Multi-scale memory:** three recent delta-token groups are organized with initial and recent observations, with keyframe-change memory enabled for RoboMME and real-world tasks. RMBench uses initial and recent observations with the three recent delta-token groups, without keyframe memory.
- **Task-adaptive routing:** a shared VLM backbone predicts actions directly for tasks without multi-stage planning, or first generates an executable subtask to condition action generation for multi-stage tasks.

The policy is implemented in the QwenOFT framework from [StarVLA](https://github.com/starVLA/starVLA).

![EvoMem-VLA architecture](https://yuhengna.github.io/EvoMem-VLA/assets/images/architecture.png)

### Results

| Evaluation setting | Success rate |
| --- | ---: |
| RMBench | 80.7% |
| RoboMME | 82.0% |
| Real-world tasks | 83.8% |

We jointly train one policy per simulation benchmark. Real-world evaluation covers four tasks on a Franka single-arm robot and an AgileX COBOT dual-arm platform, with one policy trained per embodiment. See the [project page](https://yuhengna.github.io/EvoMem-VLA/) for task demonstrations and detailed results.

### Citation

```bibtex
@misc{na2026evomemvla,
  title = {EvoMem-VLA: State-Evolution Memory for Long-Horizon Robot Manipulation},
  author = {Yuheng Na and Zhide Zhong and Junjie He and Junfeng Li and Haodong Yan and Jiaan Wang and Jiaguan Zhu and Yangyang Zheng and Tianyu Huang and Haoang Li},
  year = {2026},
  url = {https://yuhengna.github.io/EvoMem-VLA/}
}
```
