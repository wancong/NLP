# Flask
The url_for() function generates the URL to a view based on a name and arguments. The name associated with a view is also called the endpoint

<pre>
{% block header %}{% endblock %}
</pre>
{% block title %} will change the title displayed in the browser’s tab and window title.  

{% extends 'base.html' %} tells Jinja that this template should replace the blocks from the base template.  

A useful pattern used here is to place {% block title %} inside {% block header %}. This will set the title block and then output the value of it into the header block, so that both the window and page share the same title without writing it twice.

# Make the Project Installable
<pre>
pip install -e .
</pre>
This tells pip to find setup.py in the current directory and install it in editable or development mode.  

The “micro” in microframework means Flask aims to keep the core simple but extensible.  

<pre>
flask.render_template(template_name_or_list, **context)
</pre>

# pyhanlp
<pre>
>>> HanLP.segment("我的目标是成为NLP专家")  
</pre> 
<jpype._jclass.java.util.ArrayList object at 0x7fdecbbde9e8>
<pre>
>>> (HanLP.segment("我的目标是成为NLP专家")).toString()
</pre>
'[我/rr, 的/ude1, 目标/n, 是/vshi, 成为/v, NLP/nx, 专家/nnt]'



Internal exceptions (2 events):  
Event: 0.054 Thread 0x00007fdb84046800 Exception <a 'java/lang/NoSuchMethodError': Method sun.misc.Unsafe.defineClass(Ljava/lang/String;[BII)Ljava/lang/Class; name or signature does not match> (0x00000000c0007ca0) thrown at [/build/openjdk-8-OdO8jS/openjdk-8-8u162-b12/src/hotspot/src/share/vm/  

Event: 0.054 Thread 0x00007fdb84046800 Exception <a 'java/lang/NoSuchMethodError': Method sun.misc.Unsafe.prefetchRead(Ljava/lang/Object;J)V name or signature does not match> (0x00000000c0007f88) thrown at [/build/openjdk-8-OdO8jS/openjdk-8-8u162-b12/src/hotspot/src/share/vm/prims/jni.cpp, lin  

**java_class_path (initial):** /home/wancong/projects/flask/examples/javascript/venv/lib/python3.5/site-packages/pyhanlp/static/hanlp-1.6.3.jar:/home/wancong/projects/flask/examples/javascript/venv/lib/python3.5/site-packages/pyhanlp/static  
Launcher Type: generic  
