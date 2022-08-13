---
title: <map>
slug: Web/HTML/Element/map
translation_of: Web/HTML/Element/map
---
<div class="blockIndicator note">
<p>这篇文章翻译不完整</p>
</div>

<p><strong>HTML <code>&lt;map&gt;</code> 属性</strong> 与 {{HTMLElement("area")}} 属性一起使用来定义一个图像映射 (一个可点击的链接区域).</p>

<table class="properties">
 <tbody>
  <tr>
   <th scope="row"><a href="/en-US/docs/HTML/Content_categories">内容类别</a></th>
   <td><a href="/en-US/docs/HTML/Content_categories#Flow_content">流式内容</a>，<a href="/en-US/docs/HTML/Content_categories#Phrasing_content">短语内容</a>，palpable 内容。</td>
  </tr>
  <tr>
   <th scope="row">允许的内容</th>
   <td>任何<a href="/en-US/docs/HTML/Content_categories#Transparent_content_model">透明</a>元素。</td>
  </tr>
  <tr>
   <th scope="row">标签省略</th>
   <td>{{no_tag_omission}}</td>
  </tr>
  <tr>
   <th scope="row">允许的父元素</th>
   <td>任何接受<a href="/en-US/docs/HTML/Content_categories#Phrasing_content">短语内容</a>的元素。</td>
  </tr>
  <tr>
   <th scope="row">DOM 接口</th>
   <td>{{domxref("HTMLMapElement")}}</td>
  </tr>
 </tbody>
</table>

<h2 id="属性">属性</h2>

<p>这个元素拥有<a href="https://developer.mozilla.org/en-US/docs/HTML/Global_attributes">全局属性</a>。</p>

<dl>
 <dt>{{htmlattrdef("name")}}</dt>
 <dd>name 属性 给 map 一个名字用来查询，这个属性是必须的，值必须不能为空并且不能带空格。name 属性不准与同文档中其他 map 元素的值相同，如果 id 属性也被添加，name 属性和 id 属性的值必须相同。</dd>
</dl>

<h2 id="示例">示例</h2>

<pre class="brush: html notranslate">&lt;map name="example-map-1"&gt;
  &lt;area shape="circle" coords="200,250,25" href="another.htm" /&gt;
  &lt;area shape="default" /&gt;
&lt;/map&gt;

</pre>

<h3 id="结果">结果</h3>

<p>{{ EmbedLiveSample('Examples', '350', '166', '', 'Web/HTML/Element/map') }}</p>

<h3 id="Expected_live_example_output">Expected live example output</h3>

<p>The live example above should appear similar to the following images (when using your keyboard tab key):</p>

<p><em>For the <code>left.html</code> link:</em><br>
 <img alt="" src="https://mdn.mozillademos.org/files/14595/Screen%20Shot%202017-02-02%20at%2010.48.40%20PM.png"></p>

<p><em>For the <code>right.html</code> link</em><br>
 <img alt="" src="https://mdn.mozillademos.org/files/14597/Screen%20Shot%202017-02-02%20at%2010.49.04%20PM.png"></p>

<h2 id="规范">规范</h2>

{{Specifications}}

<h2 id="浏览器兼容性">浏览器兼容性</h2>

{{Compat("html.elements.map")}}

<h2 id="另见">另见</h2>

<ul>
 <li>{{HTMLElement("a")}}</li>
 <li>{{HTMLElement("area")}}</li>
</ul>

<p>{{HTMLRef}}</p>