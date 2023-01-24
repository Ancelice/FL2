# FL2 (Federated Learing Ver.2)
連合学習（Federated Learning）における蒸留を用いた端末負荷と通信量の削減  
CIFAR-10を用いた画像認識において、クライアントの精度向上、システム全体の通信量削減を実現  
※今回は6, 8, 10, 12, 14層の、計5種類のモデルを設定  
![image](https://user-images.githubusercontent.com/103622417/214254456-cc57022f-1c9c-4789-9353-91fc2f25e9ac.png)


## Publications
矢島大路，小野翔多，三好 匠，山崎 託，シルバーストン トーマス，"Federated Learningにおける蒸留を用いたデバイス処理削減手法の検討," 電子情報通信学会ネットワークシステム研究会，はじめての研究会セッション，予稿なし，Oct. 2021. （初めての研究会講演奨励賞）  

Hiromichi YAJIMA, Takumi MIYOSHI, Taku YAMAZAKI, Shota ONO, and Thomas SILVERSTON, "Reducing Device Processing Cost in Federated Learning Using Distillation," 2022 IEICE General Conference, English Session, BS-3-2, pp. S-3 - S-4, March 2022. (The English Session Award of NS Technical Comittee, IEICE, Oct. 2022)  

矢島大路，三好 匠，山崎 託，小野翔多，"連合学習における蒸留を用いた処理負荷と通信量の削減（依頼公演）," 電子情報通信学会技術研究報告, Vol. 122, No. 198, NS2022-83, pp. 8-11, Oct. 2022.  

矢島大路，小野翔多，三好 匠，山崎 託, "蒸留を用いた連合学習における機械学習モデルのサイズが与える影響," 2023年電子情報通信学会総合大会, 発表予定  


## CIFAR-10
![image](https://user-images.githubusercontent.com/103622417/214209460-4dc083a3-e73e-4616-be91-e4a84b79fc64.png)

## 提案手法
![image](https://user-images.githubusercontent.com/103622417/214207753-db3a9f37-4f3b-4270-8419-c666ca53cc9e.png)

## 蒸留
![image](https://user-images.githubusercontent.com/103622417/214207802-392ad5da-4ae0-4c5a-9fc9-a4f10af4569e.png)


～保存場所～

プログラム  
＞client（クライアント側ではしらせるプログラム）  
＞server（サーバ側ではしらせるプログラム）  
＞result（実験で得られたCSVをグラフ化するプログラム）  

結果  
＞Figure（実験データのグラフのみ）  
＞Result（グラフとExcelファイル）  


～フォルダ命名規則～

(Server Global Model Size) - (Distilled Global Model Size)  
※10-10など，数字が等しいものは従来の連合学習（Federated Learning）、それ以外は提案手法  


～プログラムのはしらせ方～

今回の実験ではサーバ1台，クライアント3台を想定する


ex) 12-8の実験をするとき

サーバ側では"Server12-8.py"をはしらせる  
クライアントは"Client1-8.py, Client2-8.py, Client3-8.py をそれぞれはしらせる"  

※訓練データは計50,000枚ある．20,000枚はサーバに，残り30,000はクライアント3台で均等に分配し，4か所で保持されている訓練データに被りがないようにする  
※テストデータは計10,000枚．4か所で精度をはかるときにテストデータが同じでなければならないため，4か所すべてに10,000枚配布する  
※蒸留の作業は，まず訓練データ20,000枚を10,000ずつに分ける．次に片方の10,000に対し予測結果を出す．最後にこの予測結果10,000枚と手を付けていない残り10,000の計20,000を用い学習を行う  
