---
layout: post
title: Python code example
date: 2016-02-01 13:26:34
active: blog
icon: code
author: dstrbad
categories: python
comments: true
---


Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec in vehicula lorem, eleifend lobortis enim. Morbi cursus ante quis ligula lacinia eleifend. Nunc egestas sodales tellus. Donec aliquam, eros in ultricies iaculis, diam libero blandit metus, eget venenatis ipsum felis quis risus. Sed scelerisque magna non elit elementum mollis eu in mauris. Nulla bibendum rhoncus urna, eu pulvinar nisl. In id nibh dui. Etiam at condimentum nisi. Sed semper, turpis at vehicula sollicitudin, nibh turpis aliquet urna, aliquet euismod dui leo a sem. Nulla dapibus dui eu nulla euismod, a tincidunt risus sagittis. Praesent pretium quam id odio pulvinar dictum. Donec quis ultrices augue. Sed ultricies lectus id nulla porttitor pulvinar. In feugiat risus nisl.

{% highlight python %}
#! python

# input and operator if

x = int(raw_input("Please enter an integer: "))

if x < 0:
      x = 0
      print 'Negative changed to zero'
elif x == 0:
      print 'Zero'
elif x == 1:
      print 'Single'
else:
      print 'More'
{% endhighlight %}