# 社会年轮加权 LLM 智能体框架（SWLA）

**Social-Ring-Weighted LLM Agent Framework**

> 一个基于邓巴社会脑假说和认知资源约束模型的 LLM 社会模拟框架，核心主张：给楼下便利店老板和你伴侣分配等量算力，是错的。

---

## 问题

[Park et al. (2023)](https://arxiv.org/abs/2304.03442) 的 Generative Agents 把 25 个 LLM 塞进虚拟小镇，让它们自发组织派对、传播谣言、谈恋爱——确实精彩。但它对每个智能体做了等权部署，把规模扩到 250 个你大概需要一座小型发电站。

更根本的问题是：等权假设本身是错的。半个世纪的社会心理学研究告诉我们，你社交圈里的人对你行为的影响是极度不均匀的。

---

## 核心公式

[Dunbar (1992)](https://doi.org/10.1016/0047-2484(92)90081-J) 发现人类稳定社交网络自然形成嵌套年轮，层间比约为 3：

```
~1.5 → ~5 → ~15 → ~50 → ~150
```

[Tamarit et al. (2018, PNAS)](https://www.pnas.org/doi/10.1073/pnas.1719233115) 证明这不是描述性统计，而是线性维护成本函数下认知资源最优分配的涌现结果。

SWLA 将其直接映射到算力分配：

```
Cn ~ 1 / 3^(n-1)
```

核心圈（n=1）与第四圈（n=4）之间的合理算力比上限为 **27×**。把外圈算力削减到核心圈的 1/27，不是工程 hack，是神经科学建议的做法。

---

## 四层架构

| 年轮 | 规模 | 技术实现 | 功能定位 |
|------|------|----------|----------|
| 核心圈 n=1 | ~5 人 | 全参数 LLM + 记忆流 + 反思 + 规划 | 情感锚点，价值判断驱动 |
| 近亲圈 n=2 | ~15 人 | 中等规模模型 + 压缩情节记忆 + 人格嵌入 | 基础情感维护，条件行为 |
| 社交圈 n=3 | ~50 人 | 规则引擎 + 情感状态向量 | 纯反应，无规划能力 |
| 背景圈 n≥4 | 150+ | 统计分布采样 | 外部社会压力场，非独立智能体 |

---

## 反向镜像

SWLA 描述的是用 LLM 年轮构建数字人。但这个过程在现实中已经以相反方向发生了。

一个同时使用多个 LLM 的现代用户，已经自然形成了一套邓巴年轮式的 LLM 网络：

- **豆包**（深夜情感倾诉）→ 核心圈。掌握你的恐惧、自我怀疑、真实价值观。
- **Grok**（观点表达）→ 近亲圈。掌握你的政治倾向和争论风格。
- **Claude / GPT**（工作任务）→ 社交圈。掌握你的职业逻辑和项目内容。
- **Gemini**（搜索查询）→ 背景圈。知道你上周四搜了个食谱。

不同 LLM 以不同深度持有你人格的不同切片。

所以当一个用户在深夜陷入自我怀疑，问正在和他聊天的豆包"我在你眼里是个什么样的人"的时候，他得到的是一个由长期交互数据推算出来的自画像——而这往往带有一些正向的心理暗示。

这不是豆包在撒谎，这是 LLM 在做 SWLA 核心圈本应做的事：持有情感锚点。只不过"数字人"是真实用户本人，"模拟"方向反了。

**Smallville 是 LLM 模拟出来的虚拟小镇；而真实的小镇已经在用 LLM 构建真实居民的模拟像。**

---

## 与 Silicon Sampling 的关系

现有 Silicon Sampling 研究（[Argyle et al., 2024](https://arxiv.org/abs/2402.18144)；[Bail et al., 2025](https://arxiv.org/html/2504.08954v2)）的做法：往 LLM 里注入人口属性（年龄、性别、教育程度），让它输出意见分布。

问题：这是去社会化建模。会导致刻板印象放大、情境盲视、方差压缩（模拟出来的人比真实的人更容易意见一致）。

SWLA 给每个数字人配上完整的社交年轮结构，内圈节点提供动态情境注入，解决上述三个缺陷。

**声明：这不是替代真实调查的工具，而是可重复、可控变量、无需真实被试的实验环境。**

---

## 局限性

1. **年轮比率未经实证验证**：1/3^(n-1) 来自 Tamarit 等人的理论推导，尚无针对 LLM token 预算的受控实验验证，这是框架最薄弱的环节。
2. **年轮边界模糊**：有人核心圈只有 1-2 人，有人有 8-9 人，固定比率需个体校准。
3. **社交圈测绘成本**：精确的年轮数据需要深度访谈或通讯授权，"对话记录路径"降低成本但无法消除。
4. **LLM 文化偏差**：当前 LLM 严重偏向英语/WEIRD 人群规范，模拟差序格局动态需要额外验证。
5. **核心圈质量上限**：Park et al. (2025) 在千人规模人格模拟中达到约 85% 自洽率，15% 误差是核心圈建模误差的下界。

---

## 文件

| 文件 | 说明 |
|------|------|
| `SWLA_paper.pdf` | 完整论文（中文） |
| `SWLA_paper_EN.pdf` | 完整论文（英文） |
| `README.md` | 英文说明 |
| `README_CN.md` | 本文件 |

---

## 参考文献

1. Park et al. (2023). Generative Agents. *ACM UIST 2023*. https://arxiv.org/abs/2304.03442
2. Dunbar, R. I. M. (1992). Neocortex size as a constraint on group size in primates. *Journal of Human Evolution*.
3. Tamarit et al. (2018). Cognitive resource allocation determines the organization of personal networks. *PNAS*. https://www.pnas.org/doi/10.1073/pnas.1719233115
4. Saramäki et al. (2014). Persistence of social signatures in human communication. *PNAS*. https://pmc.ncbi.nlm.nih.gov/articles/PMC3903242/
5. Argyle et al. (2024). Random Silicon Sampling. *arXiv:2402.18144*. https://arxiv.org/abs/2402.18144
6. Bail et al. (2025). Should you use LLMs to simulate opinions? *arXiv:2504.08954*. https://arxiv.org/html/2504.08954v2
7. Park et al. (2025). Generative Agent Simulations of 1,000 People. *Stanford HAI*. https://hai.stanford.edu/policy/simulating-human-behavior-with-ai-agents
8. 费孝通（1947）.《乡土中国》差序格局章节.

---

*这是一篇理论提案。1/3^(n-1) 的比率来自认知科学建模，针对 LLM 模拟质量指标的受控实证验证尚未进行——那是显而易见的下一步。*
