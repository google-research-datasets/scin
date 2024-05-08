# SCIN Dataset

The SCIN (Skin Condition Image Network) open access dataset aims to supplement publicly available dermatology datasets from health system sources with representative images from internet users. To this end, the SCIN dataset was collected from Google Search users in the United States through a voluntary, consented image donation application. The SCIN dataset is intended for health education and research, and to increase the diversity of dermatology images available for public use.

The SCIN dataset contains 5,000+ volunteer contributions (10,000+ images) of common dermatology conditions. Contributions include Images, self-reported demographic, history, and symptom information, and self-reported Fitzpatrick skin type (sFST). In addition, dermatologist labels of the skin condition and estimated Fitzpatrick skin type (eFST) and layperson estimated Monk Skin tone (eMST) labels are provided for each contribution.

The data is stored in the [dx-scin-public-data bucket on Google Cloud Storage](https://console.cloud.google.com/storage/browser/dx-scin-public-data). Check out the [`scin_demo.ipynb`](scin_demo.ipynb) notebook for a quick review of how to access the dataset and the [Dataset Documentation](dataset_schema.md) for an overview of its schema.

Please note: This dataset contains images of medical conditions, some of which may be sensitive and/or graphic in nature.

Known issues:

* There are 15 images that are duplicates (and appear 42 times total) in the data. Because this data was used for the paper, it's been included in the release.
* There are 48 cases where the case is marked as gradable but no skin condition
  label is present. This happens for cases where they were marked as ungradable
  due to multiple conditions present.
* [Issue #1](https://github.com/google-research-datasets/scin/issues/1): 1 image file is missing

## License

The SCIN Dataset is released under [SCIN Data Use License](LICENSE)

## DOI

[![DOI](https://zenodo.org/badge/760881983.svg)](https://zenodo.org/doi/10.5281/zenodo.10819503)

## Research Paper

To learn more about the dataset and methods, please see our paper [Crowdsourcing Dermatology Images with Google Search Ads: Creating a Real-World Skin Condition Dataset](https://arxiv.org/abs/2402.18545), in collaboration with physicians at Stanford Medicine.

```
@misc{ward2024crowdsourcing,
      title={Crowdsourcing Dermatology Images with Google Search Ads: Creating a Real-World Skin Condition Dataset},
      author={Abbi Ward and Jimmy Li and Julie Wang and Sriram Lakshminarasimhan and Ashley Carrick and Bilson Campana and Jay Hartford and Pradeep Kumar S and Tiya Tiyasirichokchai and Sunny Virmani and Renee Wong and Yossi Matias and Greg S. Corrado and Dale R. Webster and Dawn Siegel and Steven Lin and Justin Ko and Alan Karthikesalingam and Christopher Semturs and Pooja Rao},
      year={2024},
      eprint={2402.18545},
      archivePrefix={arXiv},
      primaryClass={cs.CY}
}
```

## Contact

To contact the team, please use this [contact form](https://docs.google.com/forms/d/e/1FAIpQLSdTSw-Vz1TcTv42_REzDIa28p9-xSbpvc3AttASqC0pzZdvOA/viewform).

