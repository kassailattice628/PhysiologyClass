# Quick NI-DAQ recording on MATLAB
NIDAQ (USB6009) を使用して GUI つき簡易記録．

---
Original: https://github.com/kassailattice628/Physiology_StudentExp.git
## Requirement
1. Windwos 10/11で動作確認．  
2. MATLAB 2022a で動作確認． appdesigner を使用しているので， バージョン違う場合，自動で色々変更される可能性あり．
4. Data acquisition toolbox (64bit) 必須．  
5. NIDAQ サポートパッケージ（MATLAB アドオンから入手）

### Instration Drivers
NIDAQ-mx は matlab のアドオンから．
（ホームタブメニュー > （環境）アドオン > ハードウェアサポートパッケージの入手）  

### DAQ devices
NIDAQ USB-6009．これはおそらくなんでも使える．  
デバイスを変更する場合は appdesigner 上で DAQ の名称を変更する必要あり．  
複数の NI-DAQ デバイスを使用している場合，表示名 "Dev1" などが自動で割り振られるため
こちらも変更必要あり．

### Input Channel
現在は，差動入力で Ch(1) しか設定していない（AI0)．  
複数 Ch の場合は， addinput を追加．

---
## Usage << MainRecDaQ2_2023.mlapp>>
PhysiologyClass フォルダに移動して  
`MainRecDAQ2_2023`  
とするか， appdesigner 上で起動．

1. Start/Stop ボタンでオシロモードの on/off

2. データを記録する場合は， Start した状態で， Capture．  
Capture を押すと 域値を超える入力がくるまで待機．域値の設定は，Pause 中に Trigger Level で編集．  
取得データの範囲（時間）は，Trigger の前後数秒． 設定は，Pause 中に Capture Pre-Trig, Post-Trig で編集．   
Pre-Trig で設定した時間を経過してない場合は，，エラーが出るので注意．

3. Triger 検出すると，指定した時間分のデータが Varibale Name で指定した 変数で MATLAB の workspace に保存．  
複数回記録した場合は，その変数（cell 配列）にデータが追加される．  
Capture が終了するごとに，mydata_1.mat のように個別にファイルは保存されていく． 
---
## Usage <<ViewData.mlapp>>
`ViewData`  
もしくは， appdesigner 上から

---
## Done
- Matlabのライセンスが CWL　になったため，オフラインでも使用できるようになった．
- アプリ化したものは変更ができないので， appdesigner で作り直し．
- 大まかな機能は，以前のバージョンと同じだが， MATLAB のバージョンアップにより daq toolbox のセッティングは大きく変更した．

