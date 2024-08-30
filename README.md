# Code will be open-sourced soon

# TRD-Net

## Abstract
Urbanization intensifies building energy consumption and carbon emissions, challenging
sustainable development. This study introduces the Temporal Convolutional
Network-Residual Network-Deep Reinforcement Learning (TRD-Net) model, a hybrid
approach designed to enhance urban building energy management and carbon emission
reduction. TRD-Net captures temporal-spatial features, strengthens deep feature
representation, and optimizes decision-making. The model achieved 95.1% accuracy and
a 94.81% Area Under the Curve (AUC) on the Urban Building Energy Consumption
Dataset, outperforming existing methods. These results demonstrate TRD-Net’s
potential in advancing energy efficiency and sustainability in urban environments.

![](https://github.com/luolei5257/dd/blob/main/figure/over1131.jpg)

## Requirements

```bash
git clone https://github.com/luolei5257/dd  # clone
cd main
conda env create -f environment.yaml
conda activate TRD-Net
pip install -r requirements.txt  # install
```
## Testing

To sample from our model, you can use scripts/inference.py. For example,
```bash
python scripts/inference.py \
  --plms \
  --outdir results \
  --config configs/v1.yaml \
  --ckpt checkpoints/model.ckpt \
  --image_path examples/image/example_1.png \
  --mask_path examples/mask/example_1.png \
  --reference_path examples/reference/example_1.jpg \
  --seed 230 \
  --scale 5
```

or simply run:
```
sh test.sh
```

## Training
Here are the links to download the required datasets:

1. **Urban Building Energy Stock Datasets**:
   - This dataset contains over one million records detailing residential urban building stocks, including types such as terraced houses, detached houses, semi-detached houses, and bungalows. It covers a wide range of building features such as HVAC systems and building fabric properties.
   - [Download Urban Building Energy Stock Datasets](https://data.mendeley.com/datasets/m6vv9k9gcd/1)

2. **Directory of Buildings Energy Consumption Data sets (DBECD)**:
   - This directory provides detailed information on various building energy consumption datasets, categorized by the strategies used to collect them: measurement, survey, and simulation.
   - [Visit DBECD Homepage](https://tokhub.github.io/dbecd/)

Generate format：
```
python scripts/read_bbox.py
```

### Training TRD-Net
```
python -u main.py \
--logdir models/TRD-Net \
--pretrained_model pretrained_models/TRD-Netv1-4.ckpt \
--base configs/v1.yaml \
--scale_lr False
```

## Results

![](https://github.com/luolei5257/dd/blob/main/figure/table.jpg)
