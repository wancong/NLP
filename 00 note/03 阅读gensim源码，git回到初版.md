# 阅读gensim源码
---
## 回到初版
1. git log --pretty=oneline 查看历史
2. git reset hard  7dfc5ce04437298d4aa3f69ef7cd6e033d7feaf8 回到最初
3. 很快（不到1秒），回到最初，67M。 小了很多。

gemsim.py
---
初版代码感觉完全没压力，首次提交时间：Mon Aug 31 21:30:33 2009  
主要实现了3个算法tidif, lsi, rp
<pre>
METHOD is currently either tfidf, lsi or rp.  
Example: ./gensim.py tfidf eng  
</pre>

<pre>
# next, create a method matrix which will serve for cossim computations.
# different methods create different matrices, but all return a sparse matrix of the shape (numDocs x N)
if method == 'tfidf':
    mat = tfidf # do nothing -- for tfidf, we have got the matrix in the correct format already
elif method == 'lsi':
    mat = docsim.buildLSIMatrices(tfidf = tfidf, factors = 200)
elif method == 'rp':
    mat = docsim.buildRPMatrices(tfidf = tfidf, dimensions = 300)
else:
    assert False, "unknown method '%s'" % method
</pre>

## tfdif
term frequency–inverse document frequency  

tf = 词j出现次数 / 总的词数
idf = log(文档总数 / 包含词j的文档数)

文件build_tfidf, 先于gensim.py执行，tfidf矩作为gensim.p的输出

追踪调用流程：  
build_tfdif -> docsim.buildTFIDFMatrices -> 
DocumentCollection.DocumentCollection.getTFIDFMatrix  

### tf:
1 ->utils_dml.vect2bow_sorted  
<pre>
def vect2bow_sorted(_ids):
    """Convert sequence of ids into (id->id_frequency) list, sorted by 'id' increasingly."""
	"""
	1 id(数字)排序
	2 统计id出现的次数
	"""
    if len(_ids) == 0:
        return []
    ids = sorted(_ids)  #排序 
    result = []
    last = ids[0]  #每次待统计id
    cnt = 0
    total = 0
    for id in ids:
        if last == id:
            cnt += 1
        else:
            result.append((last, cnt))
            total += cnt
            cnt = 1
            last = id
    total += cnt
    result.append((last, cnt))
    return result, total
</pre>
2 DocumentCollection.DocumentCollection.getTFIDFMatrix  
itotal = 1.0 / total
result.data[id].append(itotal * idfreq) #idfreq是词i的统计次数,词名称是数字化的id

### idf
<pre>
for i in xrange(len(docs)):
	...
	# nnz包含词j的文件数目
	nnz = numpy.array([len(result.data[j]) for j in xrange(result.shape[0])])
	# log(文件总数/包含词j的文件数) / log(2)
	idfs = numpy.log((1.0 * result.shape[1]) / nnz) / numpy.log(2)
</pre>

### tf * idf
<pre>
result.data[iterm] = [val * idfs[iterm] for val in result.data[iterm]]
</pre>
