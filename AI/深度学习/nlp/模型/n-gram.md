# 什么是 N-Gram

N-Gram 是自然语言处理（NLP）和文本分析中的一种模型，用于将文本序列分解成连续的子序列。这些子序列称为n-gram，其中 n 表示组中单词或字符的数量。根据n的值，n-gram可以分为：

- <span style="font-weight:bold; color:rgb(0, 176, 240)">unigram（1-gram）</span>: 每个单独的词
- <span style="font-weight:bold; color:rgb(0, 176, 240)">bigram（2-gram）</span>: 每两个连续的词
- <span style="font-weight:bold; color:rgb(0, 176, 240)">trigram（3-gram）</span>: 每三个连续的词
- <span style="font-weight:bold; color:rgb(0, 176, 240)">n-gram</span>： 一般化的术语，用于描述任意数量的连续词或字符

# 计算

让我们从计算 `P(w|h)` 的任务开始，即给定一些历史 `h` 的单词 `w` 的概率。假设历史` h` 是 `The water of Walden Pond is so beautiful `，我们想知道下一个单词是`blue`的概率`P(blue|The water of Walden Pond is so beautiful)`：
$$
\frac{C(The\ water\ of\ Walden\ Pond\ is\ so\ beautiful\ blue)}{C(The\ water\ of\ Walden\ Pond\ is\ so\ beautiful)}
$$
这其实就是计算句子`The water of Walden Pond is so beautiful`跟随着单词`blue`的概率。
如果我们有一个足够大的语料库，我们可以计算这两个句子的数量并从方程中估计概率。但即使是整个网络也不够大，无法为我们提供整个句子计数的良好估计。这是因为语言是创造性的，新句子一直在被发明出来，我们不能指望获得像整个句子这样的大对象的准确计数。出于这个原因，我们需要更聪明的方法来估计给定历史 `h` 的单词 `w `的概率，或者整个单词序列` W `的概率。