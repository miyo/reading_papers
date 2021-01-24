
- Title: HBM Connect: High-Performance HLS Interconnect for FPGA HBM
- Authors: Young-kyu Choi, Yuze Chi, Weikang Qiao, Nikola Samardzic, and Jason Cong

## 概要
FPGA HBMのための高性能なカスタム化したインタコネクト HBM Connect の提案．

- PE(processing element)がPC(pseudo channel)にアクセスするバースト長とバンド幅を増やすBRAMによるバッファリングスキーム
- クロスバの構成要素2x2のスループットを増やすHLSベースのソリューション
- 設計空間探索
- U280で試した

## 動機/先行研究との比較

Bucket SortとMerge Sortでケースタディ．
HLSとビルトインのAXIクロスバでは，うまくHBMの帯域を有効に使えない．

## 提案手法のキモ

- HBM Connectを，カスタムクロスバ，AXI burst buffer，ビルトインAXIクロスバで構成．
- カスタムクロスバ: マルチステージネットワーク(=バタフライネットワーク)
- AXI burst buffer: HLSでバッファを実装
- カスタムクロスバの段数とバーストバッファのサイズを探索できるように

## 検証方法
U280に実装．
- バケットソート: 実効バンド幅が65GB/s -> 203GB/s〜108GB/sに．
 - BW^2/LUTとBW^2/BRAMを指標に評価．それぞれ，6.5倍と9.8倍が最大．
マージソート: 実効バンド幅が9.4GB/sがベースライン
 - BW^2/LUTとBW^2/BRAMを指標に評価．それぞれ，211倍と85倍が最大．

## 議論

## 関連研究
HBMとDDRの比較は[19, 27]．[27]はShuhai(RTLベースのHBMベンチマーク)
ヘテロジニアスなメモリ階層向け最適化のケーススタディは[20]を参照
[19] A. Lu, et al., "Demystifying the memory system of modern datacenter FPGAs for software programmers through microbenchmarking"
[27] Z. Wang, et al., "Shuhai: Benchmarking High Bandwidth Memory on FPGAs"
[20] H. Miao, et al., "StreamboxHBM: Stream analytics on high bandwidth hybrid memory"

## その他メモ
- データ転送帯域の目安
 - [8] Virtex-7 690T<->DRAM: 13GB/s, Tesla K40: 290GB/s
 - [21] Sandy Brdge E5-2670<->DRAM: 42GB/s
