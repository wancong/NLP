# pyhanlp

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
For the most part, inner classes can be used like normal classesm, with thw following differences :  
Inner classes in java natively use $ to separate the outer class from the inner class. For example, inner class Foo defined inside class Bar is called Bar.Foo in java, but its real native name is Bar$Foo.
Because of this name mangling, you cannot use the standard package access method to get them. Use the method` __getclass__` in the JPackage to load them.
Non-static inner classes cannot be instantiated from Python code. Instances received from Java code thay can be used without problem.


