# 什么是 N-Gram

N-Gram 是自然语言处理（NLP）和文本分析中的一种模型，用于将文本序列分解成连续的子序列。这些子序列称为n-gram，其中 n 表示组中单词或字符的数量。根据n的值，n-gram可以分为：

- <span style="font-weight:bold; color:rgb(0, 176, 240)">unigram（1-gram）</span>: 每个单独的词
- <span style="font-weight:bold; color:rgb(0, 176, 240)">bigram（2-gram）</span>: 每两个连续的词
- <span style="font-weight:bold; color:rgb(0, 176, 240)">trigram（3-gram）</span>: 每三个连续的词
- <span style="font-weight:bold; color:rgb(0, 176, 240)">n-gram</span>： 一般化的术语，用于描述任意数量的连续词或字符

# N-gram

让我们从计算 `P(w|h)` 的任务开始，即给定一些历史 `h` 的单词 `w` 的概率。假设历史` h` 是 `The water of Walden Pond is so beautiful `，我们想知道下一个单词是`blue`的概率`P(blue|The water of Walden Pond is so beautiful)`：

$$
\frac{C(The\ water\ of\ Walden\ Pond\ is\ so\ beautiful\ blue)}{C(The\ water\ of\ Walden\ Pond\ is\ so\ beautiful)}\tag{1.1}
$$

这其实就是计算句子`The water of Walden Pond is so beautiful`跟随着单词`blue`的概率。
如果我们有一个足够大的语料库，我们可以计算这两个句子的数量并从方程中估计概率。但即使是整个网络也不够大，无法为我们提供整个句子计数的良好估计。这是因为语言是创造性的，新句子一直在被发明出来，我们不能指望获得像整个句子这样的大对象的准确计数。出于这个原因，我们需要更聪明的方法来估计给定历史 `h` 的单词 `w `的概率，或者整个单词序列` W `的概率。
然后我们来使用概率的链式来表示某个单词的序列。
其中$X_{1:n}$表示X1到Xn的单词，所以句子的概率如下：

$$
\begin{equation}\begin{split}
P(W_{1:n})&=P(W_1)P(W_2|W_1)P(W3|W_{1:2})...P(W_n|W_{1:n}) \\
&=\prod_{k=1}^nP(W_k|W_{1:k-1}) 
\end{split}\tag{1.2}\end{equation}
$$

等式 1.2 表明，我们可以通过将多个条件概率相乘来估计整个单词序列的联合概率。但是使用链式法则似乎并没有真正帮助我们！我们不知道任何方法可以计算给定一长串前词$P(W_n|W_{1:n-1})$ 的确切概率。正如上面所说，我们不能仅仅通过计算某个语料库中每个长字符串后面每个单词出现的次数来估计，因为语言是创造性的，任何特定的上下文都可能以前从未出现过！

## 2.1马尔可夫假设
n-gram 模型的直觉是，我们可以只通过最后几个单词来近似历史，而不是计算给定一个单词的整个历史的概率。<span style="font-weight:bold; color:rgb(0, 176, 240)">bigram（2-gram）</span>仅使用前一个词 $P(W_n|W_{n-1})$ 的条件概率来近似$P(W_n|W_{1:n-1})$的概率。换句话说，不是计算概率:
$$
P(blue|The\ water\ of\ Walden\ Pond\ is\ so\ beautiful)\tag{2.1}
$$
而是通过概率：
$$
P(blue|beautiful)\tag{2.2}
$$
近似替代。
一个词的概率仅取决于前一个词的假设称为`马尔可夫假设`。马尔可夫模型是一类概率模型，它假设我们可以预测某个未来单位的概率，而无需太深入地研究过去。我们可以将二元语法（将一个单词回顾过去）推广到三元语法（将两个单词回顾过去），从而推广到 `n-gram`（将 `n-1` 个单词回顾过去）

对于 MLE `n-gram` 参数估计的一般情况：

$$
P(W_n|W_{n-N+1:n-1})=\frac{C(W_{n-N+1:n})}{C(W_{n-N+1:n-1})}\tag{2.3}
$$
# 对数概率
当小概率时间累乘，值就会变得极小，这种时候就有切换表示模式的需求。语言模型概率始终作为对数概率在对数空间中存储和计算。这是因为概率（根据定义）小于或等于 1，因此我们乘以的概率越多，乘积就越小。将足够多的 n-gram 相乘将导致数值下溢。在对数空间中相加等效于在线性空间中相乘，因此我们通过相加来组合对数概率。通过添加对数概率而不是乘以概率，我们得到的结果并不小。我们在对数空间中进行所有计算和存储，如果我们需要在最后通过获取概率的 exp 来报告概率，只需转换回概率：

$$
P_1*P_2*P_3*P_4=\exp(In(P_1)+In(P_2)+In(P_3)+In(P_4))
$$