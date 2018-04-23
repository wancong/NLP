# NLP

### 射雕英雄传的word2vec
##### 1 gb2312转utf-8，读入原文件时有少量gb2312读取失败，注意ignore
##### 2 jieba.analyse.extract_tags，获取主角
##### 3 ‘黄蓉道’等错误分词，手工校正
##### 4 手工统计高频词
##### 5 直接gensim.models.word2vec.LineSentence效果不好
##### 6 手工切分句子。原始材料行宽有限，错误的截断。
##### 7 一行行分词。测试了jieba和thulac
##### 8 gensim的使用
##### 9 测试tf-idf
##### 10 gensim的word2vec
##### 11 各种测试。原理很简单，代码很直白，但感觉效果很强大。‘成吉思汗’和‘铁木真’亲近度高达0.95

