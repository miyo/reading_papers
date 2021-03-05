
- title: Compiler-Driven FPGA Virtualization with SYNERGY Extended Abstract
- authors: Joshua Landgraf, Tiffany Yang, Will Lin, Christopher J. Rossbach, Eric Schkufza

## 概要

- FPGA仮想化のためのJITとリソース管理/プロテクションレイヤをあわせたSYNERGYの提案

## 背景

- AmorphOS [12]
  - multitenancy のための cross-program protection と cross-platform compatibility をサポート．FPGAファブリック量の動的なスケーリングができる．
  - アプリケーション状態管理はインターフェースを提供してユーザ任せ．over-subscriptionと複数FPGAは未解決
- Cascade [21]
  - VerilogのJITコンパイラ．ハードウェアプログラムをソフトウェアシミュレーションとFPGAファブリックで実行
  - コンテクストスイッチ，マイグレーションといった仮想化のプリミティブはもってない．細粒度の制御は不足．

## 論文のキモ

- FPGA仮想化には，コンパイラとランタイムが必要
- SYNERGYは，JITとリソース管理/プロテクションレイヤをあわせたもの
- SYNERGY’s first contribution is a set of compiler transformations to produce code that can be interrupted at sub-clocktick granularity according to the semantics of the original program.
- SYNERGY’s second contribution is a new technique for FPGA multi-tenancy.
- SYNERGY’s final contribution is a compiler backend targeting an OS-level protection layer for process isolation, fair scheduling, and cross-platform compatibility.

## 評価内容

## 議論

## 関連研究
- Ahmed Khawaja, Joshua Landgraf, Rohith Prakash, Michael Wei, Eric Schkufza, and Christopher J Rossbach. Sharing, protection, and compatibility for reconfigurable fabric with amorphos. In 13th {USENIX} Symposium on Operating Systems Design and Implementation ({OSDI} 18), pages 107–127, 2018.
- Eric Schkufza, Michael Wei, and Christopher J. Rossbach. Just-intime compilation for verilog: A new technique for improving the FPGA programming experience. In Proceedings of the Twenty-Fourth International Conference on Architectural Support for Programming Languages and Operating Systems, ASPLOS 2019, Providence, RI, USA, April 13-17, 2019, pages 271–286, 2019.

## その他メモ

