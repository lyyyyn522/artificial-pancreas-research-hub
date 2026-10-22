# 人工胰腺系统概览

> 本文是人工胰腺研究的入门笔记，介绍系统组成与基本信息流，不构成医疗建议。

## 1. 什么是人工胰腺？

人工胰腺（artificial pancreas）是由传感器、控制算法和胰岛素输注设备协同工作的系统，旨在部分自动化血糖监测与胰岛素输注。它也常被称为自动胰岛素输注（automated insulin delivery, AID）或闭环系统（closed-loop system）。

“人工胰腺”并不意味着它完全复制了健康胰腺的全部功能。研究和设备应用中所说的系统通常聚焦于根据血糖相关信息自动调整胰岛素输注。

## 2. 系统的主要组成

典型系统包括以下三个部分：

1. **连续血糖监测系统（CGM）**  
   持续采集血糖相关读数，并将数据传送给控制算法。CGM 读数是算法的输入，不应简单等同于任一时刻的实验室血糖测量。

2. **控制算法**  
   根据 CGM 数据及系统设定，计算或调整胰岛素输注指令。算法是连接监测与输注的决策部分。

3. **胰岛素泵**  
   接收算法指令并输注胰岛素。

基本信息流可以表示为：

**CGM 读数 → 控制算法 → 胰岛素泵 → 人体血糖变化 → CGM 后续读数**

这个反馈环路是“闭环”概念的核心。

## 3. 开环、闭环与混合闭环

- **开环管理**：监测信息与胰岛素输注之间没有由算法自动形成的完整反馈控制环路，用户或医护人员需要参与决策。
- **闭环自动化**：算法根据传感器数据自动调整胰岛素输注。
- **混合闭环（hybrid closed loop）**：部分输注调整自动进行，但某些场景仍需要用户输入信息，例如进餐相关信息。具体自动化程度会因系统而异，应查阅对应设备或研究的定义。

阅读论文时，不要只看作者使用了“人工胰腺”或“闭环”这个名称；还要核对系统自动执行了哪些功能、需要哪些人工输入。

## 4. 血糖预测在系统中的位置

血糖预测模型可以估计未来一段时间内的血糖变化，作为控制算法的输入或辅助信息。研究时应区分两个不同问题：

- **预测问题**：模型对未来血糖值或风险事件预测得怎样？
- **控制问题**：系统使用这些信息后，胰岛素输注与整体闭环表现怎样？

因此，较低的预测误差本身不能证明闭环控制安全有效。预测模型和控制策略需要分别描述、分别评估。

## 5. 研究时需要关注的系统因素

- CGM 数据的误差、缺失与时间延迟
- 胰岛素输注对血糖变化的作用并非即时发生
- 进餐、运动和个体差异等因素可能影响血糖变化
- 传感器、通信、算法或泵发生问题时，系统如何处理
- 测试是在离线数据、仿真环境还是实际研究场景中完成

这些因素意味着：离线预测实验、仿真控制实验和真实场景评估是不同层次的证据，不能互相替代。

## 6. 本仓库的研究边界

本仓库整理的是科研与学习资料。模型示例、预测结果或仿真结果不构成个人医疗建议，也不能直接用于真实设备的自动给药决策。

## 7. 参考资料

- National Institute of Diabetes and Digestive and Kidney Diseases (NIDDK). [Artificial Pancreas](https://www.niddk.nih.gov/health-information/diabetes/overview/managing-diabetes/artificial-pancreas)
- U.S. Food and Drug Administration (FDA). [What is the pancreas? What is an artificial pancreas device system?](https://www.fda.gov/medical-devices/artificial-pancreas-device-system/what-pancreas-what-artificial-pancreas-device-system)
- U.S. Food and Drug Administration (FDA). [Types of Artificial Pancreas Device Systems](https://www.fda.gov/medical-devices/artificial-pancreas-device-system/types-artificial-pancreas-device-systems)

## 8. 待进一步学习

- [ ] CGM 测量的是什么？与血糖测量有哪些区别？
- [ ] 控制算法会使用哪些输入？
- [ ] 血糖预测任务如何定义预测时距？
- [ ] 离线预测评估与闭环仿真评估有什么区别？
