---
layout: post
title: capstone project
author: [Yuhsiang Lin]
category: [Lecture]
tags: [jekyll, ai]
---

期末專題實作:Deep Reinforcement Learning for Automated Stock Trading(股票交易強化學習)

---
## Deep Reinforcement Learning for Automated Stock Trading(股票交易強化學習)

### 系統簡介及功能說明

1. **系統簡介**:用多種深度強化學習方法集成來做交易策略，策略包含Q-learning的三種算法:Deep Q Network(DQN)、Double DQN及Dueling Double DQN，分析三種算法的特性，從而根據不同的市場條件進行調整。



2. **功能說明**:可以用於優化資本配置和最大化投資績效-例如預期回報。預期回報最大化可以由對潛在回報和風險的估計而獲得。

---
### 系統方塊圖
系統流程圖<br>
![](https://github.com/00953001/AI-course/blob/gh-pages/images/DIAGRAM%20FOR%20STOCK%20%20DeepLearning.png?raw=true)


AI模型說明<br>
**QDN**

![](https://pic4.zhimg.com/v2-af5301606efb58939e09e007094e8a3f_r.jpg)

DQN有兩個網絡，分別是預測網絡（Predict Q Network）和目標網絡（Target Q Network），預測網絡用來預測當前狀態對應各個動作的Q值，目標網絡用來預測下一個，或者下第幾個狀態各個動作的Q值。

![](https://pic4.zhimg.com/v2-5e05f3af72d4885dfc3fc2e0a35388bb_r.jpg)

**DDQN**

![](https://pic3.zhimg.com/80/v2-d5de8538f067a0a0a67a5da3d8e9f59e_720w.webp)

在double q-learning中，是兩個estimator相互疊代估計，每個estimator從經驗集中的一個子集中學習，但在double DQN中並不一樣，為了達到和DQN即為相似的結構只是在DQN的基礎上將online network直接用於求max時找action的index，然後就完全按照DQN中用target network的periodic copy來進行target的估計。直覺上與double q-learning相差很大，q-learning的理論分析不一定能直接套上。

**Dueling double DQN**

![](https://pic2.zhimg.com/v2-e86875688ee51e15f8ef284be38275e1_r.jpg)

Dueling DQN的思想就是獨立的學出Value和Advantage，將它們加起來組成Q，而不是像傳統DQN那樣直接學出所有的Q值

---
### 製作步驟

1. 建立資料集 dataset
2. 移植程式to Kaggle
3. Kaggle上訓練模型
4. Kaggle上測試模型

---
### 系統測試及成果展示

![](https://github.com/00953001/AI-course/blob/gh-pages/images/newplot%20(1).png?raw=true)

**DQN**

![](https://github.com/00953001/AI-course/blob/gh-pages/images/newplot.png?raw=true)

Loss and Reward

![](https://github.com/00953001/AI-course/blob/gh-pages/images/newplot%20(2).png?raw=true)

**DDQN**

![](https://github.com/00953001/AI-course/blob/gh-pages/images/newplot%20(3).png?raw=true)

Loss and Reward

![](https://github.com/00953001/AI-course/blob/gh-pages/images/newplot%20(4).png?raw=true)

**Dueling DDQN**

![](https://github.com/00953001/AI-course/blob/gh-pages/images/newplot%20(5).png?raw=true)

Loss and Reward

![](https://github.com/00953001/AI-course/blob/gh-pages/images/newplot%20(6).png?raw=true)

### 結論

從13年-2017年，DQN做的東西很多是搭了Deep learning的快車，大部分idea在傳統RL中已經有了，如何把它們融入Deep network是主要方向。

2013的DQN出現具有重要意義，實現了q-learning在網絡中無法收斂的問題，而且如同deep learning的大部分工作一樣（nlp，GNN...）端到端一體化。DQN的兩個關鍵點在於experience replay和q-target設計，這也是最大的貢獻，後續的工作沿著這兩個問題繼續做。

q-target好像一個estimator不太夠：double DQN利用兩個estimator解決overestimate的問題；

q-target設計太簡單表達能力不夠：Dueling DQN則是從結構上的改進，更像是一種正則化手段增強學習能。

後續的工作更多在於如何利用experience replay和q-target設計更加平穩快速地估計q值的問題。

kaggle 網址:https://www.kaggle.com/yu0116/q-learning-on-stock

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*

