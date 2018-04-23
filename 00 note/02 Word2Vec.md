# Word2Vec
---
[paper](https://arxiv.org/pdf/1301.3781.pdf)
## CBOW  
#### Continuous Bag of Words
**核心思想**:  根据当前词局部，预测该词。  
**例如**： 例如前2个词+后2个词，映射预测当前词。映射层所有词公用，局部关注连续流动。  

## Skip-gram
#### Continuous Skip gram  
**核心思想**： 根据当前词预测前后的词。  
**例如**： 根据当前词预测前2个词和后2个词。  