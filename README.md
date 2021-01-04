# AIOps
有关AIOps场景汇总及相关算法介绍
## 第一次讨论 主题：异常检测
**时间**：2020.12.28～2021.1.10

**背景**：异常检测是监控系统中一项基础且重要功能，其旨在自动地发现时间序列数据中的异常波动，作为后续的告警、自动止损、根因分析等重要前置条件。在实际场景下，传统的依靠固定阈值、同环比等发现异常点，会由于数据的变动等导致检测结果不准确；基于算法的异常检测，由于异常点数据稀少，异常类型多样以及KPI类型多样，也会给算法设计造成一定难度。讨论的点是：
1. 大家的异常检测，主要用在哪一些场景，例如：kpi类的业务指标、系统cpu until等；
2. 目前的异常检测有哪一些痛点，比如：误报率高、监控数据缺失等；
3. 对于误报、准确率容忍度
   
**模版**：
- 介绍领域的背景。金融银行领域、电商领域等；
- 目前异常检测使用情况；
- 目前异常检测所遇到的一些痛点。
  
### 第一阶段 场景收集
**时间**：2020.12.28～2021.1.4

**形式**：按照模版收集、合并大家的问题，在2021.1.4日将所有问题总结汇总到这里。

**问题概括**：
- 采用predict+n*sigma的方式构造上界做异常检测，其中predict是用指数平滑计算出来的预测值，sigma用的是历史数据的方差。但是数据周期性较差，波动较大，导致历史数据计算出来的方差较大，是否有更好的计算上界的方式，不受波动较大的历史数据影响？
- 业务数据订单数量会受各种营销活动的影响，导致异常检测漏报或者误报
- 业务数据订单数量小的时候，异常检测效果较差
- 应用exception报错，存在波动较大的情况
- 目前一般来说，异常检测后，如果出现异常会出告警；业务收到告警可能会打标。一般来说，到业务打标以后异常检测就成为闭环。但是实际来看，仅仅01的打标对模型提升的效果相对有限，在共同提升模型性能的闭环设计层面，大家有没有较好的体感或者建议呢？
### 第二阶段 问题讨论
**时间**：2021.1.4～2021.1.10

**形式**：针对收集的痛点，大家集思广益，在跨领域、跨岗位的讨论中是否能碰撞一些火花。最终在2021.1.10将问题与对应解决思路整理成文字。

