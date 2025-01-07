```
import torch
import torch.nn as nn

# 假设我们的词汇表大小为 5，嵌入维度为 3
vocab_size = 5
embedding_dim = 3

# 创建嵌入层
embedding = nn.Embedding(num_embeddings=vocab_size, embedding_dim=embedding_dim)

# 示例输入（单词的索引）
input_indices = torch.tensor([0, 1, 2, 3, 4])  # 假设有 5 个单词

# 获取嵌入表示
embedded_output = embedding(input_indices)

print("Embedded Output:\n", embedded_output)

```

将索引映射成词向量