---
tags:
  - 误差理论
  - 例题
  - 练习题
source: Google检索-误差理论例题
---

# Google 检索例题与练习题

## P0 检索范围

| 专题 | 检索词 | 主要来源 |
|---|---|---|
| 系统误差 | systematic error example problems | Scribbr, Statistics How To, Purdue Chemistry |
| 随机误差 | random error standard deviation measurement examples | Scribbr, UMD Physics, Chemistry LibreTexts |
| 测量误差模型 | measurement error true value observed value examples | MathWords, Statistics How To, Classical Test Theory |
| MSA 测量系统分析 | MSA Gauge R&R example problems | Quality Magazine, EMS Handbook, Muelaner |
| 测量不确定度 | measurement uncertainty Type A Type B example | NIST, GUM Annex H, Muelaner |

## P0 来源链接

| 编号 | 来源 |
|---|---|
| G-01 | [Scribbr: Random vs. Systematic Error](https://www.scribbr.com/methodology/random-vs-systematic-error/) |
| G-02 | [Statistics How To: Systematic Error / Random Error](https://www.statisticshowto.com/experimental-design/systematic-error-random-error/) |
| G-03 | [Purdue Chemistry: Errors](https://chemed.chem.purdue.edu/genchem/topicreview/bp/ch1/errors.php) |
| G-04 | [UMD Physics: Random vs Systematic Error](https://physics.umd.edu/courses/Phys276/Hill/Information/Notes/ErrorAnalysis.html) |
| G-05 | [Chemistry LibreTexts: Measurement Errors](https://chem.libretexts.org/Ancillary_Materials/Worksheets/Worksheets%3A_Analytical_Chemistry_II/Measurement_Errors) |
| G-06 | [MathWords: Measurement Error](https://www.mathwords.com/e/error_measurement.htm) |
| G-07 | [Statistics How To: Measurement Error](https://www.statisticshowto.com/measurement-error/) |
| G-08 | [Statistics How To: Classical Test Theory](https://www.statisticshowto.com/classical-test-theory/) |
| G-09 | [Quality Magazine: Measurement Systems Analysis](https://www.qualitymag.com/articles/97565-measurement-systems-analysis) |
| G-10 | [EMS Handbook: Gauge R&R](https://emshandbook.com/vol-09/6/measurement-system-analysis-gauge-rr/) |
| G-11 | [Muelaner: Measurement Systems Analysis and Gage R&R](https://www.muelaner.com/measurement-systems-analysis-msa/) |
| G-12 | [NIST: Five Examples of Assessment and Expression of Measurement Uncertainty](https://www.nist.gov/publications/five-examples-assessment-and-expression-measurement-uncertainty) |
| G-13 | [NIST TN 1297 Appendix D2](https://www.nist.gov/node/768256) |
| G-14 | [GUM Annex H Examples](https://www.iso.org/sites/JCGM/GUM/JCGM100/C045315e-html/C045315e_FILES/MAIN_C045315e/AH_e.html) |
| G-15 | [Muelaner: Evaluating Uncertainty of Measurement](https://www.muelaner.com/uncertainty-of-measurement/) |

---

## 专题一：系统误差

### 来源例题 1：未校准天平

| 项目 | 内容 |
|---|---|
| 来源轴 | G-01, G-03 |
| 题目 | 某天平每次称量都比真实质量高 0.8 g。称量 5 个样品后求平均值，能否消除该误差？ |
| 解答 | 不能。该误差方向和大小稳定，是系统误差。求平均只能减弱随机波动，不能自动消除固定偏倚。 |

### 来源例题 2：拉长的卷尺

| 项目  | 内容                                     |
| --- | -------------------------------------- |
| 来源轴 | G-02                                   |
| 题目  | 一把旧塑料卷尺被拉长，用它测长度时读数总偏高还是偏低？属于哪类误差？     |
| 解答  | 读数会偏低：同样标称刻度对应的真实长度变长。它由工具状态造成，属于系统误差。 |

### 来源例题 3：滴定终点总是晚判

| 项目 | 内容 |
|---|---|
| 来源轴 | G-03 |
| 题目 | 滴定实验中，操作者总是在颜色变化后才读终点，导致体积读数偏大。该误差如何处理？ |
| 解答 | 这是人为判读造成的系统误差。处理方式是统一终点判据、训练操作、做空白或校正。 |

### 练习题

| 编号 | 题目 | 参考答案 |
|---|---|---|
| S-1 | 温度计零点偏高 0.5 ℃，连续测 10 次水温并取平均，平均值还会偏高吗？ | 会。零点偏高是系统误差，平均不能消除。 |
| S-2 | 电流表长期未校准，所有读数约低 2%。这是定值系统误差还是比例系统误差？ | 比例系统误差，偏差随真实读数按比例变化。 |
| S-3 | 如何判断一组测量是否存在系统误差？ | 与标准值或校准值比较，看偏差是否长期同向、稳定或按规律变化。 |

---

## 专题二：随机误差

### 来源例题 1：同一长度多次读数不同

| 项目  | 内容                                                   |
| --- | ---------------------------------------------------- |
| 来源轴 | G-01, G-04                                           |
| 题目  | 同一把尺测同一物体，读数为 10.1、10.0、10.2、10.1 cm。误差主要影响准确度还是精密度？ |
| 解答  | 这些读数围绕某个中心波动，主要体现随机误差，影响精密度。                         |

### 来源例题 2：设备短时波动

| 项目  | 内容                                   |
| --- | ------------------------------------ |
| 来源轴 | G-05                                 |
| 题目  | 仪器读数受瞬时噪声影响，重复测量出现正负不定的小偏差。应如何估计该误差？ |
| 解答  | 用重复测量的标准差或标准误估计随机误差。                 |

### 来源例题 3：平均值能减弱随机误差

| 项目 | 内容 |
|---|---|
| 来源轴 | G-01 |
| 题目 | 为什么样本量变大时，随机误差对平均值的影响通常变小？ |
| 解答 | 随机误差方向不固定，正负波动在平均中会部分抵消。标准误常随 $1/\sqrt{n}$ 下降。 |

### 练习题

| 编号  | 题目                                    | 参考答案                   |
| --- | ------------------------------------- | ---------------------- |
| R-1 | 某量重复测量 4 次：9.8、10.1、10.0、10.2。平均值是多少？ | $10.025$。              |
| R-2 | 若单次测量标准差为 0.30，重复独立测量 9 次，平均值标准误约为多少？ | $0.30/\sqrt{9}=0.10$。  |
| R-3 | 随机误差为什么不能用一个固定修正量完全消除？                | 因为每次误差大小和方向不固定，只能统计描述。 |

---

## 专题三：测量误差模型

### 来源例题 1：绝对误差

| 项目  | 内容                                 |
| --- | ---------------------------------- |
| 来源轴 | G-06, G-07                         |
| 题目  | 体重秤读数为 150 lb，真实值为 145 lb。测量误差是多少？ |
| 解答  | $150-145=5$ lb。若只问绝对误差，则为 5 lb。    |

### 来源例题 2：观察分数模型

| 项目 | 内容 |
|---|---|
| 来源轴 | G-08 |
| 题目 | 经典测验理论中，观察分数 82，误差分数 -3，则真实分数是多少？ |
| 解答 | $X=T+E$，所以 $T=X-E=82-(-3)=85$。 |

### 来源例题 3：相对误差

| 项目 | 内容 |
|---|---|
| 来源轴 | G-06 |
| 题目 | 测得长度 19.8 cm，真实长度 20.0 cm。相对误差是多少？ |
| 解答 | 误差 $=-0.2$ cm；相对误差 $|-0.2|/20.0=1\%$。 |

### 练习题

| 编号 | 题目 | 参考答案 |
|---|---|---|
| M-1 | 测得电压 4.92 V，标准值 5.00 V。带符号误差是多少？ | $4.92-5.00=-0.08$ V。 |
| M-2 | 观察分数为 76，真实分数估计为 80，误差分数是多少？ | $E=X-T=76-80=-4$。 |
| M-3 | 测得质量 50.6 g，真实质量 50.0 g。绝对误差和相对误差分别是多少？ | 绝对误差 0.6 g；相对误差 $0.6/50.0=1.2\%$。 |

---

## 专题四：MSA 测量系统分析

### 来源例题 1：Gauge R&R 判定

| 项目 | 内容 |
|---|---|
| 来源轴 | G-09, G-10, G-11 |
| 题目 | 某测量系统的 Gauge R&R 占总变差 8%。通常可否接受？ |
| 解答 | 通常小于 10% 可视为可接受；仍需结合客户要求和使用场景判断。 |

### 来源例题 2：重复性和再现性

| 项目 | 内容 |
|---|---|
| 来源轴 | G-10, G-11 |
| 题目 | 同一操作者用同一量具重复测同一零件，结果差异较大。主要检查重复性还是再现性？ |
| 解答 | 主要检查重复性。重复性对应同一操作者、同一量具、同一对象下的波动。 |

### 来源例题 3：分辨率不足

| 项目 | 内容 |
|---|---|
| 来源轴 | G-09, G-11 |
| 题目 | 产品公差为 ±0.10 mm，量具最小分辨率为 0.10 mm。问题在哪里？ |
| 解答 | 分辨率过粗，难以识别公差范围内的关键变化，测量系统可能不适合该任务。 |

### 练习题

| 编号 | 题目 | 参考答案 |
|---|---|---|
| A-1 | Gauge R&R 为 28%，应直接判定优秀吗？ | 不能。通常 10%-30% 属于需结合用途判断，28% 接近临界。 |
| A-2 | 三名操作者测同一批零件，操作者之间均值差异明显。主要反映重复性还是再现性？ | 再现性。 |
| A-3 | 一个量具每次测同一零件都很接近，但相对标准件总低 0.05 mm。MSA 中重点看什么？ | 偏倚。 |

---

## 专题五：测量不确定度评定

### 来源例题 1：Type A 与 Type B

| 项目 | 内容 |
|---|---|
| 来源轴 | G-13, G-15 |
| 题目 | 通过 20 次重复测量估计重复性不确定度，属于 Type A 还是 Type B？ |
| 解答 | Type A，因为它由统计分析重复测量数据得到。 |

### 来源例题 2：卡尺测螺栓

| 项目 | 内容 |
|---|---|
| 来源轴 | G-15 |
| 题目 | 用卡尺测螺栓长度，不确定度来源至少包括哪些？ |
| 解答 | 可包括重复性、分辨率、校准证书给出的不确定度、温度影响和操作者读数。 |

### 来源例题 3：NIST 的复杂实例

| 项目 | 内容 |
|---|---|
| 来源轴 | G-12, G-14 |
| 题目 | NIST 示例中，为什么玻璃棱镜折射率、砷含量、放射性测绘等都属于不确定度问题？ |
| 解答 | 它们都需要把测量模型、数据波动和其他已知信息合成到结果的不确定度表达中。 |

### 练习题

| 编号 | 题目 | 参考答案 |
|---|---|---|
| U-1 | 校准证书给出标准器不确定度，这通常按 Type A 还是 Type B 使用？ | Type B，因为来自外部资料或证书信息。 |
| U-2 | 重复测量均值为 100.0，合成标准不确定度 $u_c=0.4$，取 $k=2$，扩展不确定度是多少？ | $U=ku_c=0.8$。结果可写为 $100.0 \pm 0.8$。 |
| U-3 | 为什么不确定度评定不能只看仪器分辨率？ | 因为还可能包含重复性、校准、环境、方法、人员和样品等分量。 |

## P0 最后检查

| 检查项 | 结果 |
|---|---|
| 每专题来源例题 | 5 个专题，每个 3 道 |
| 每专题练习题 | 5 个专题，每个 3 道 |
| 是否混入知乎词条外的新专题 | 否，仅沿用原 5 个专题 |
| 是否保留可反查来源 | 是，使用 G-01 至 G-15 来源轴 |
