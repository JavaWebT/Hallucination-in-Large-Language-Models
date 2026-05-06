# Hallucination-in-Large-Language-Models
大语言模型的幻觉
<img width="913" height="855" alt="image" src="https://github.com/user-attachments/assets/43b549c8-aaf1-46df-b4b7-5ccbd255e691" />
### 幻觉的分类
- 事实性幻觉
- 忠实性幻觉
- <img width="1080" height="402" alt="image" src="https://github.com/user-attachments/assets/7425645f-a574-45ec-89a7-ff8f17ef3bbd" />
### 出现幻觉的原因
- 数据缺陷： 数据质量低，过拟合；
- 训练缺陷
   - 预训练阶段：
     - 架构缺陷: 单向建模，上下文提取能力弱；自注意力，随着token长度增加，导致注意力稀释。
     - 暴露偏差：后面的token依赖前面生成的token,若前面的有错，则会出现级联错误。
   - 对齐阶段
     - 能力错位: LLM的内部能力与其被训练的标注信息不对应，出现知识边界，而产生幻觉。
     - 信念错位：基于人类反馈强化学习RLHF微调，导致LLMs预测会偏向人类的喜好，忽视事实性。
### 检测大模型病症
- 事实性幻觉
  - 检索外部事件： 预测结果与可靠的事实进行对比
  - 不确定性估计
    - 基于模型内部状态：主要依赖于访问大模型的内部状态。例如，通过考虑关键概念的最小标记概率来确定模型的不确定性。
    - 基于响应：则主要依赖于观察大模型的行为，不需要访问其内部状态。例如，通过采样多个响应并评估事实陈述的一致性来检测幻觉。
- 忠实性幻觉
  - 基于事实的度量，测量生成内容和源内容之间事实的重叠程度来评估忠实性。
  - 分类器度量：使用训练过的分类器来区分模型生成的忠实内容和幻觉内容。
  - 问答度量：使用问答系统来验证源内容和生成内容之间的信息一致性。
  - 不确定度估计：测量模型对其生成输出的置信度来评估忠实性。
  - 提示度量：让大模型作为评估者，通过特定的提示策略来评估生成内容的忠实性。
  <img width="1080" height="624" alt="image" src="https://github.com/user-attachments/assets/06dd129d-6b4f-4749-919b-e97c16012bdc" />
### 缓解幻觉的影响的方法
- 数据相关的幻觉
  - 高质量数据
  - 知识边界：
    - 知识编辑
    - RAG（检索增强生成）
    - 检索增强具体分为三种类型：一次性检索、迭代检索和事后检索。
      - 一次性检索是将从单次检索中获得的外部知识直接预置到大模型的提示中；
      - 迭代检索允许在整个生成过程中不断收集知识；
      - 事后检索是基于检索的修订来完善大模型输出。
      - <img width="1080" height="558" alt="image" src="https://github.com/user-attachments/assets/3186a4e5-eedf-40b2-ae02-e9ebd9bd194a" />
- 训练相关的幻觉
  - 过完善预训练策略
  - 确保更丰富的上下文理解
  - 和规避偏见来应对
- 推理相关的幻觉
  - 事实性增强解码
  - 忠实性增强解码
    - 上下文一致性
    - 逻辑一致性
### Reference:
- HuaWei and Harbin Institute of Technology :Survey on Hallucination in Large Language Models:Principles, Taxonomy, Challenges, and Open Questions














- IBM_Blogs：https://community.ibm.com/community/user/blogs/anjaly-radhakrishnan/2026/03/23/when-ai-sounds-right-but-is-wrong-understanding
- Tencent_Article：https://cloud.tencent.com/developer/article/2662129?policyId=1004
