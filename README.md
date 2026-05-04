# TimesNet-2D-CNN

<img width="842" height="319" alt="image" src="https://github.com/user-attachments/assets/7d29c30e-d1a1-49b4-aa2a-e556b50e13fb" />

<img width="843" height="298" alt="image" src="https://github.com/user-attachments/assets/f5d9d2cf-81d5-4e88-bccf-47d996802cec" />

## Intraperiod-Variation and Interperiod-Variation
週期內變化(Intraperiod) 和周期間變化(Interperiod)

由傅立葉轉換依照頻率由大到小切割樣本，再把無數小樣本拼起來形成2D的時間序列結構

因為股價在傅立葉轉換裡一定呈現降幕的現象，所以分割出的時間週期會偏長


# 模型參數設置
<img width="728" height="248" alt="image" src="https://github.com/user-attachments/assets/4c71dbc8-4a4f-4652-93ed-66a968a65d54" />

# d model
C就是餵入的N個變量
<img width="354" height="50" alt="image" src="https://github.com/user-attachments/assets/cd97ede5-b5ee-494c-9e9f-7de6e8424331" />



# Normalization of Data
Reversible Instance Normalization

1. **Normalize:**

$$X_{in} = \frac{X - \mu_{instance}}{\sigma_{instance}}$$

2. **Processing (模型運算):**

$$\hat{Y}_{out} = \text{TimesNet}(X_{in})$$

3. **Denormalize:**

$$\hat{Y}_{final} = \hat{Y}_{out} \times \sigma_{instance} + \mu_{instance}$$

# Loss Function
MSE

# 金融數據測試
TARGET_TICKER = 'NVDA' (預測目標T+5)

MARKET_FEATURES = ["TSM","AVGO","MU","AMD","ASML","LRCX","KLAC","TXN","QCOM","AMAT","ADI","INTC","SNPS","CDNS","MRVL"]
DATA_START_DATE = '2007-05-01'

TRAIN_END_DATE  = '2024-07-01'

TEST_START_DATE = '2025-01-01'

DATA_END_DATE   = '2025-12-31'


## 模型參數
WINDOW_SIZES = [256, 512,720]
D_MODEL = 32
EPOCHS = 10
LR = 0.001
BATCH_SIZE = 32

## Data type
餵入Log Price 不使用 log return 是希望保留所有數據細節讓模型自己挖掘特徵，如果餵入弱平穩數據反而丟失太多細節，論文作者是這樣建議

<img width="1909" height="1056" alt="image" src="https://github.com/user-attachments/assets/f52af7db-1db8-4e02-8c79-93837c07843e" />

## 樣本外殘差分布(預測值-實際值)
帶有一點偏態，模型沒有捕捉完全，不過以樣本外來說我覺得很不錯了
<img width="1248" height="787" alt="image" src="https://github.com/user-attachments/assets/177374d3-b90d-4009-9164-843c530cb132" />

