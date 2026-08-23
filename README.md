# 论文主页与研究概述

这个仓库用于集中展示 4 篇与随机接入、能量收集、信息年龄和空间容量相关的论文。主页文件为 `index.html`，论文 PDF 位于 `papers/` 目录。


## 论文列表

### 1. 能量收集型短包通信 LoRa 网络的信息年龄建模与优化

PDF：[`info-age-lora-energy-harvesting-short-packet.pdf`](papers/info-age-lora-energy-harvesting-short-packet.pdf)

**研究背景：**  
工业物联网中的 LoRa 节点通常具有低功耗、广覆盖和短包通信等特点，但节点能量受限，且需要长期依靠环境能量收集维持运行。对于状态监测、工业控制等场景，仅追求吞吐量或时延并不能准确反映信息是否足够新鲜，因此信息年龄（Age of Information, AoI）成为衡量接收端信息新鲜度的重要指标。已有 AoI 研究多基于抽象随机接入模型或理想供能假设，难以直接刻画能量收集短包 LoRa 网络中的能量队列、短包解码和随机接入冲突之间的耦合关系。

**主要工作：**  
论文面向能量收集驱动的短包通信 LoRa 网络，建立了基于时隙 Aloha 的随机接入模型，并将节点能量队列建模为马尔可夫链。在此基础上，结合短包编码理论和碰撞模型，推导平均 AoI 的解析表达式。论文进一步分别研究最小电池容量和理想无限电池容量两类极端场景：前者用于刻画能量存储受限时的性能下限，后者用于分析消除存储瓶颈后的理论性能上限，并围绕数据包生成概率和块长度进行 AoI 优化。

**主要成果：**  
论文给出了平均 AoI 的一般表达式，并推导了不同电池容量条件下的最优参数选择策略。在最小电池容量场景中，系统主要通过调整数据包生成概率来优化 AoI；在理想无限电池容量场景中，系统可联合优化块长度和生成概率。仿真结果验证了理论分析的准确性，并表明联合优化能够显著改善大规模网络中的 AoI 表现，使优化后的平均 AoI 随节点数近似线性增长。论文还揭示了能量受限区间和能量充足区间下最优策略的差异：能量受限时倾向于更积极接入以充分利用能量，能量充足时则倾向于通过降低接入频率或增大块长度缓解信道碰撞。

### 2. Information Freshness in Random Access Networks with Energy Harvesting

PDF：[`information-freshness-random-access-energy-harvesting.pdf`](papers/information-freshness-random-access-energy-harvesting.pdf)

**研究背景：**  
在物联网系统中，传感节点需要持续上报状态信息，但许多节点受电池容量和能量补给限制。能量收集技术可以延长节点寿命，却也会导致节点因能量不足而暂时沉默，从而影响信息新鲜度。已有关于能量收集 AoI 的研究多集中在点对点通信场景，而实际 IoT 网络通常由大量节点共享信道并通过随机接入竞争传输机会，因此冲突、能量到达和更新频率之间的相互作用需要进一步分析。

**主要工作：**  
论文研究了能量收集驱动的时隙 Aloha 随机接入网络中的平均 AoI。系统采用 generate-at-will 策略，节点在决定发送时生成最新状态包，并在能量缓存非空时以一定概率接入信道。论文针对一般能量缓存容量推导平均 AoI 的闭式表达式，并进一步在单位缓存和无限缓存两种情形下优化更新率。

**主要成果：**  
论文证明，当所有节点的能量到达率之和大于或等于 1 时，通过将更新率设置为节点总数的倒数，能量收集 Aloha 网络可以达到与无能量约束网络相同或近似相同的最优平均 AoI，此时优化后的 AoI 随节点数线性增长。当总能量到达率小于 1 时，能量短缺会带来 AoI 性能损失，最优更新率应高于单节点能量到达率，以在能量积累和更新及时性之间取得平衡。仿真结果表明，适当调节更新率可以避免固定接入策略下 AoI 随网络规模快速恶化的问题；同时，无限缓存情形下的最优更新率可作为较大有限缓存场景的紧近似。

### 3. Spatial Capacity of Random-Access Poisson Networks

PDF：[`spatial-capacity-random-access-poisson-networks.pdf`](papers/spatial-capacity-random-access-poisson-networks.pdf)

**研究背景：**  
大规模 IoT 网络通常采用分布式随机接入来降低集中调度开销，但节点密集部署会造成强干扰。如果接入概率、重传退避参数或接收门限配置不当，网络空间容量会显著下降。传统随机接入分析往往假设节点始终活跃，或只用二元队列状态描述节点是否有包发送，难以刻画实际退避协议中不同失败次数对应不同接入概率所造成的状态相关干扰。

**主要工作：**  
论文研究基于时隙 Aloha 的 Poisson bipolar 网络，在饱和业务假设下建立一个联合空间干扰和时间状态转移的时空分析框架。论文将队首包（HOL packet）的退避状态建模为离散时间马尔可夫链，并用随机几何刻画不同退避状态下发射节点的空间分布。基于解耦近似，论文推导成功传输概率的不动点表达式、典型链路吞吐量以及空间容量表达式，并进一步优化初始传输概率和接收门限。

**主要成果：**  
论文给出了最大空间容量、最优初始传输概率和最优接收门限的半闭式刻画。结果表明，在竞争受限区域中，一旦初始传输概率经过优化，最大吞吐量与具体退避函数和最大退避阶段无关，而主要由接收门限、信噪比、节点密度和链路距离决定；当优化参数达到饱和时，退避函数会重新影响性能。论文还揭示了不同 SNR 区域下的设计规律：低 SNR 区域中，最大空间容量和最优接收门限随接收 SNR 近似线性变化，且容量随节点密度增加而提高；高 SNR 区域中，网络进入干扰受限状态，最优接收门限只由路径损耗指数决定，最大容量趋于饱和并不再依赖节点密度。此外，论文证明最大空间容量随收发距离单调下降，并通过仿真验证了分析框架的准确性。

### 4. To Sense or Not To Sense: An AoI Perspective in Energy-Harvesting Networks

PDF：[`to-sense-or-not-to-sense-aoi-energy-harvesting-networks.pdf`](papers/to-sense-or-not-to-sense-aoi-energy-harvesting-networks.pdf)

**研究背景：**  
随机接入网络中，Aloha 和 CSMA 是两类代表性协议。Aloha 机制简单，适合短包和大量低功耗节点；CSMA 通过发送前信道侦听降低碰撞，通常能提升接入效率。然而，在能量收集网络中，节点传输行为同时受能量到达、信道状态和接入机制影响，已有工作对能量收集 CSMA 网络的信息年龄分析仍较少。尤其是在 AoI 视角下，何时值得通过信道侦听减少碰撞，何时应采用更简单的 Aloha，是一个需要系统比较的问题。

**主要工作：**  
论文研究能量收集 CSMA 网络中的平均 AoI，建立随机能量到达过程和信道状态演化模型，并推导任意能量缓存容量下的平均 AoI 闭式表达式。在无限能量缓存假设下，论文进一步求解最优数据包生成率及对应的最小平均 AoI。随后，论文将优化后的 EH-CSMA 与 EH-Aloha 进行对比，用以判断不同网络配置下信道侦听机制是否带来 AoI 优势。

**主要成果：**  
论文表明，CSMA 的信道侦听可以显著降低碰撞，从而在小 mini-slot 长度、低传播时延或密集网络中明显降低平均 AoI；优化后的平均 AoI 随网络规模近似线性增长，且最优生成率会随节点数增加而降低，以平衡更新频率和碰撞风险。与 Aloha 的比较显示，当信道侦听开销较小，CSMA 通常具有更好的信息新鲜度；但当 mini-slot 长度增大、传播时延或侦听开销较高时，CSMA 的额外等待会抵消其避碰优势，Aloha 反而可能获得更低 AoI。论文进一步给出了临界 mini-slot 长度随能量到达率变化的规律，为能量收集随机接入网络中的协议选择提供了理论依据。

## 研究脉络总结

这 4 篇论文围绕低功耗物联网随机接入网络展开，核心关注两个问题：

1. 如何在能量受限或能量收集条件下保持信息新鲜度；
2. 如何在大规模随机接入网络中通过接入概率、退避机制、块长度和接收门限优化系统性能。

其中，前两篇侧重能量收集 Aloha 网络的信息年龄建模与更新率优化；第一篇进一步结合 LoRa 短包通信和块长度优化，面向工业物联网应用。第三篇从空间容量角度研究 Poisson 随机接入网络的退避和门限设计，为密集网络的吞吐容量优化提供理论工具。第四篇则在 AoI 框架下比较 EH-CSMA 与 EH-Aloha，回答在能量收集网络中是否值得进行信道侦听的问题。

## GitHub Pages 发布方式

如果仓库还没有启用 Pages，可按以下步骤操作：

1. 进入 GitHub 仓库 `AllisAlright/Papers`。
2. 打开 `Settings` -> `Pages`。
3. Source 选择 `Deploy from a branch`。
4. Branch 选择 `main`，文件夹选择 `/root`。
5. 保存后等待几分钟，页面会发布到：

```text
https://allisalright.github.io/Papers/
```

## 单篇 PDF 链接

```text
https://allisalright.github.io/Papers/papers/info-age-lora-energy-harvesting-short-packet.pdf
https://allisalright.github.io/Papers/papers/information-freshness-random-access-energy-harvesting.pdf
https://allisalright.github.io/Papers/papers/spatial-capacity-random-access-poisson-networks.pdf
https://allisalright.github.io/Papers/papers/to-sense-or-not-to-sense-aoi-energy-harvesting-networks.pdf
```
