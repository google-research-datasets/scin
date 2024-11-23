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

To learn more about the dataset and methods, please see our paper [Creating an Empirical Dermatology Dataset Through Crowdsourcing With Web Search Advertisements](https://jamanetwork.com/journals/jamanetworkopen/fullarticle/2826506), in collaboration with physicians at Stanford Medicine.

Citation:

```
@article{10.1001/jamanetworkopen.2024.46615,
    author = {Ward, Abbi and Li, Jimmy and Wang, Julie and Lakshminarasimhan, Sriram and Carrick, Ashley and Campana, Bilson and Hartford, Jay and Sreenivasaiah, Pradeep K. and Tiyasirisokchai, Tiya and Virmani, Sunny and Wong, Renee and Matias, Yossi and Corrado, Greg S. and Webster, Dale R. and Smith, Margaret Ann and Siegel, Dawn and Lin, Steven and Ko, Justin and Karthikesalingam, Alan and Semturs, Christopher and Rao, Pooja},
    title = {Creating an Empirical Dermatology Dataset Through Crowdsourcing With Web Search Advertisements},
    journal = {JAMA Network Open},
    volume = {7},
    number = {11},
    pages = {e2446615-e2446615},
    year = {2024},
    month = {11},
    abstract = {Health datasets from clinical sources do not reflect the breadth and diversity of disease, impacting research, medical education, and artificial intelligence tool development. Assessments of novel crowdsourcing methods to create health datasets are needed.To evaluate if web search advertisements (ads) are effective at creating a diverse and representative dermatology image dataset.This prospective observational survey study, conducted from March to November 2023, used Google Search ads to invite internet users in the US to contribute images of dermatology conditions with demographic and symptom information to the Skin Condition Image Network (SCIN) open access dataset. Ads were displayed against dermatology-related search queries on mobile devices, inviting contributions from adults after a digital informed consent process. Contributions were filtered for image safety and measures were taken to protect privacy. Data analysis occurred January to February 2024.Dermatologist condition labels as well as estimated Fitzpatrick Skin Type (eFST) and estimated Monk Skin Tone (eMST) labels.The primary metrics of interest were the number, quality, demographic diversity, and distribution of clinical conditions in the crowdsourced contributions. Spearman rank order correlation was used for all correlation analyses, and the χ2 test was used to analyze differences between SCIN contributor demographics and the US census.In total, 5749 submissions were received, with a median of 22 (14-30) per day. Of these, 5631 (97.9\%) were genuine images of dermatological conditions. Among contributors with self-reported demographic information, female contributors (1732 of 2596 contributors [66.7\%]) and younger contributors (1329 of 2556 contributors [52.0\%] aged \&lt;40 years) had a higher representation in the dataset compared with the US population. Of 2614 contributors who reported race and ethnicity, 852 (32.6\%) reported a racial or ethnic identity other than White. Dermatologist confidence in assigning a differential diagnosis increased with the number of self-reported demographic and skin-condition–related variables (Spearman R = 0.1537; P \&lt; .001). Of 4019 contributions reporting duration since onset, 2170 (54.0\%) reported onset within less than 7 days of submission. Of the 2835 contributions that could be assigned a dermatological differential diagnosis, 2523 (89.0\%) were allergic, infectious, or inflammatory conditions. eFST and eMST distributions reflected the geographical origin of the dataset.The findings of this survey study suggest that search ads are effective at crowdsourcing dermatology images and could therefore be a useful method to create health datasets. The SCIN dataset bridges important gaps in the availability of images of common, short-duration skin conditions.},
    issn = {2574-3805},
    doi = {10.1001/jamanetworkopen.2024.46615},
    url = {https://doi.org/10.1001/jamanetworkopen.2024.46615},
    eprint = {https://jamanetwork.com/journals/jamanetworkopen/articlepdf/2826506/ward\_2024\_oi\_241322\_1731448364.35384.pdf},
}
```

## Contact

To contact the team, please use this [contact form](https://docs.google.com/forms/d/e/1FAIpQLSdTSw-Vz1TcTv42_REzDIa28p9-xSbpvc3AttASqC0pzZdvOA/viewform).

