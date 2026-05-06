# Hallucination-in-Large-Language-Models
大语言模型的幻觉
<img width="913" height="855" alt="image" src="https://github.com/user-attachments/assets/43b549c8-aaf1-46df-b4b7-5ccbd255e691" />
### 幻觉的分类
- 事实性幻觉
- 忠实性幻觉
- <img width="1080" height="402" alt="image" src="https://github.com/user-attachments/assets/7425645f-a574-45ec-89a7-ff8f17ef3bbd" />
### 出现幻觉的原因
- 数据缺陷，模型过度依赖数据中的某些模式，比如当河南和石家庄多次共现时，模型可能会将和石家庄作为河南的省会。
- 训练缺陷：
   - 预训练阶段：
     - 架构缺陷: 注意力稀释。
     - 暴露偏差：按序预测，后面的token以来前面的token,若前面的有错，则会出现级联效应。
   - 对齐阶段
     - 能力错位: 要求的LLM的能力与其被训练的标注信息不对应，出现知识边界，而产生错误信息。
     - 信念错位：基于人类反馈强化学习RLHF微调，导致LLMs预测会偏向人类的喜好，忽视事实性。
### 检测大模型病症
- 事实性幻觉
  - 检索外部事件： 预测结果与事实进行对比
  - 不确定性估计
    - 基于模型内部状态：通过模型对该内容预测的最低概率确定
    - 基于响应：通过多轮问答来确定
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















### Reference:
- HuaWei and Harbin Institute of Technology :Survey on Hallucination in Large Language Models:Principles, Taxonomy, Challenges, and Open Questions
- IBM_Blogs：https://community.ibm.com/community/user/blogs/anjaly-radhakrishnan/2026/03/23/when-ai-sounds-right-but-is-wrong-understanding
- Tencent_Article：https://cloud.tencent.com/developer/article/2662129?policyId=1004
