# 基于机器学习与遗传算法的镍基高温合金多目标设计与性能预测

本项目采用数据驱动的方法（材料信息学 / Materials Informatics），构建了面向**镍基高温合金（Ni-based Superalloys）**的全流程机器学习研究与设计体系。项目涵盖**数据相关性分析、微观特征描述符提取、多回归/分类模型构建与LOOCV留一交叉验证、以及基于改进遗传算法（GA）的新合金成分与热处理工艺反向设计**。

## 🛠️ 主要模块与文件说明

仓库内主要文件按功能划分为以下模块：

### 1. 数据集 (Datasets)
* `High-Temperature Alloy Dataset.xlsx`：高温合金基础成分与综合力学性能数据集。
* `镍基高温合金微观数据集.xlsx` / `weiguan.xlsx`：合金微观结构、强化相尺寸与分布特征数据集。
* `micro_descriptors_*.xlsx`：各主量元素（Al, Co, Cr, Mo, Nb, Ni, Ti, W 等）及对应性能（UTS, TYS, Elong）的微观特征描述符衍生数据。
* `皮尔逊分析.xlsx`：成分、特征与目标性能之间的 Pearson 相关系数结果。

### 2. 特征分析与微观建模 (Analysis & Feature Modeling)
* `成分相关性分析.ipynb`：特征间相关性热图与特征筛选分析。
* `成分-强化相分析.ipynb`：化学成分对强化相（γ' 相）演变影响的关联规律挖掘。
* `新成分微观特征模型预测.ipynb`：由成分反向预测微观组织演化的代理模型。

### 3. 性能预测模型对比 (Performance Prediction - UTS & Elongation)
针对**抗拉强度（UTS）**与**延伸率（EL）**，系统对比了主流机器学习模型在低数据样本下的表现：
* **模型实现代码**：
  * `抗拉强度--[BPNN/随机森林/支持向量机/高斯回归/集成回归/决策树].ipynb`
  * `延伸率--[BPNN/随机森林/支持向量机/GPR/集成回归/决策树].ipynb`
  * `XGB模型预测.ipynb` / `MLP模型预测.ipynb` / `KNN模型预测.ipynb`
* **模型评估与交叉验证**：
  * `final_output_LOOCV_*.xlsx`：留一交叉验证（Leave-One-Out Cross-Validation）预测结果与误差对比。
  * `final_output_seed*.xlsx`：不同随机数种子（Random Seeds）下的模型收敛与稳定性测试记录。

### 4. 分类与综合评价 (Classification & Evaluation)
* `分类模型预测评价.ipynb` & `可视化分类模型图.ipynb`：高性能区间合金的分类边界决策树与多维分类图示。
* `classification_results_*.xlsx`：分类指标对比表（Precision, Recall, F1-Score, AUC）。

### 5. 新合金成分与热处理工艺设计 (Inverse Design & Optimization)
* `改进的遗传算法.ipynb` / `将遗传算法输出的数据存在表格.ipynb`：采用改进遗传算法进行多目标协同优化搜索最优合金成分。
* `FOR循环设计新合金.ipynb`：基于经验边界约束的网格遍历/循环迭代成分设计。
* `1#热处理工艺挑选.ipynb` / `2#热处理工艺挑选.ipynb` / `热处理设计.ipynb`：优化合金固溶与时效温度、时间等工艺参数。
* `挑选的新合金.xlsx` / `筛选结果.xlsx`：最终多目标优化筛选出的推荐候选合金列表。

---

## 💻 运行环境与依赖库

推荐使用 **Python 3.8+** 及 Jupyter Notebook 环境，主要依赖库包括：

```bash
pip install numpy pandas scikit-learn xgboost matplotlib seaborn openpyxl deap
# 如涉及神经网络深度学习模块:
pip install torch  # 或 tensorflow
## 📌 核心研究内容与架构
