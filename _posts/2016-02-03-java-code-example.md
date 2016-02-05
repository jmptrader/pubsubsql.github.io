---
layout: post
title: Java code example
date: 2016-02-03 13:26:34
active: blog
icon: code
author: vsimunov
categories: code
comments: true
---


Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec in vehicula lorem, eleifend lobortis enim. Morbi cursus ante quis ligula lacinia eleifend. Nunc egestas sodales tellus. Donec aliquam, eros in ultricies iaculis, diam libero blandit metus, eget venenatis ipsum felis quis risus. Sed scelerisque magna non elit elementum mollis eu in mauris. Nulla bibendum rhoncus urna, eu pulvinar nisl. In id nibh dui. Etiam at condimentum nisi. Sed semper, turpis at vehicula sollicitudin, nibh turpis aliquet urna, aliquet euismod dui leo a sem. Nulla dapibus dui eu nulla euismod, a tincidunt risus sagittis. Praesent pretium quam id odio pulvinar dictum. Donec quis ultrices augue. Sed ultricies lectus id nulla porttitor pulvinar. In feugiat risus nisl.

{% highlight java %}
import java.awt.Rectangle;

public class ObjectVarsAsParameters
{ public static void main(String[] args)
  { go();
  }
  
  public static void go()
  { Rectangle r1 = new Rectangle(0,0,5,5);
    System.out.println("In method go. r1 " + r1 + "\n");
    // could have been 
    //System.out.prinltn("r1" + r1.toString());
    r1.setSize(10, 15);
    System.out.println("In method go. r1 " + r1 + "\n");
    alterPointee(r1);
    System.out.println("In method go. r1 " + r1 + "\n");
    
    alterPointer(r1);
    System.out.println("In method go. r1 " + r1 + "\n");
  }
  
  public static void alterPointee(Rectangle r)
  { System.out.println("In method alterPointee. r " + r + "\n");
    r.setSize(20, 30);
    System.out.println("In method alterPointee. r " + r + "\n");
  }
  
  public static void alterPointer(Rectangle r)
  { System.out.println("In method alterPointer. r " + r + "\n");
    r = new Rectangle(5, 10, 30, 35);
    System.out.println("In method alterPointer. r " + r + "\n");
  }
  
  
}
{% endhighlight %}