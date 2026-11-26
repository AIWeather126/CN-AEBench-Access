# CN-AEBench Dataset

For dataset validity research, extreme-event analysis, benchmark testing, and visualization, please visit:

https://aiweather126.github.io/CN-AEBench/pages

*CN-AEBench* is a comprehensive multi-source atmospheric and environmental dataset integrating ground meteorological observations, environmental monitoring, and ECMWF IFS forecast data.

📊 **Data Coverage:** 2023–Present

🌍 **Meteorological Stations:** 2,250+

🌍 **Environmental Monitoring Stations:** Approximately 2,600

⏱️ **Temporal Resolution:** 1 Hour

## 1. Variable Information

### 1.1 Static Descriptive Information Table

| No.  | Variable Name    | Unit    | Description                           |
| ---- | ---------------- | ------- | ------------------------------------- |
| 1    | elevation        | m       | Station elevation                     |
| 2    | lon              | degree  | Station longitude                     |
| 3    | lat              | degree  | Station latitude                      |
| 4    | station_province | --      | Province where the station is located |
| 5    | station_city     | --      | City where the station is located     |
| 6    | station_id       | --      | Station identifier                    |
| 7    | type             | --      | Land-use type at the station location |
| 8    | ndvi             | -1 to 1 | NDVI value at the station location    |

### 1.2 Multi-source Variable Description Table

| No.  | Variable Name | Unit                  | Description                                 |
| ---- | ------------- | --------------------- | ------------------------------------------- |
| 1    | ws_2min       | m/s                   | 2-minute average wind speed                 |
| 2    | ws_10min      | m/s                   | 10-minute average wind speed                |
| 3    | wd_2min       | degree                | 2-minute average wind direction             |
| 4    | wd_10min      | degree                | 10-minute average wind direction            |
| 5    | wd_instant    | degree                | Instantaneous wind direction                |
| 6    | ws_instant    | m/s                   | Instantaneous wind speed                    |
| 7    | vis           | m                     | Horizontal visibility                       |
| 8    | t             | °C                    | Air temperature                             |
| 9    | dt            | °C                    | Dew-point temperature                       |
| 10   | precipitation | mm                    | Hourly precipitation                        |
| 11   | rh            | %                     | Relative humidity                           |
| 12   | p             | hPa                   | Atmospheric pressure                        |
| 13   | slp           | hPa                   | Sea-level pressure                          |
| 14   | vapor         | hPa                   | Vapor pressure                              |
| 15   | phenomena     | --                    | Weather phenomena                           |
| 16   | ec_vis        | m                     | NWP horizontal visibility                   |
| 17   | ec_sh2        | kg/kg                 | NWP 2-m specific humidity                   |
| 18   | ec_t2m        | °C                    | NWP 2-m air temperature                     |
| 19   | ec_d2m        | °C                    | NWP 2-m dew-point temperature               |
| 20   | ec_sp         | hPa                   | NWP surface pressure                        |
| 21   | ec_msl        | hPa                   | NWP mean sea-level pressure                 |
| 22   | ec_u10        | m/s                   | NWP 10-m u-component of wind                |
| 23   | ec_v10        | m/s                   | NWP 10-m v-component of wind                |
| 24   | ec_rh         | %                     | NWP relative humidity (diagnostic variable) |
| 25   | ec_ws         | m/s                   | NWP wind speed (diagnostic variable)        |
| 26   | ec_wd         | degree                | NWP wind direction (diagnostic variable)    |
| 27   | ec_cbh        | m                     | NWP cloud-base height                       |
| 28   | ec_sf         | m of water equivalent | NWP hourly snowfall                         |
| 29   | ec_blh        | m                     | NWP boundary-layer height                   |
| 30   | ec_fal        | 0 to 1                | NWP albedo                                  |
| 31   | ec_lcc        | 0 to 1                | NWP low-cloud cover                         |
| 32   | ec_mcc        | 0 to 1                | NWP medium-cloud cover                      |
| 33   | ec_hcc        | 0 to 1                | NWP high-cloud cover                        |
| 34   | ec_tp         | m                     | NWP hourly precipitation                    |
| 35   | PM2.5         | μg/m³                 | Hourly mean PM2.5 concentration             |
| 36   | PM10          | μg/m³                 | Hourly mean PM10 concentration              |
| 37   | SO2           | μg/m³                 | Hourly mean SO2 concentration               |
| 38   | NO2           | μg/m³                 | Hourly mean NO2 concentration               |
| 39   | O3            | μg/m³                 | Hourly mean O3 concentration                |
| 40   | CO            | mg/m³                 | Hourly mean CO concentration                |
| 41   | AQI           | --                    | Air Quality Index                           |

>   **Note on** `**ec_tp**` **and** `**ec_sf**`**:**
>   The IFS forecast provides `tp` (total precipitation) and `sf` (snowfall) as cumulative values accumulated since forecast initialization. These two variables are de-accumulated into hourly values by taking the difference between consecutive forecast steps. All other NWP variables are instantaneous quantities.

## 2. AI-based Experiment Settings and Information

The experiments were conducted using CN-AEBench-L3.

### 2.1 Research Areas

We selected four representative regions across China for comprehensive evaluation.

#### 🏔️ Lanzhou Urban Agglomeration

-   Northwest China
-   Characterized by an arid climate, complex terrain, and frequent dust events influenced by the Gobi Desert.

#### 🌺 Kunming Urban Agglomeration

-   Southwest China
-   Located on the Yunnan–Guizhou Plateau, with a mild climate throughout the year and distinctive monsoon patterns.

#### ❄️ Harbin Urban Agglomeration

-   Northeast China
-   Features an extreme continental climate, harsh winters, and significant seasonal variations.

#### 🌊 Shanghai

-   East Coast
-   China's economic hub, characterized by a subtropical monsoon climate, urban heat-island effects, and typhoon influences.

Each region was trained and tested independently to evaluate regional model performance.

### 2.2 Data Split Strategy

Overall ratio:

**Training : Validation : Test = 7 : 1 : 2**

**Validation Set:**

Days 1–10 of October 2023, January/April/July/September/December 2024, and March/June 2025.

**Test Set:**

Days 14 to the end of the corresponding months.

**Training Set:**

All remaining data.

### 2.3 Experimental Setup

#### Short-term Prediction

-   Configuration: 24 steps → 1 / 4 / 12 / 24 steps
-   Evaluation lead times:
    -   1 h (nowcasting)
    -   4 h, 12 h, and 24 h (short-term prediction)
    -   Overall performance

#### Long-term Prediction

-   Configuration: 48 steps → 1 / 24 / 48 / 72 / 96 / 120 steps
-   Evaluation lead times:
    -   1 h (nowcasting)
    -   24 h, 48 h, 72 h, 96 h, and 120 h (extended-range prediction)
    -   Overall performance

The training configuration was as follows:

-   Maximum epochs: 500
-   Early-stopping patience: 30 epochs
-   Optimizer: Adam
-   Initial learning rate: 0.001
-   Learning-rate scheduler: MultiStepLR
-   Batch size: 512

For all reported results, the checkpoint with the lowest validation loss was selected and evaluated on the held-out test set to ensure an unbiased performance assessment.

All experiments were conducted on a single server equipped with:

-   4 × NVIDIA A100 GPUs
-   Intel Xeon Ice Lake processor (32 cores, 64 threads, 2.6 GHz)
-   188 GB RAM
-   Ubuntu Linux
-   CUDA 11.7
-   PyTorch 1.13

**Experiment results and visualization:**

https://aiweather126.github.io/CN-AEBench/pages

## 3. Data Availability

*CN-AEBench* L3 data is designed for developing end-to-end intelligent forecasting models and is currently at version **1.1.0**.



To ensure benchmark stability and comparability across research studies, dataset versions are updated when significant improvements are made to accommodate new weather and environmental changes, with clear version numbering.

### Dataset Access

Due to data access and licensing requirements, the dataset is not publicly downloadable.

Researchers interested in obtaining CN-AEBench for academic research are welcome to contact the authors.

Please send your data access request to:

**Email:** [2534114@tongji.edu.cn](mailto:2534114@tongji.edu.cn)

Please briefly describe your institutional affiliation, research purpose, and intended use of the dataset in your email.

Dataset access will be considered in accordance with applicable data licensing requirements and research conditions.

## 4. Data Sources

The multi-source data used in CN-AEBench are derived from meteorological observations, environmental monitoring, and numerical weather prediction products.

The environmental monitoring data include information obtained from provincial-level environmental monitoring platforms, such as:

-   https://sthj.sh.gov.cn/
-   https://sthjt.jiangsu.gov.cn/
-   https://aqi.zjemc.org.cn/
-   https://sthjt.ah.gov.cn/site/tpl/5371
-   https://nmg.merryai.com:33864/publish/#/realtime
-   http://hjzlxxfb.sthjt.jiangxi.gov.cn:9317/eipp/
-   https://sthjj.zhengzhou.gov.cn/air24.jhtml
-   https://sthjt.henan.gov.cn/
-   https://fjaqi.fjemc.org.cn/fb/

Additional data sources may be continuously monitored and integrated as part of ongoing research.

## 5. Research Domains

-   Weather Forecasting
-   Climate Analysis
-   Air Quality and Environmental Forecasting
-   Numerical Weather Prediction (NWP)
-   Data Assimilation
-   Intelligent Modelling

For questions regarding CN-AEBench, academic collaboration, or dataset access, please contact the authors at [**2534114@tongji.edu.cn**](mailto:2534114@tongji.edu.cn).
