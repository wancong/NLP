# pyhanlp

## HanLP$Config

遇到问题：  
HanLP.Config报错，说没有该属性  

解决办法：
JClass('com.hankcs.hanlp.HanLP$Config').ShowTermNature = False  
参见main.py的line89

原因：    
内部class，而不是内部属性  
内部类是一个相对独立的实体，与外部类不是is-a关系  
内部类是一个编译时概念，编译后外部类及其内部类会生成两个独立的class文件：   OuterClass.class和OuterClass$InnerClass.class  

在HanLP的HanLP.java中  
public static final class Config()  //内部class  
public static List<Term> segment(String text)  //内部属性  

[参考Jpype](http://jpype.sourceforge.net/doc/user-guide/userguide.html#using)  
--5. Inner Classes    


## DemoCustomDictionary.java
// 首字哈希之后二分的trie树分词  
import com.hankcs.hanlp.dictionary.CustomDictionary;  
import com.hankcs.hanlp.dictionary.BaseSearcher;  

BaseSearcher searcher = CustomDictionary.getSearcher(text);  

import java.util.Map;
Map.Entry entry;


## python testmod
<pre>
testmod(... optionflags=doctest.NORMALIZE_WHITESPACE)
</pre>
Optional keyword arg "optionflags" or's together module constants,
<pre>
and defaults to 0.  This is new in 2.3.  Possible values (see the
docs for details):
    DONT_ACCEPT_TRUE_FOR_1
    DONT_ACCEPT_BLANKLINE
    NORMALIZE_WHITESPACE
    ELLIPSIS
    SKIP
    IGNORE_EXCEPTION_DETAIL
    REPORT_UDIFF
    REPORT_CDIFF
    REPORT_NDIFF
    REPORT_ONLY_FIRST_FAILURE
</pre>

<pre>
"blank lines": r"""
    Blank lines can be marked with <BLANKLINE>:
        >>> print('foo\n\nbar\n')
        foo
        <BLANKLINE>
        bar
        <BLANKLINE>
""",

"ellipsis": r"""
    If the ellipsis flag is used, then '...' can be used to
    elide substrings in the desired output:
        >>> print(list(range(1000))) #doctest: +ELLIPSIS
        [0, 1, 2, ..., 999]
""",

"whitespace normalization": r"""
    If the whitespace normalization flag is used, then
    differences in whitespace are ignored.
        >>> print(list(range(30))) #doctest: +NORMALIZE_WHITESPACE
        [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14,
         15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26,
         27, 28, 29]
""",
</pre>





