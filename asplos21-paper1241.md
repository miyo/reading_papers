
- title: CutQC: Using Small Quantum Computers for Large Quantum Circuit Evaluations
- authors: Wei Tang, Teague Tomesh, Jeffrey Larson, Martin Suchara, Margaret Martonosi

## 概要

## 背景

- As a result, both the noise and the intermediate-scale characteristics of NISQ devices present significant obstacles to their practical use.
- To realize quantum advantage in the near future, we need to better utilize near-term NISQ quantum computers. This work develops and demonstrates a comprehensive methodology for cutting large quantum circuits.

- The recently developed ones include use of real-time device calibration data to improve circuit fidelity by optimally mapping logical qubits to physical ones [18, 19], efficiently scheduling operations to reduce quantum gate counts [20], and repeating circuit executions to mitigate error [21, 22, 23].
  - These techniques do not allow executions of circuits requiring more qubits than are on the device, and their reliability improvement is limited.
- Our work addresses all of these shortcomings, applying efficient partitioning and highly parallelizable postprocessing techniques to realize a practical circuit cutting implementation. This allows for useful trade-offs between classical and quantum compute resources.

## 論文のキモ

- The core insight from this work is that mixed-integer programming (MIP) can efficiently find cut locations to partition general quantum circuits and distribute the workload between quantum and classical platforms. 

## 評価内容

- To evaluate the performance of CutQC, we benchmarked six different quantum circuits that represent a general set of circuits for gate-based QC platforms and promising near-term applications.

## 議論

## 関連研究

- optimally maping
  - [18] Prakash Murali, Jonathan M Baker, Ali Javadi-Abhari, Frederic T Chong, and Margaret Martonosi. Noise-adaptive compiler mappings for noisy intermediate-scale quantum computers. In Proceedings of the Twenty-Fourth International Conference on Architectural Support for Programming Languages and Operating Systems, pages 1015–1029, 2019.
  - [19] Swamit S Tannu and Moinuddin K Qureshi. Not all qubits are created equal: a case for variability-aware policies for NISQ-era quantum computers. In Proceedings of the Twenty-Fourth International Conference on Architectural Support for Programming Languages and Operating Systems, pages 987–999, 2019.
- scheduling operations
  - [20] Jeff Heckey, Shruti Patil, Ali JavadiAbhari, Adam Holmes, Daniel Kudrow, Kenneth R Brown, Diana Franklin, Frederic T Chong, and Margaret Martonosi. Compiler management of communication and parallelism for quantum computation. In Proceedings of the Twentieth International Conference on Architectural Support for Programming Languages and Operating Systems, pages 445–456, 2015.
- repeating circuit executions to mitigate error
  - [21] Abhinav Kandala, Kristan Temme, Antonio D Córcoles, Antonio Mezzacapo, Jerry M Chow, and Jay M Gambetta. Error mitigation extends the computational reach of a noisy quantum processor. Nature, 567(7749):491, 2019.
  - [22] Swamit S Tannu and Moinuddin Qureshi. Ensemble of diverse mappings: Improving reliability of quantum computers by orchestrating dissimilar mistakes. In Proceedings of the 52nd Annual IEEE/ACM International Symposium on Microarchitecture, pages 253–265, 2019.
  - [23] Swamit S Tannu and Moinuddin K Qureshi. Mitigating measurement errors in quantum computers by exploiting state-dependent bias. In Proceedings of the 52nd Annual IEEE/ACM International Symposium on Microarchitecture, pages 279–290, 2019.

## その他メモ

