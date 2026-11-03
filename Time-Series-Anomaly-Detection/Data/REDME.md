# Dataset Information

## Dataset Name
TSB-AD-U (Time Series Benchmark for Anomaly Detection)

## Selected Dataset
`010_NAB_id_10_WebService_tr_500_1st_271.csv`

## Dataset Details

- Total observations: 1,000
- Total columns: 2
- Column 1: `Data` — time-series numerical values
- Column 2: `Label` — anomaly labels

## Label Description

- `0` = Normal observation
- `1` = Anomalous observation

## Training and Testing Split

| Set | Observations |
|---|---:|
| Training | 500 |
| Testing | 500 |

The first 500 observations are used for training and the remaining 500 observations are used for testing.

## Source

Official dataset: https://www.thedatum.org/datasets/TSB-AD-U.zip

Original benchmark repository: https://github.com/TheDatumOrg/TSB-AD

## Note

This project uses one selected time series from the TSB-AD-U benchmark. The dataset is used for academic experimentation. Please consult the original benchmark and source-dataset licenses before redistribution.
