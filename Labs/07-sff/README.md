# Lab 7: Latches and Flip-flops

## 1. Preparation tasks

   | **clk** | **d** | **q(n)** | **q(n+1)** | **Comments** |
   | :-: | :-: | :-: | :-: | :-- |
   | ↑ | 0 | 0 | 0 |  |
   | ↑ | 0 | 1 | 1 |  |
   | ↑ | 1 |  | 1 |  |
   | ↑ | 1 |  | 1 |  |

   | **clk** | **j** | **k** | **q(n)** | **q(n+1)** | **Comments** |
   | :-: | :-: | :-: | :-: | :-: | :-- |
   | ↑ | 0 | 0 | 0 | 0 | No change |
   | ↑ | 0 | 0 | 1 | 1 | No change |
   | ↑ | 0 |  |  |  |  |
   | ↑ | 0 |  |  |  |  |
   | ↑ | 1 |  |  |  |  |
   | ↑ | 1 |  |  |  |  |
   | ↑ | 1 |  |  |  |  |
   | ↑ | 1 |  |  |  |  |

   | **clk** | **t** | **q(n)** | **q(n+1)** | **Comments** |
   | :-: | :-: | :-: | :-: | :-- |
   | ↑ | 0 | 0 |  |  |
   | ↑ | 0 | 1 |  |  |
   | ↑ | 1 |  |  |  |
   | ↑ | 1 |  |  |  |



## 2. Display driver
### 2.1. Listing of VHDL code of the process p_mux with syntax highlighting
© 2021 GitHub, Inc.
Terms
Privacy
Security
Status
Docs
Contact GitHub
Pricing
API
Training
Blog
About
