# Intersectional Fairness (ISF)

## Description
Intersectional Fairness (ISF) is a bias detection and mitigation technology for intersectional bias, which combinations of multiple protected attributes causes.  
ISF leverages the existing single-attribute bias mitigation methods to make a machine-learning model fair regarding intersectional bias.  
Approaches applicable to ISF are pre-, in-, and post-processing. For now, ISF supports Adversarial Debiasing, Equalized Odds, Massaging, and Reject Option Classification.

### Supported Python Configurations:

| Item      | Version |
| ------- | -------------- |
| Python  | 3.7 |


## Setup
The ISF setup will install resources and patch AIF360.

### Install with `pip`
```bash
pip install git+https://github.com/intersectional-fairness/isf.git
```

### Patch AIF360 for Intersectional Fairness  
Apply a patch to AIF360 to work with ISF.

The patch contents are as follows.

| file    | method/class | fixes |
| ------- | -------------- | -------------- |
| datasets/structured_dataset.py | validate_dataset | * Changed the generating condition of 'Value Error' condition to support multiple protection attributes |
| algorithms/postprocessing/reject_option_classification.py | RejectOptionClassification | * Added "F1 difference" to corresponding metric<br/>* Defined "Balanced Accuracy" as default value for accuracy_metric_name |

patch application command

```bash
patch {aif360 installed directory path}/datasets/structured_dataset.py patch/structured_dataset.patch
patch {aif360 installed directory path}/algorithms/postprocessing/reject_option_classification.py patch/reject_option_classification.patch
```

## Run the Examples
The `examples` directory contains a diverse collection of jupyter notebooks that use Intersectional Fairness in various ways.  

If you use open data supported by AIF360, you need to download the datasets and place them in their respective directories as described in [aif360/data/README.md](aif360/data/README.md).

## Citing Intersectional Fairness
A technical description of Intersectional Fairness is available in this [paper](https://arxiv.org/abs/2010.13494).  
Below is the bibtex entry for this paper.  

```
@misc{kobayashi2020onevsone,
      title={One-vs.-One Mitigation of Intersectional Bias: A General Method to Extend Fairness-Aware Binary Classification},
      author={Kenji Kobayashi and Yuri Nakao},
      year={2020},
      eprint={2010.13494},
      archivePrefix={arXiv},
      primaryClass={cs.LG}
      url = {https://arxiv.org/abs/2010.13494}
}
```

## Support
If you have any questions or problems, please contact [us](MAINTAINERS.md).

## License
Intersectional Fairness and the OSS licenses it uses is [here](LICENSE).
