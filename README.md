<p align="center">
  <img src="docs/assets/logo.png" alt="SNAP logo" width="120">
</p>

# _SNAP_: What Makes Synthetic Hard Negatives Work in Vision-Language Pretraining?

Official repository for **SNAP**, a model-agnostic method that generates synthetic hard negatives directly in the representation space for vision-language pretraining. Synthetic hard negatives work well for unimodal self-supervised learning, but naively transferring them to CLIP-style training fails: cross-modal blends fall into the modality gap, and intra-modal blends that touch the matched positive leak its signal into the loss. SNAP avoids both failure modes by generating intra-modal negatives that never involve the positive from either modality, adding **less than 10% training overhead** on top of CLIP and FLIP.

> **What Makes Synthetic Hard Negatives Work in Vision-Language Pretraining?**  
> Nikos Giakoumoglou, Paschalis Giakoumoglou, Andreas Floros, Kleanthis Marios Papadopoulos, Tania Stathaki — **ACCV 2026**  
> [Paper](https://arxiv.org/abs/2610.09700) | [Website](https://giakoumoglou.github.io/snap/) | [Code](https://github.com/giakoumoglou/snap)

---

## Overview

We analyze six representation-space synthesis strategies and identify two failure modes in their transfer to vision-language pretraining: cross-modal constructions that produce overly easy negatives or pull them toward the query, and intra-modal constructions that incorporate the matched positive. We also observe logit-scale saturation when training with synthetic hard negatives and a learnable temperature, and find that fixing the temperature improves downstream performance. Using this geometric analysis we propose SNAP, which generates intra-modal hard negatives that never involve the positive from either modality, avoiding both failure modes entirely. SNAP requires no external generative models and is evaluated on top of CLIP and FLIP across multiple architectures (ViT-B/16, ViT-B/32, RN-50) and datasets (CC3M, CC12M), delivering consistent improvements on zero-shot retrieval, zero-shot classification, and linear probe evaluation.

## Code

The training and evaluation code is being cleaned up for release and will be added to this repository. In the meantime, see the [paper](https://arxiv.org/abs/2610.09700) and [project page](https://giakoumoglou.github.io/snap/) for the full method and results.

---

### License

This project is under the MIT license. See [LICENSE](LICENSE) for details.

## Citation

If you find this repository useful, please consider giving it a star ⭐ and citing our paper:

```bibtex
@misc{giakoumoglou2026snap,
      title={{What Makes Synthetic Hard Negatives Work in Vision-Language Pretraining?}},
      author={Nikos Giakoumoglou and Paschalis Giakoumoglou and Andreas Floros and Kleanthis Marios Papadopoulos and Tania Stathaki},
      year={2026},
      eprint={2610.09700},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2610.09700},
}
```
