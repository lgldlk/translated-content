---
title: <span>
slug: Web/HTML/Element/span
tags:
  - HTML
  - span
  - 元素
  - 流内容
  - 行内元素
translation_of: Web/HTML/Element/span
---
<div>{{HTMLRef}}</div>

<p><strong>HTML <code>&lt;span&gt;</code> </strong>元素是短语内容的通用行内容器，并没有任何特殊语义。可以使用它来编组元素以达到某种样式意图（通过使用类或者 Id 属性），或者这些元素有着共同的属性，比如<strong>lang</strong>。应该在没有其他合适的语义元素时才使用它。<code>&lt;span&gt;</code> 与 {{HTMLElement("div")}} 元素很相似，但 {{HTMLElement("div")}} 是一个 <a href="/en-US/docs/HTML/Block-level_elements">块元素</a> 而 <code>&lt;span&gt;</code> 则是 <a href="/en-US/docs/HTML/Inline_elements"> 行内元素 </a>.</p>

<div>{{EmbedInteractiveExample("pages/tabbed/span.html", "tabbed-shorter")}}</div>

<ul>
 <li><dfn><a href="/en-US/docs/HTML/Content_categories">内容分类</a></dfn> <a href="/en-US/docs/HTML/Content_categories#Flow_content">流内容</a>, <a href="/en-US/docs/HTML/Content_categories#Phrasing_content">表述内容</a>.</li>
 <li><dfn>允许的内容</dfn><a href="/zh-CN/docs/Web/Guide/HTML/Content_categories#Phrasing_content">短语元素</a></li>
 <li><dfn>标签省略</dfn> 不允许，开始标签和结束标签都不能省略。</li>
 <li><dfn>允许的父元素</dfn>任意可以包含 <a href="/en-US/docs/HTML/Content_categories#Phrasing_content">表述内容</a> 或 <a href="/en-US/docs/HTML/Content_categories#Flow_content">流内容</a> 的元素。</li>
 <li><dfn>DOM 接口</dfn>{{domxref("HTMLSpanElement")}} (在 {{glossary("HTML5")}}, 之前是 {{domxref("HTMLElement")}})</li>
</ul>

<h2 id="Attributes">属性</h2>

<p>该元素仅包含 <a href="https://developer.mozilla.org/en-US/docs/HTML/Global_attributes">全局属性</a>。</p>

<h2 id="Example1">例 1</h2>

<pre class="brush:html">&lt;p&gt;&lt;span&gt;一些文字&lt;/span&gt;&lt;/p&gt;</pre>

<h3 id="Result1">结果</h3>

<p>{{EmbedLiveSample('例 1')}}</p>

<h2 id="Example2">例 2</h2>

<pre class="brush:html">&lt;li&gt;&lt;span&gt;
    &lt;a href="portfolio.html" target="_blank"&gt;See my portfolio&lt;/a&gt;
&lt;/span&gt;&lt;/li&gt;
</pre>

<h3 id="CSS">CSS</h3>

<pre class="brush:css"><code>li span {
  background: gold;
 }</code></pre>

<h3 id="Result2">结果</h3>

<p>{{EmbedLiveSample('例 2')}}</p>

<h2 id="规范">规范</h2>

{{Specifications}}

<h2 id="See_also">浏览器兼容性</h2>

<p>{{Compat("html.elements.span")}}</p>

<h2 id="See_also">参见</h2>

<ul>
 <li>HTML {{HTMLElement("div")}} 元素</li>
</ul>