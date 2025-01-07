```
import torch import torch.nn.functional as F # 示例标签 
labels = torch.tensor([0, 1, 2, 3]) 
# 假设有4个类别 
# 假设类别总数 
num_classes = 4 
# 使用 one_hot 函数进行 One-Hot 编码 
one_hot_encoded = F.one_hot(labels, num_classes=num_classes) print(one_hot_encoded)
```

将数字向量变成one_hot