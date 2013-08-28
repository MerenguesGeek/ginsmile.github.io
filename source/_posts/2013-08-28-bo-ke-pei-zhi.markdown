---
layout: post
title: "博客配置"
date: 2013-08-28 23:16
comments: true
categories: 
---

1.添加About Me页面
------------------------------------
首先创建about页面：`rake new_page["about"]`，就会在创建source/about目录的同时创建index.markdown,使用编辑器编辑即可。    
然后打开source/_includes/custom/navigation.html，修改成如下：
    <ul class="main-navigation">
      <li><a href="{{ root_url }}/">Blog</a></li>
      <li><a href="{{ root_url }}/blog/archives">Archives</a></li>
      <li><a href="{{ root_url }}/about">About Me</a></li>
    </ul>
{% img right /images/about_shot.png 247 130 'image' 'images' %}
然后使用`rake generate`命令，就会产生相应的静态页面。使用`rake preview`预览即可。    
如果想在username.github.io中看到，不要忘了`rake deploy`以及git命令提交到github。   

<!--more-->
2.添加社会化分享按钮
-----------------------------------------
只需要添加著名的社会化分享按钮addthis.com即可。去[addthis.com](https://www.addthis.com/get/sharing#.Uh4X56EW3nM)注册,获取代码。    
将代码粘贴到source/_includes/post/sharing.html中。例如我的sharing.html文件为：
    <div class="sharing">
        <!-- AddThis Button BEGIN -->
        <div class="addthis_toolbox addthis_default_style addthis_32x32_style">
            <a class="addthis_button_sinaweibo"></a>
            <a class="addthis_button_twitter"></a>
            <a class="addthis_button_facebook"></a>
            <a class="addthis_button_pinterest_share"></a>
            <a class="addthis_button_google_plusone_share"></a>
            <a class="addthis_button_compact"></a><a class="addthis_counter addthis_bubble_style"></a>
        </div>
        <script type="text/javascript">var addthis_config = {"data_track_addressbar":true};</script>
        <script type="text/javascript" src="//s7.addthis.com/js/300/addthis_widget.js#pubid=ra-521dd13b3fa550d0"></script>
        <!-- AddThis Button END -->
   
3.添加社会化评论
-----------------------------------------
Octopress已经提供了一个评论插件，名为Disqus，我们只需要到Disqus注册帐号，在注册的时候输入网站域名（username.github.io即可）。注册时的shortname很有用，下面代码中要修改的就是shortname！！注册成功后修改octopress目录下的_config.yml文件：
    #Disqus Comments
    disqus_short_name: shortname
    disqus_show_comment_count: true
*另外，这里注意，在修改_config.yml的时候，一定要注意冒号后面有个空格，否则在`rake generate`的时候会有解析错误*    
最重要的一点，_config.yml文件修改好之后必须generate之后才能在本地preview到。而其他文件，比如post了一个新的文章，如果处在preview状态，刷新一下localhost:4000会立马看到。




4.添加新浪微博支持
-------------------------------------------
原始的greyshade主题不支持新浪微博，这里稍加修改，即可在页面左下角显示新浪微博的按钮。本修改方法来自于[allenhsu](http://www.imallen.com/blog/2013/05/12/add-support-for-weibo-and-dribbble-to-greyshade.html)，在这里向作者表示感谢。     
{% img left /images/social_shot.png 282 114 'image' 'images' %}     

首先，在source/sass/parts/_header.scss文件中去掉第316行,`margin-right: 15px;`更改为：
    margin-right: 5px;
    margin-bottom: 15px;
然后，还是在上一个文件里，在320行往后添加weibo相关代码，最终代码段如下：
    &:hover{
    				opacity: 1;
    			}
    			&.weibo{
    				background: image-url('social/weibo.png') center no-repeat #e32529;
    				border: 1px solid #e32529;
    				&:hover{
    				  border: 1px solid darken(#e32529, 10%);
    				}
    			      }			      
    			&.facebook{
    				background: image-url('social/facebook.png') center no-repeat #3B5998;
    				border: 1px solid #3B5998;
    				&:hover{
    					border: 1px solid darken(#3B5998, 10%);
    				}
    			}
第三步，在source/_includes/header.html中，修改代码，在类为social的div下加上如下代码：
    <div class="social">
    		{% if site.weibo_user %}
    		<a class="weibo" href="http://www.weibo.com/{{ site.weibo_user }}" title="Weibo">Weibo</a>
    		{% endif %}
最后，不要忘了在source/images/social文件夹下添加weibo.png图片，可以直接到我的github下载。    
如果还不清楚，可在我的github中查看修改过程。修改commit链接。    

