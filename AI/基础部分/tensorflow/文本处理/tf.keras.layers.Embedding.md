```
import tensorflow as tf

# 假设我们的词汇表大小为 5，嵌入维度为 3
vocab_size = 5
embedding_dim = 3

# 创建嵌入层
embedding = tf.keras.layers.Embedding(input_dim=vocab_size, output_dim=embedding_dim)

# 示例输入（单词的索引）
input_indices = tf.constant([0, 1, 2, 3, 4])  # 假设有 5 个单词

# 获取嵌入表示
embedded_output = embedding(input_indices)

print("Embedded Output:\n", embedded_output.numpy())  # 使用 .numpy() 将 tensor 转换为 numpy 数组

```
将索引映射成词向量