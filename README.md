# DQN-project
## 安裝套件
安裝 Gym 的 Atari 環境套件，初始化 MsPacman 環境
gym->環境建立
cv2->處理畫面（灰階、縮放）
numpy->數值計算
torch->建構神經網路
deque/namedtuple->儲存經驗回放
RecordVideo->錄製遊戲畫面
## 畫面預處理與 frame stack
一張圖看不出方向與速度->堆 4 張圖，可以讓 CNN 看出「動作」變化
## DQN 網路結構
CNN 網路從圖像中抽取特徵
最後輸出是每個動作的 Q 值（如：9 個動作 → 回傳 9 維向量）
## Replay Memory（經驗回放）
將舊資料保留，打破樣本之間的相依性（decorrelation）
可重複利用資料，提升樣本效率
## 設定超參數
GAMMA	折扣因子，未來獎勵的重要程度
BATCH_SIZE->一次訓練取樣的資料量
EPS_xx->epsilon-greedy 的探索策略參數
TARGET_UPDATE->多少 step 更新一次 target_net
LR->學習率
## 訓練主迴圈
### 初始化環境與網路
RecordVideo 每 10 局錄一支影片（輸出為 mp4）
### 每一局訓練流程
### 選擇動作（epsilon-greedy）
epsilon 控制「隨機 vs. 最佳動作」的比例
## 更新記憶體 + 訓練網路
## 反向傳播與 gradient clipping
Clip 梯度可以防止 Q 值暴衝，造成數值不穩
## 每 TARGET_UPDATE 步驟，同步 target_net

# 結論 : 靠著CNN+Frame stack擷取動態訊息，藉著Replay buffer儲存舊資料，用DQN來避免高估Q值，最終獲得還不錯的成果
