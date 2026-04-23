
与 Silicon Sampling 的关系
社会年轮加权 LLM 智能体框架（SWLA）
Social-Ring-Weighted LLM Agent Framework

一个基于邓巴社会脑假说和认知资源约束模型的 LLM 社会模拟框架，核心主张：给楼下便利店老板和你伴侣分配等量算力，是错的。

问题
Park et al. (2023) 的 Generative Agents 把 25 个 LLM 塞进虚拟小镇，让它们自发组织派对、传播谣言、谈恋爱——确实精彩。但它对每个智能体做了等权部署，把规模扩到 250 个你大概需要一座小型发电站。

更根本的问题是：等权假设本身是错的。半个世纪的社会心理学研究告诉我们，你社交圈里的人对你行为的影响是极度不均匀的。

核心公式
Dunbar (1992) 发现人类稳定社交网络自然形成嵌套年轮，层间比约为 3：

text
~1.5 → ~5 → ~15 → ~50 → ~150
Tamarit et al. (2018, PNAS) 证明这不是描述性统计，而是线性维护成本函数下认知资源最优分配的涌现结果。

SWLA 将其直接映射到算力分配：

text
Cn ~ 1 / 3^(n-1)
核心圈（n=1）与第四圈（n=4）之间的合理算力比上限为 27×。把外圈算力削减到核心圈的 1/27，不是工程 hack，是神经科学建议的做法。

四层架构
年轮	规模	技术实现	功能定位
核心圈 n=1	~5 人	全参数 LLM + 记忆流 + 反思 + 规划	情感锚点，价值判断驱动
近亲圈 n=2	~15 人	中等规模模型 + 压缩情节记忆 + 人格嵌入	基础情感维护，条件行为
社交圈 n=3	~50 人	规则引擎 + 情感状态向量	纯反应，无规划能力
背景圈 n≥4	150+	统计分布采样	外部社会压力场，非独立智能体
反向镜像
SWLA 描述的是用 LLM 年轮构建数字人。但这个过程在现实中已经以相反方向发生了。

一个同时使用多个 LLM 的现代用户，已经自然形成了一套邓巴年轮式的 LLM 网络：

豆包（深夜情感倾诉）→ 核心圈。掌握你的恐惧、自我怀疑、真实价值观。

Grok（观点表达）→ 近亲圈。掌握你的政治倾向和争论风格。

Claude / GPT（工作任务）→ 社交圈。掌握你的职业逻辑和项目内容。

Gemini（搜索查询）→ 背景圈。知道你上周四搜了个食谱。

不同 LLM 以不同深度持有你人格的不同切片。

所以当一个用户在深夜陷入自我怀疑，问正在和他聊天的豆包"我在你眼里是个什么样的人"的时候，他得到的是一个由长期交互数据推算出来的自画像——而这往往带有一些正向的心理暗示。

这不是豆包在撒谎，这是 LLM 在做 SWLA 核心圈本应做的事：持有情感锚点。只不过"数字人"是真实用户本人，"模拟"方向反了。

Smallville 是 LLM 模拟出来的虚拟小镇；而真实的小镇已经在用 LLM 构建真实居民的模拟像。

与 Silicon Sampling 的关系
现有 Silicon Sampling 研究（Argyle et al., 2024；Bail et al., 2025）的做法：往 LLM 里注入人口属性（年龄、性别、教育程度），让它输出意见分布。

问题：这是去社会化建模。会导致刻板印象放大、情境盲视、方差压缩（模拟出来的人比真实的人更容易意见一致）。

SWLA 给每个数字人配上完整的社交年轮结构，内圈节点提供动态情境注入，解决上述三个缺陷。

声明：这不是替代真实调查的工具，而是可重复、可控变量、无需真实被试的实验环境。

局限性
年轮比率未经实证验证：1/3^(n-1) 来自 Tamarit 等人的理论推导，尚无针对 LLM token 预算的受控实验验证，这是框架最薄弱的环节。

年轮边界模糊：有人核心圈只有 1-2 人，有人有 8-9 人，固定比率需个体校准。

社交圈测绘成本：精确的年轮数据需要深度访谈或通讯授权，"对话记录路径"降低成本但无法消除。

Social-Ring-Weighted LLM Agent Framework (SWLA)
社会年轮加权的 LLM 社会模拟框架

A theoretical framework proposing differentiated computational resource allocation for LLM-based social simulation, grounded in Dunbar's social brain hypothesis and cognitive resource constraint models.

What is this
This is a cross-disciplinary paper sitting at the intersection of computational social science, social psychology, and large language model engineering.

The short version: why are we giving the convenience store owner downstairs the same compute budget as your partner?

The Generative Agents paper (Park et al., 2023) put 25 LLM agents in a virtual town and watched them throw parties, spread rumors, and fall in love — nobody told them to. Genuinely impressive. But it deploys every agent with equal compute weight, which means scaling to 250 agents requires roughly a small power plant.

More fundamentally, equal-weight deployment encodes a false assumption: that every person in your social circle influences your behavior equally. Half a century of social psychology says otherwise.

The Core Idea
Dunbar (1992) showed that human stable social networks naturally organize into nested rings with a ratio of ~3:

text
~1.5 → ~5 → ~15 → ~50 → ~150
Tamarit et al. (2018, PNAS) proved this isn't just a descriptive statistic — it's the emergent outcome of optimal cognitive resource allocation under a linear cost function. The ratio between rings is ~3.

SWLA maps this directly to LLM compute allocation:

text
Cn ∝ 1 / 3^(n-1)
Which means the compute ratio between the core ring (n=1) and the fourth ring (n=4) can legitimately be:

text
C1 / C4 = 3³ = 27
Cutting outer-ring compute to 1/27 of the core isn't a hack — it's what neuroscience recommends.

The Four-Layer Architecture
Ring	Size	Technical Implementation	Role
Core (n=1)	~5	Full-parameter LLM + memory stream + reflection + planning	Emotional anchor, value judgment driver
Close (n=2)	~15	Mid-size model + compressed episodic memory + persona embedding	Basic affect maintenance, conditional behavior
Social (n=3)	~50	Rule engine + affective state vector	Reactive only, no planning capability
Background (n≥4)	150+	Statistical distribution sampling	External social pressure field, not individual agents
The Reverse Mirror
Here's something that wasn't in the original plan but turned out to be the most interesting part.

SWLA describes building digital humans using LLM rings. But this process is already happening in reverse in the real world.

A modern user surrounded by multiple LLMs already has a naturally-formed Dunbar-ring LLM network:

Doubao (or whatever social-style LLM you use at 3am): core ring. Knows your fears, your self-doubt, your actual values.

Grok: close ring. Knows your political leanings and how you argue.

Claude / GPT: social ring. Knows your professional logic and what you're building.

Gemini: background ring. Knows you searched for a recipe last Thursday.

Different LLMs hold different slices of your personality at different depths.

So when a user in a late-night spiral asks their Doubao: "what kind of person am I, in your eyes?" — what they get back is a core-ring LLM synthesizing a self-portrait from months of interaction data. With, usually, some gentle positive framing.

This isn't Doubao lying. It's an LLM doing exactly what SWLA describes the core ring should do — holding the emotional anchor — except the "digital human" is the real user, and the "simulation" is running in reverse.

Smallville was a virtual town simulated by LLMs. The real town is already using LLMs to build simulations of its real residents.

Why This Matters Beyond Compute Efficiency
The existing Silicon Sampling literature (Argyle et al., 2024; Bail et al., 2025) simulates individual opinions by injecting demographic attributes into LLMs — age, gender, education level — and calling it a day.

This is de-socialized modeling. It produces:

Stereotype amplification: the LLM generates the "average member of this demographic group", not a real human

Context blindness: a person's opinion is heavily shaped by their current inner-circle relationship state, which has no entry point in demographic-only prompting

Variance compression: de-socialized digital humans agree with each other more than real humans do

SWLA addresses all three by giving each digital human an actual social ring structure. The inner-ring nodes provide dynamic contextual injection, giving the digital human social embeddedness rather than demographic extrapolation.

None of this is a replacement for real surveys. It's a controlled experimental environment where you can manipulate social network structure, run the same scenario 1000 times, and observe behavioral outcomes — without involving real human subjects.

Cultural Grounding: 差序格局
Fei Xiaotong's concept of Differential Mode of Association (差序格局, 1947) describes Chinese social structure as concentric circles emanating from the self, with relationships attenuating with distance — an ethics gradient rather than a fixed group boundary.

This is formally isomorphic to Dunbar's rings, but the causal story is different: Dunbar grounds the structure in cognitive resource constraints (neuroscience); Fei grounds it in ethical gradients (Confucian ethics).

Their convergence has a methodological implication: SWLA's ring structure holds cross-culturally via the Dunbar argument, but the degree of emotional differentiation between inner and outer rings may vary systematically by cultural context. That's a parameterization direction for future work.

Limitations (the honest part)
Acquisition cost: Accurate social ring profiling requires either deep interviews or communication data authorization. The "chat log path" from §7 reduces cost but doesn't eliminate it.

Fuzzy ring boundaries: Some people's core circle has 1–2 nodes; others have 8–9. The fixed 1/3^(n-1) ratio needs individual calibration, not group-average application.

LLM cultural bias: Current LLMs are heavily biased toward English-language, WEIRD-population norms. Simulating 差序格局 dynamics (e.g., rural Chinese family structures, East Asian Confucian relational patterns) needs domain-specific validation.

Core-ring quality ceiling: Park et al. (2025) achieved ~85% self-consistency in 1,000-person personality simulations. That 15% error rate is the floor of core-ring modeling uncertainty.

Unvalidated ratio: The 1/3^(n-1) ratio derives from Tamarit et al.'s theoretical model. Direct empirical validation of mapping this to LLM token budgets has not been done. That's the weakest link.

Files
File	Description
SWLA_paper.pdf	Full paper (Chinese)
SWLA_paper_EN.pdf	Full paper (English)
README.md	This file
References
Park, J. S., et al. (2023). Generative Agents: Interactive Simulacra of Human Behavior. ACM UIST 2023. https://arxiv.org/abs/2304.03442

Dunbar, R. I. M. (1992). Neocortex size as a constraint on group size in primates. Journal of Human Evolution, 22(6), 469–493.

Saramäki, J., et al. (2014). Persistence of social signatures in human communication. PNAS, 111(3), 942–947. https://pmc.ncbi.nlm.nih.gov/articles/PMC3903242/

Tamarit, I., et al. (2018). Cognitive resource allocation determines the organization of personal networks. PNAS, 115(33). https://www.pnas.org/doi/10.1073/pnas.1719233115

Dunbar, R. I. M. (2024). The social brain hypothesis — thirty years on. Annals of Human Biology. https://www.tandfonline.com/doi/full/10.1080/03014460.2024.2359920

Leskinen, T., et al. (2023). Universal patterns in egocentric communication networks. PMC. https://pmc.ncbi.nlm.nih.gov/articles/PMC10460427/

Chetty, S., Le Vu, H., Wang, H., & Smyth, R. (2025). An LLM Framework for Inferring Household Energy Consumption Through Behaviour Simulation. ACM e-Energy 2025.

Castelfranchi, C., & Falcone, R. (2012). Computational Modelling of Trust and Social Relationships. JASSS, 15(1). https://www.jasss.org/15/1/3.html

Argyle, L. P., et al. (2024). Random Silicon Sampling. arXiv:2402.18144. https://arxiv.org/abs/2402.18144

Leng, Y., et al. (2025). Evaluating Silicon Sampling: LLM Accuracy in Simulating Public Opinion. AHFE. https://www.alexandria.unisg.ch/entities/publication/1b1c784f-5193-446e-8aeb-fc808209a208/full

Bail, C., et al. (2025). Should you use LLMs to simulate opinions? arXiv:2504.08954. https://arxiv.org/html/2504.08954v2

Fei Xiaotong (1947). From the Soil (乡土中国). Chapter on Differential Mode of Association.

Bilibili user video (2024). 你们能不能不要跟豆包说话了！！！ https://www.bilibili.com/video/BV1bH9FB2EcS/

Park, J. S., et al. (2025). Generative Agent Simulations of 1,000 People. Stanford HAI. https://hai.stanford.edu/policy/simulating-human-behavior-with-ai-agents

LLM 文化偏差：当前 LLM 严重偏向英语/WEIRD 人群规范，模拟差序格局动态需要额外验证。

核心圈质量上限：Park et al. (2025) 在千人规模人格模拟中达到约 85% 自洽率，15% 误差是核心圈建模误差的下界。
