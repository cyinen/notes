Chain of Thought论文、代码和资源【论文精读】_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1t8411e7Ug/?spm_id_from=333.1007.top_right_bar_window_history.content.click&vd_source=facb259fe9a6824a1fea1d9874ae8b9d)

-   zero-shot：输入问题，等待输出结果
-   CoT：输入问题并提示Let’s think step by step
-   Manual-CoT: 是一种few shot方法，所以构造了一些模板Q&A（模板A中也有Let’s think step by step），然后再给出问题并提示Let’s think step by step
-   Auto-CoT：采样多个问题，每个问题提示Let’s think step by step，让模型给出答案。然后拼接所有生成的Q&A并给出最终问题，并提示Let’s think step by step

# 为什么需要CoT?

问题可以分为两类：一类是容易回答的，没有太多逻辑推理的，比如：天气如何？面包几块钱？另一类是需要长链条的逻辑推理的问题：数学等。

当语言模型的规模指数级增大时，它解决常规问题的能力有了很大的提升，然而它解决逻辑推理的问题的能力却提升很小。而CoT就是帮助解决这样的问题，它的核心思想是：不要光给出答案，把推理过程也给出来。如下图所示，关键在于构造的prompt要包含推理过程：

![](https://i0.hdslb.com/bfs/note/eac4b6a666c6a5f0c922a916f053ac1cb06ac09b.png)

  

为什么延长推理过程就有效呢？这可能是因为语言模型token-by-token的特点。

标准的prompt可以被视为大模型能力的下限，如何提取大模型学到的知识的问题是一个难点，标准的prompt是一个很好的起点，但却绝不是终点。