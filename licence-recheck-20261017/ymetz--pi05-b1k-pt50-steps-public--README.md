---
tags: [robotics, behavior-1k, openpi, pi0.5]
---
# pi0.5 BEHAVIOR-1K: Comet pt50 fine-tuned on the 2026 demos with task / skill / step prompts

Initialised from [sunshk/openpi_comet](https://huggingface.co/sunshk/openpi_comet) `pi05-b1kpt50-cs32`. Same input and
output space as pt50 (absolute actions, 32-step chunks, pt50 norm stats), served with openpi-comet's
`pi05_b1k-base` config. Licence terms follow the base checkpoint and openpi. Each `step-N/` folder holds `params/` and `assets/` of one training checkpoint.

- `steps-cont-2000/`: steps-cont step 2000
- `steps-cont-4000/`: steps-cont step 4000
- `steps-cont-6000/`: steps-cont step 6000
- `steps-cont-8000/`: steps-cont step 8000
- `steps-cont-9999/`: steps-cont step 9999
