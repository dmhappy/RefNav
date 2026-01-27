# RefNav
RefNav: Reflective-Correcting Zero-Shot Navigation via Counterfactual Backtracking in Continuous Environments
This is the official repository of [RefNav: Reflective-Correcting Zero-Shot Navigation via Counterfactual Backtracking in Continuous Environments]

<div align=center>
<img src="./img/teaser.png" width=80%>
</div>

## Setup

### Dataset Preparation

Please follow [HM3DSem](https://aihabitat.org/datasets/hm3d-semantics/) to download the dataset and prepare the data. The data format should be:

```
data/
├── objectgoal_hm3d/
│   ├── train/
│   ├── val/
│   └── val_mini/
├── scene_datasets/
│   └── hm3d/
│       ├── minival/
│       └── val/
├── versioned_data/
├── matterport_category_mappings.tsv
└── object_norm_inv_perplexity.npy
```

### Checkpoints

Please checkout [Grounded-SAM](https://github.com/IDEA-Research/Grounded-Segment-Anything) to download `groundingdino_swint_ogc.pth` and `sam_vit_h_4b8939.pth` and put them into `Grounded_SAM/`.

### Dependencies

1. Python & PyTorch

    This code is tested on Python 3.9.16 on Ubuntu 20.04, with PyTorch 1.11.0+cu113.

2. Habitat-Sim & Habitat-Lab

    ```
    # Habitat-Sim
    git clone https://github.com/facebookresearch/habitat-sim.git
    cd habitat-sim; git checkout tags/challenge-2022; 
    pip install -r requirements.txt; 
    python setup.py install --headless

    # Habitat-Lab
    git clone https://github.com/facebookresearch/habitat-lab.git
    cd habitat-lab; git checkout tags/challenge-2022; 
    pip install -e .
    ```

3. Grounded-SAM

    Please checkout [Grounded-SAM](https://github.com/IDEA-Research/Grounded-Segment-Anything) to install the dependencies.

4. Others

    ```
    pip install -r requirements.txt
    ```

## Running

### Example

An example command to run the pipeline:

```
CUDA_VISIBLE_DEVICES=0 python main.py --split val --eval 1 --auto_gpu_config 0 --prompt_type scoring \
-n 1 --num_eval_episodes 100 --text_threshold 0.55 --boundary_coeff 12 --start_episode 0 --tag_freq 100 \
--use_gtsem 0 --num_local_steps 20 --print_images 1 --exp_name test
```
