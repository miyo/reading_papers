
- Title: Demystifying the Memory System of Modern Datacenter FPGAs for Software Programmers through Microbenchmarking
- Authors: Alec Lu, Zhenman Fang, Weihua Liu, Lesley Shannon

## 概要

- HLS設計でデータセンタ向けFPGAのメモリシステムを効率的に使う方法を示す．
 - ナイーブな実装だとオフチップメモリバンド幅の5%程度にしかならない
- メモリバンド幅に影響する要素として，並列アクセスポート数/各ポートのデータ幅/各ポートのバースト長/連続アクセス数に着目
- U200とU280向けにマイクロベンチマークを実装して評価
- KNNとSpMVを高速化．ベースデザインと比べて，それぞれ3.5倍，8.5倍高速化

## 動機/先行研究との比較

FPGAボードのオフチップメモリとHBMの性能を知りたい

## やったこと

- マイクロベンチマークで性能評価した
 - Vivado HLS/Vitis向けの設計
 - 実装: https://github.com/SFU-HiAccel/uBench
- ケーススタディ(KNN, SpMV)で性能評価/最適化してみた

## 結果

- シングルポート
 - バンド幅
  - 512bitで頭打ち
   - DDR4バンクは512bit，HBMは256-bitだけどHBMCが450MHzでロジックが300MHzだから
  - 連続アクセス
   - 128KBで頭打ち(DDR4-read/write, HBM-read)
   - 32KBで頭打ち(HBM-write)
  - DDR理論値は19.2GB/s -> 実効値は17.94GBps(read), 16.11GB/s(write)
  - HBM理論値は14.4GB/s -> 実効値は13.2GBps([28]の13.27GBpsよりもちょっと遅かった)
  - `max_burst_length`, `num_outstanding_access` パラメタで性能向上
 - リソース使用量，あれこれ
- 複数ポート
 - U200のDDR4 x4の最大性能は，71.7GB/s(read)，64.6GB/s(write)
  - `max_burst_size`が16Kbになるように(できないときは，`max_burst_length`を256に)
  - データ幅は512-bit
 - HBMは，421.6GB/s(read)，421.8GB/s(write)
  - 512bit幅@300MHz
  - 32HBMバンク
- 複数引数で単一AXIポートをシェアする場合
- カーネル間の転送帯域
 - bit幅増やすと速くなる．1024bitで最大38.28GB/s
 - ポート数増やすと速くなる 32x1024bitで最大612.84GB/s
- ケーススタディ
 - KNN: 1x -> 3.5xに高速化(24-thread CPU(CPU;Xeon Silver 4214x2) の 5.6倍高速化)
 - SpMV: 1x -> 8.5xに高速化(24-thread CPU実装の3.4倍高速化)

## 関連研究

- 32bitデータタイプを使ったHLS設計での測定 [17] Jason Cong et al., "Bandwidth Optimization Through On-Chip Memory Restructuring for HLS" (off-chipでは1/16だったそうな)
- HLSベース設計でDRAMの83%(DDR3; 12.8GBpsに対して10GBps)の実効性能を達成 [36] Chen Zhang, et al., "Caffeine: Toward Uniformed Representation and Acceleration for Deep Convolutional Neural Networks"

## その他メモ
