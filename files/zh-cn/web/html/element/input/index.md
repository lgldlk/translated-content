---
title: <input>：输入（表单输入）元素
slug: Web/HTML/Element/Input
tags:
  - Element
  - Forms
  - HTML
  - HTML forms
  - HTML input tag
  - Input
  - Reference
  - Web
translation_of: Web/HTML/Element/input
---
<p>{{HTMLRef}}</p>

<p><strong>HTML <code>&lt;input&gt;</code> 元素</strong>用于为基于 Web 的表单创建交互式控件，以便接受来自用户的数据; 可以使用各种类型的输入数据和控件小部件，具体取决于设备和{{Glossary("user agent", "用户代理")}}。</p>

<p>{{EmbedInteractiveExample("pages/tabbed/input-text.html", "tabbed-shorter")}}</p>

<table class="properties">
 <tbody>
  <tr>
   <th scope="row"><a href="/en-US/docs/HTML/Content_categories">内容分类</a></th>
   <td>流式元素；短语元素；交互元素（若 type 属性不处于隐藏 <code>hidden</code>状态）；表单相关内容、可列举的元素、可标签的元素、可提交的元素、可重置的元素。</td>
  </tr>
  <tr>
   <th scope="row">允许的内容</th>
   <td>无，这是一个{{Glossary("empty element","空元素")}}。</td>
  </tr>
  <tr>
   <th scope="row">标签省略</th>
   <td>
    <p>必须有开始标签但不必有结束标签。</p>
   </td>
  </tr>
  <tr>
   <th scope="row">允许的祖先元素</th>
   <td>任何元素都可以包含语句型元素。</td>
  </tr>
  <tr>
   <th scope="row">允许的无障碍网络应用</th>
   <td>
    <ul>
     <li><code>type=button</code>：{{ARIARole("link")}}, {{ARIARole("menuitem")}}, {{ARIARole("menuitemcheckbox")}}, {{ARIARole("menuitemradio")}}, {{ARIARole("radio")}}, {{ARIARole("switch")}}, {{ARIARole("tab")}}</li>
     <li><code>type=checkbox</code>：{{ARIARole("button")}}, {{ARIARole("menuitemcheckbox")}}, {{ARIARole("option")}}, {{ARIARole("switch")}}</li>
     <li><code>type=image</code>：{{ARIARole("link")}}, {{ARIARole("menuitem")}}, {{ARIARole("menuitemcheckbox")}}, {{ARIARole("menuitemradio")}}, {{ARIARole("radio")}}, {{ARIARole("switch")}}</li>
     <li><code>type=radio</code>：{{ARIARole("menuitemradio")}}</li>
     <li><code>type=color|date|datetime|datetime-local|email|file</code>：None</li>
     <li><code>type=hidden|month|number|password|range|research</code>：None</li>
     <li><code>type=search|submit|tel|text|url|week</code>：None</li>
    </ul>
   </td>
  </tr>
  <tr>
   <th scope="row">DOM 接口</th>
   <td>{{domxref("HTMLInputElement")}}</td>
  </tr>
 </tbody>
</table>

<h2 id="&lt;input>_types"><code>&lt;input&gt;</code> types</h2>

<p><code>&lt;input&gt;</code> 的工作方式相当程度上取决于 {{htmlattrxref("type", "input")}} 属性的值，不同的 type 值会在各自的参考页中进行介绍。如果未指定此属性，则采用的默认类型为 <code>text</code>。</p>

<p>可用的值包括：</p>

<table class="standard-table">
 <colgroup>
  <col>
  <col style="width: 50%;">
  <col>
 </colgroup>
 <thead>
  <tr>
   <th>Type</th>
   <th>描述</th>
   <th>基础例子</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{HTMLElement("input/button", "button")}}</td>
   <td>没有默认行为的按钮，上面显示 <a href="#attr-value">value</a> 属性的值，默认为空。</td>
   <td id="examplebutton">
    <pre class="brush: html hidden">
&lt;input type="button" name="button" /&gt;
    </pre>
    {{EmbedLiveSample("examplebutton",200,55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/checkbox", "checkbox")}}</td>
   <td>复选框，可设为选中或未选中。</td>
   <td id="examplecheckbox">
    <pre class="brush: html hidden">
&lt;input type="checkbox" name="checkbox"/&gt;
    </pre>
    {{EmbedLiveSample("examplecheckbox",200,55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/color", "color")}}</td>
   <td>用于指定颜色的控件；在支持的浏览器中，激活时会打开取色器。</td>
   <td id="examplecolor">
    <pre class="brush: html hidden">
&lt;input type="color" name="color"/&gt;
    </pre>
    {{EmbedLiveSample("examplecolor",200,55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/date", "date")}}</td>
   <td>输入日期的控件（年、月、日，不包括时间）。在支持的浏览器激活时打开日期选择器或年月日的数字滚轮。</td>
   <td id="exampledate">
    <pre class="brush: html hidden">
&lt;input type="date" name="date"/&gt;
    </pre>
    {{EmbedLiveSample("exampledate",200,55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/datetime-local", "datetime-local")}}</td>
   <td>输入日期和时间的控件，不包括时区。在支持的浏览器激活时打开日期选择器或年月日的数字滚轮。</td>
   <td id="exampledtl">
    <pre class="brush: html hidden">
&lt;input type="datetime-local" name="datetime-local"/&gt;
    </pre>
    {{EmbedLiveSample("exampledtl",200,55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/email", "email")}}</td>
   <td>编辑邮箱地址的区域。类似 <code>text</code> 输入，但在支持的浏览器和带有动态键盘的设备上会有确认参数和相应的键盘。</td>
   <td id="exampleemail">
    <pre class="brush: html hidden">
&lt;input type="email" name="email"/&gt;
    </pre>
    {{EmbedLiveSample("exampleemail",200,55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/file", "file")}}</td>
   <td>让用户选择文件的控件。使用 <a href="#attr-accept">accept</a> 属性规定控件能选择的文件类型。</td>
   <td id="examplefile">
    <pre class="brush: html hidden">
&lt;input type="file" accept="image/*, text/*" name="file"/&gt;
    </pre>
    {{EmbedLiveSample("examplefile",'100%',55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/hidden", "hidden")}}</td>
   <td>不显示的控件，其值仍会提交到服务器。举个例子，右边就是一个隐形的控件。</td>
   <td></td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/image", "image")}}</td>
   <td>带图像的 <code>submit</code> 按钮。显示的图像由 <code>src</code> 属性规定。如果 <a href="#attr-src">src</a> 缺失，<a href="#attr-alt">alt</a> 属性就会显示。</td>
   <td id="exampleimage">
    <pre class="brush: html hidden">
&lt;input type="image" name="image" src="" alt="image input"/&gt;
    </pre>
    {{EmbedLiveSample("exampleimage",200,55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/month", "month")}}</td>
   <td>输入年和月的控件，没有时区。</td>
   <td id="examplemonth">
    <pre class="brush: html hidden">
&lt;input type="month" name="month"/&gt;
    </pre>
    {{EmbedLiveSample("examplemonth",200,55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/number", "number")}}</td>
   <td>用于输入数字的控件。如果支持的话，会显示滚动按钮并提供缺省验证（即只能输入数字）。拥有动态键盘的设备上会显示数字键盘。</td>
   <td id="examplenumber">
    <pre class="brush: html hidden">
&lt;input type="number" name="number"/&gt;
    </pre>
    {{EmbedLiveSample("examplenumber",200,55,"","", "nobutton")}}</td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/password", "password")}}</td>
   <td>单行的文本区域，其值会被遮盖。如果站点不安全，会警告用户。</td>
   <td id="examplepassword">
    <pre class="brush: html hidden">
&lt;input type="password" name="password"/&gt;
    </pre>
    {{EmbedLiveSample("examplepassword",200,55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/radio", "radio")}}</td>
   <td>单选按钮，允许在多个拥有相同 <a href="#attr-name">name</a> 值的选项中选中其中一个。</td>
   <td id="exampleradio">
    <pre class="brush: html hidden">
&lt;input type="radio" name="radio"/&gt;
    </pre>
    {{EmbedLiveSample("exampleradio",200,55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/range", "range")}}</td>
   <td>此控件用于输入不需要精确的数字。控件是一个范围组件，默认值为正中间的值。同时使用 <a href="#attr-min">min</a> 和 <a href="#attr-max">max</a> 来规定值的范围。</td>
   <td id="examplerange">
    <pre class="brush: html hidden">
&lt;input type="range" name="range" min="0" max="25"/&gt;
    </pre>
    {{EmbedLiveSample("examplerange",200,55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/reset", "reset")}}</td>
   <td>此按钮将表单的所有内容重置为默认值。不推荐。</td>
   <td id="examplereset">
    <pre class="brush: html hidden">
&lt;input type="reset" name="reset"/&gt;
    </pre>
    {{EmbedLiveSample("examplereset",200,55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/search", "search")}}</td>
   <td>用于搜索字符串的单行文字区域。输入文本中的换行会被自动去除。在支持的浏览器中可能有一个删除按钮，用于清除整个区域。拥有动态键盘的设备上的回车图标会变成搜索图标。</td>
   <td id="examplesearch">
    <pre class="brush: html hidden">
&lt;input type="search" name="search"/&gt;
    </pre>
    {{EmbedLiveSample("examplesearch",200,55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/submit", "submit")}}</td>
   <td>用于提交表单的按钮。</td>
   <td id="examplesubmit">
    <pre class="brush: html hidden">
&lt;input type="submit" name="submit"/&gt;
    </pre>
    {{EmbedLiveSample("examplesubmit",200,55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/tel", "tel")}}</td>
   <td>用于输入电话号码的控件。拥有动态键盘的设备上会显示电话数字键盘。</td>
   <td id="exampletel">
    <pre class="brush: html hidden">
&lt;input type="tel" name="tel"/&gt;
    </pre>
    {{EmbedLiveSample("exampletel",200,55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/text", "text")}}</td>
   <td>默认值。单行的文本区域，输入中的换行会被自动去除。</td>
   <td id="exampletext">
    <pre class="brush: html hidden">
&lt;input type="text" name="text"/&gt;
    </pre>
    {{EmbedLiveSample("exampletext",200,55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/time", "time")}}</td>
   <td>用于输入时间的控件，不包括时区。</td>
   <td id="exampletime">
    <pre class="brush: html hidden">
&lt;input type="time" name="time"/&gt;
    </pre>
    {{EmbedLiveSample("exampletime",200,55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/url", "url")}}</td>
   <td>
    <p>用于输入 URL 的控件。类似 <code>text</code> 输入，但有验证参数，在支持动态键盘的设备上有相应的键盘。</p>
   </td>
   <td id="exampleurl">
    <pre class="brush: html hidden">
&lt;input type="url" name="url"/&gt;
    </pre>
    {{EmbedLiveSample("exampleurl",200,55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <td>{{HTMLElement("input/week", "week")}}</td>
   <td>用于输入以年和周数组成的日期，不带时区。</td>
   <td id="exampleweek">
    <pre class="brush: html hidden">
&lt;input type="week" name="week"/&gt;
    </pre>
    {{EmbedLiveSample("exampleweek",200,55,"","", "nobutton")}}
   </td>
  </tr>
  <tr>
   <th colspan="3">废弃的值</th>
  </tr>
  <tr>
   <td>{{HTMLElement("input/datetime", "datetime")}}</td>
   <td>{{deprecated_inline}} 用于输入基于 UTC 时区的日期和时间（时、分、秒及秒的小数部分）。</td>
   <td id="exampledatetime">
    <pre class="brush: html hidden">
&lt;input type="datetime" name="datetime"/&gt;
    </pre>
    {{EmbedLiveSample("exampledatetime",200,75,"","", "nobutton")}}
   </td>
  </tr>
 </tbody>
</table>

<h2 id="属性">属性</h2>

<p><code>&lt;input&gt;</code> 元素由于拥有诸多属性而异常强大，其中前文举例说明的 {{htmlattrxref("type", "input")}} 属性尤其重要。由于所有 <code>&lt;input&gt;</code> 元素，无论是哪种 <code>type</code>，都基于 {{domxref("HTMLInputElement")}} 接口，所以理论上说，它们共享一套相同的属性。但实际上大部分属性只作用于特定一组 <code>type</code>。此外，一些属性作用于 <code>&lt;input&gt;</code> 的方式取决于 <code>&lt;input&gt;</code> 的 <code>type</code> 属性，不同的 <code>type</code> 有不同的效果。</p>

<p>下面的表格列出了所有属性，每个属性都有简短的描述。表格后的列表更详细地描述了各个属性及它们与哪些 <code>&lt;input&gt;</code> <code>type</code> 相关。与大部分或者全部 <code>&lt;input&gt;</code> <code>type</code> 都相关的属性会讲述更多细节。一些针对特定 <code>&lt;input&gt;</code> <code>type</code> 的属性，或者所有 <code>&lt;input&gt;</code> <code>type</code> 都有，但在特定的 <code>&lt;input&gt;</code> <code>type</code> 上有特定表现的属性，会在相应的 <code>type</code> 页面中说明。这个元素包含全局属性，一些针对 <code>&lt;input&gt;</code> 元素有额外意义的全局属性也会特别说明。</p>

<table>
 <caption>
 <p>{{htmlelement('input')}} 元素的属性包括<a href="/zh-CN/docs/Web/HTML/Global_attributes">全局 HTML 属性</a>和以下属性：</p>

 <table>
  <thead>
   <tr>
    <th scope="col">属性</th>
    <th scope="col">相关的 type</th>
    <th scope="col">描述</th>
   </tr>
  </thead>
  <tbody>
   <tr>
    <td><a href="#attr-accept">accept</a></td>
    <td>file</td>
    <td>用于规定文件上传控件中期望的文件类型</td>
   </tr>
   <tr>
    <td><a href="#attr-alt">alt</a></td>
    <td>image</td>
    <td>image type 的 alt 属性，是可访问性的要求。</td>
   </tr>
   <tr>
    <td><a href="#attr-autocomplete">autocomplete</a></td>
    <td>所有</td>
    <td>用于表单的自动填充功能</td>
   </tr>
   <tr>
    <td><a href="#attr-autofocus">autofocus</a></td>
    <td>所有</td>
    <td>页面加载时自动聚焦到此表单控件</td>
   </tr>
   <tr>
    <td><a href="#attr-capture">capture</a></td>
    <td>file</td>
    <td>文件上传控件中媒体拍摄的方式</td>
   </tr>
   <tr>
    <td><a href="#attr-checked">checked</a></td>
    <td>radio、checkbox</td>
    <td>用于控制控件是否被选中</td>
   </tr>
   <tr>
    <td><a href="#attr-dirname">dirname</a></td>
    <td>text、search</td>
    <td>表单区域的一个名字，用于在提交表单时发送元素的方向性</td>
   </tr>
   <tr>
    <td><a href="#attr-disabled">disabled</a></td>
    <td>所有</td>
    <td>表单控件是否被禁用</td>
   </tr>
   <tr>
    <td><a href="#attr-form">form</a></td>
    <td>所有</td>
    <td>将控件和一个 form 元素联系在一起</td>
   </tr>
   <tr>
    <td><a href="#attr-formaction">formaction</a></td>
    <td>image、submit</td>
    <td>用于提交表单的 URL</td>
   </tr>
   <tr>
    <td><a href="#attr-formenctype">formenctype</a></td>
    <td>image、submit</td>
    <td>表单数据集的编码方式，用于表单提交</td>
   </tr>
   <tr>
    <td><a href="#attr-formmethod">formmethod</a></td>
    <td>image、submit</td>
    <td>用于表单提交的 HTTP 方法 </td>
   </tr>
   <tr>
    <td><a href="#attr-formnovalidate">formnovalidate</a></td>
    <td>image、submit</td>
    <td>提交表单时绕过对表单控件的验证</td>
   </tr>
   <tr>
    <td><a href="#attr-formtarget">formtarget</a></td>
    <td>image、submit</td>
    <td>表单提交的浏览上下文</td>
   </tr>
   <tr>
    <td><a href="#attr-height">height</a></td>
    <td>image</td>
    <td>
     <p>和 {{htmlelement('img')}} 的 <code>height</code> 属性相同；垂直方向</p>
    </td>
   </tr>
   <tr>
    <td><a href="#attr-list">list</a></td>
    <td>绝大部分</td>
    <td>自动填充选项的 {{htmlelement('datalist')}} 的 id 值</td>
   </tr>
   <tr>
    <td><a href="#attr-max">max</a></td>
    <td>数字 type</td>
    <td>最大值</td>
   </tr>
   <tr>
    <td><a href="#attr-maxlength">maxlength</a></td>
    <td>password、search、tel、text、url</td>
    <td><code>value</code> 的最大长度（最多字符数目）</td>
   </tr>
   <tr>
    <td><a href="#attr-min">min</a></td>
    <td>数字 type</td>
    <td>最小值</td>
   </tr>
   <tr>
    <td><a href="#attr-minlength">minlength</a></td>
    <td>password、search、tel、text、url</td>
    <td><code>value</code> 的最小长度（最少字符数目）</td>
   </tr>
   <tr>
    <td><a href="#attr-multiple">multiple</a></td>
    <td>email、file</td>
    <td>布尔值。是否允许多个值</td>
   </tr>
   <tr>
    <td><a href="#attr-name">name</a></td>
    <td>所有</td>
    <td>input 表单控件的名字。以名字/值对的形式随表单一起提交</td>
   </tr>
   <tr>
    <td><a href="#attr-pattern">pattern</a></td>
    <td>password、text、tel</td>
    <td>匹配有效 <code>value</code> 的模式（pattern）</td>
   </tr>
   <tr>
    <td><a href="#attr-placeholder">placeholder</a></td>
    <td>password、search、tel、text、url</td>
    <td>当表单控件为空时，控件中显示的内容</td>
   </tr>
   <tr>
    <td><a href="/zh-CN/docs/Web/HTML/Attributes/readonly">readonly</a></td>
    <td>绝大部分</td>
    <td>布尔值。存在时表示控件的值不可编辑</td>
   </tr>
   <tr>
    <td><a href="/zh-CN/docs/Web/HTML/Attributes/required">required</a></td>
    <td>绝大部分</td>
    <td>布尔值。表示此值为必填项或者提交表单前必须先检查该值</td>
   </tr>
   <tr>
    <td><a href="#attr-size">size</a></td>
    <td>email、password、tel、text</td>
    <td>控件的大小</td>
   </tr>
   <tr>
    <td><a href="#attr-src">src</a></td>
    <td>image</td>
    <td>和 {{htmlelement('img')}} 的 <code>src</code> 属性一样；图像资源的地址</td>
   </tr>
   <tr>
    <td><a href="#attr-step">step</a></td>
    <td>数字 type</td>
    <td>有效的递增值</td>
   </tr>
   <tr>
    <td><a href="#attr-type">type</a></td>
    <td>所有</td>
    <td>input 表单控件的 type</td>
   </tr>
   <tr>
    <td><a href="#attr-value">value</a></td>
    <td>所有</td>
    <td>表单控件的值。以名字/值对的形式随表单一起提交</td>
   </tr>
   <tr>
    <td><a href="#attr-width">width</a></td>
    <td>image</td>
    <td>与 {{htmlelement('img')}} 的 <code>width</code> 属性一样</td>
   </tr>
  </tbody>
 </table>
 </caption>
</table>

<p>一些额外的非标准属性会在标准属性后面列出。</p>

<h3 id="属性各论">属性各论</h3>

<dl>
 <dt>{{ htmlattrdef("accept") }}</dt>
 <dd>如果该元素的 <strong>type</strong> 属性的值是 <code>file</code>，则该属性表明了服务器端可接受的文件类型；否则它将被忽略。该属性的值必须为一个逗号分割的列表，包含了多个唯一的内容类型声明：
 <ul>
  <li>以 STOP 字符 (U+002E) 开始的文件扩展名。（例如：".jpg,.png,.doc"）</li>
  <li>一个有效的 MIME 类型，但没有扩展名</li>
  <li><code>audio/*</code> 表示音频文件</li>
  <li><code>video/*</code> 表示视频文件</li>
  <li><code>image/*</code> 表示图片文件</li>
 </ul>
 </dd>
 <dt>{{ htmlattrdef("accesskey") }} {{Deprecated_Inline}}</dt>
 <dd>用户按下后可以获得此控件焦点的单个字符。这是 HTML5 全局属性。</dd>
 <dt>{{ htmlattrdef("autocomplete") }}</dt>
 <dd>这个属性表示这个控件的值是否可被浏览器自动填充。如果 <strong>type</strong> 属性的值是 hidden、checkbox、radio、file，或为按钮类型（button、submit、reset、image），则本属性被忽略。可用的值是：
 <ul>
  <li><code>off</code>：用户必须手动填值，或者该页面提供了自己的自动补全方法。浏览器不对此字段自动填充。</li>
  <li><code>on</code>：浏览器可以根据用户先前的填表情况对此字段自动填值。</li>
  <li><code>name</code>：完整的姓名</li>
  <li><code>honorific-prefix</code>：Prefix or title (e.g. "Mr.", "Ms.", "Dr.", "Mlle")</li>
  <li><code>given-name</code>：名</li>
  <li><code>additional-name</code></li>
  <li><code>family-name</code>：姓</li>
  <li><code>honorific-suffix</code>：Suffix (e.g. "Jr.", "B.Sc.", "MBASW", "II")</li>
  <li><code>nickname</code></li>
  <li><code>email</code></li>
  <li><code>username</code></li>
  <li><code>new-password</code>：新密码（如创建帐号或更改密码时使用）</li>
  <li><code>current-password</code></li>
  <li><code>organization-title</code>：Job title (e.g. "Software Engineer", "Senior Vice President", "Deputy Managing Director")</li>
  <li><code>organization</code></li>
  <li><code>street-address</code></li>
  <li><code>address-line1</code>、<code>address-line2</code>、<code>address-line3</code>、<code>address-level4</code>、<code>address-level3</code>、<code>address-level2</code>、<code>address-level1</code></li>
  <li><code>country</code></li>
  <li><code>country-name</code></li>
  <li><code>postal-code</code></li>
  <li><code>cc-name</code>：Full name as given on the payment instrument</li>
  <li><code>cc-given-name</code></li>
  <li><code>cc-additional-name</code></li>
  <li><code>cc-family-name</code></li>
  <li><code>cc-number</code>：Code identifying the payment instrument (e.g. the credit card number)</li>
  <li><code>cc-exp</code>：Expiration date of the payment instrument</li>
  <li><code>cc-exp-month</code></li>
  <li><code>cc-exp-year</code></li>
  <li><code>cc-csc</code>：Security code for the payment instrument </li>
  <li><code>cc-type</code>：Type of payment instrument (e.g. Visa)</li>
  <li><code>transaction-currency</code></li>
  <li><code>transaction-amount</code></li>
  <li><code>language</code>：Preferred language; Valid BCP 47 language tag</li>
  <li><code>bday</code></li>
  <li><code>bday-day</code></li>
  <li><code>bday-month</code></li>
  <li><code>bday-year</code></li>
  <li><code>sex</code>：Gender identity (e.g. Female, Fa'afafine); Free-form text, no newlines</li>
  <li><code>tel</code></li>
  <li><code>url</code>：Home page or other Web page corresponding to the company, person, address, or contact information in the other fields associated with this field</li>
  <li><code>photo</code>：Photograph, icon, or other image corresponding to the company, person, address, or contact information in the other fields associated with this field</li>
  <li>
   <p>参考 <a href="https://html.spec.whatwg.org/multipage/forms.html#autofill">WHATWG 标准</a> 获取更多详细内容。</p>
  </li>
 </ul>

 <p>如果 <code>&lt;input&gt;</code> 元素上没有 <strong>autocomplete</strong> 属性，浏览器可使用包含该 input 元素的表单（<code>&lt;form&gt;</code>）或通过 input 的 <strong>form</strong> 属性指定的表单的 <strong>autocomplete</strong> 属性值。更多信息请参见 {{ HTMLElement("form") }} 的 <code>autocomplete</code> 属性。</p>

 <p>与其他浏览器不同，<strong>autocomplete</strong> 还控制着 Firefox 浏览器对 &lt;input&gt; 持久化动态禁用状态和（如果适用）跨页面加载的动态检查。持久化特性默认是开启的。设置 <strong>autocomplete</strong> 的值为 <strong>off</strong> 可以关闭该特性。即使 autocomplete 属性通常不应用于 &lt;input&gt; 的 type，它也可以工作。具体可以查看 {{bug(654072)}}。</p>
 </dd>
 <dt>{{ htmlattrdef("autofocus") }}</dt>
 <dd>这个布尔属性允许您指定的表单控件在页面加载时具有焦点（自动获得焦点），除非用户将其覆盖，例如通过键入不同的控件。文档中只有一个表单元素可以具有 autofocus 属性，它是一个布尔值。 如果 type 属性设置为隐藏则不能应用（即您不能自动获得焦点的属性设置为隐藏的控件）。</dd>
 <dt>{{htmlattrdef("capture")}}</dt>
 <dd>
 <p>Introduced in the HTML Media Capture specification and valid for the <code>file</code> input type only, the <code>capture</code> attribute defines which media—microphone, video, or camera—should be used to capture a new file for upload with <code>file</code> upload control in supporting scenarios. See the {{HTMLElement("input/file", "file")}} input type.</p>
 </dd>
 <dt>{{ htmlattrdef("checked") }}</dt>
 <dd>如果该元素的 <strong>type</strong> 属性的值为 radio 或者 checkbox，则该布尔属性的存在与否表明了该控件是否是默认选择状态。
 <p>If present on a <code>checkbox</code> type, it indicates that the checkbox is checked by default (when the page loads). It does <em>not</em> indicate whether this checkbox is currently checked: if the checkbox’s state is changed, this content attribute does not reflect the change. (Only the <a href="/zh-CN/docs/Web/API/HTMLInputElement"><code>HTMLInputElement</code>’s <code>checked</code> IDL attribute</a> is updated.)</p>

 <div class="note">
 <p><strong>Note:</strong> Unlike other input controls, a checkboxes and radio buttons value are only included in the submitted data if they are currently <code>checked</code>. If they are, the name and the value(s) of the checked controls are submitted.</p>

 <p>For example, if a checkbox whose <code>name</code> is <code>fruit</code> has a <code>value</code> of <code>cherry</code>, and the checkbox is checked, the form data submitted will include <code>fruit=cherry</code>. If the checkbox isn't active, it isn't listed in the form data at all. The default <code>value</code> for checkboxes and radio buttons is <code>on</code>.</p>
 </div>
 </dd>
 <dt>{{htmlattrdef("dirname")}}</dt>
 <dd>
 <p>Valid for <code>text</code> and <code>search</code> input types only, the <code>dirname</code> attribute enables the submission of the directionality of the element. When included, the form control will submit with two name/value pairs: the first being the <a href="#attr-name">name</a> and <a href="#attr-value">value</a>, the second being the value of the <code>dirname</code> as the name with the value of <code>ltr</code> or <code>rtl</code> being set by the browser.</p>

 <pre><code>&lt;form action="page.html" method="post"&gt;
  &lt;label&gt;Fruit: &lt;input type="text" name="fruit" dirname="fruit.dir" value="cherry"&gt;&lt;/label&gt;
  &lt;input type="submit"/&gt;
&lt;/form&gt;
&lt;!-- page.html?fruit=cherry&amp;fruit.dir=ltr --&gt;</code>
</pre>

 <p>When the form above is submitted, the input cause both the <code>name</code> / <code>value</code> pair of <code>fruit=cherry</code> and the <code>dirname</code> / direction pair of <code>fruit.dir=ltr</code> to be sent.</p>
 </dd>
 <dt>{{ htmlattrdef("disabled") }}</dt>
 <dd>这个布尔属性表示此表单控件不可用。 特别是在禁用的控件中， <code>click</code> 事件 <a href="http://www.whatwg.org/specs/web-apps/current-work/multipage/association-of-controls-and-forms.html#enabling-and-disabling-form-controls">将不会被分发</a> 。 并且，禁用的控件的值在提交表单时也不会被提交。如果 <strong>type</strong> 属性为  hidden，此属性将被忽略。</dd>
</dl>

<div class="note"><strong>Note:</strong> Although not required by the specification, Firefox will by default <a href="https://stackoverflow.com/questions/5985839/bug-with-firefox-disabled-attribute-of-input-not-resetting-when-refreshing">persist the dynamic disabled state</a> of an <code>&lt;input&gt;</code> across page loads. Use the {{htmlattrxref("autocomplete","input")}} attribute to control this feature.</div>

<dl>
 <dt>{{ htmlattrdef("form") }}</dt>
 <dd>
 <p>A string specifying the {{HTMLElement("form")}} element with which the input is associated (that is, its <strong>form owner</strong>). This string's value, if present, must match the {{htmlattrxref("id")}} of a <code>&lt;form&gt;</code> element in the same document. If this attribute isn't specified, the <code>&lt;input&gt;</code> element is associated with the nearest containing form, if any.</p>

 <p>The <code>form</code> attribute lets you place an input anywhere in the document but have it included with a form elsewhere in the document.</p>

 <p>Note: An input can only be associated with one form.</p>
 </dd>
 <dt>{{htmlattrdef('formaction')}}</dt>
 <dd>
 <p>Valid for the <code>image</code> and <code>submit</code> input types only. See the {{HTMLElement("input/submit", "submit")}} input type for more information.</p>
 </dd>
 <dt>{{htmlattrdef('formenctype')}}</dt>
 <dd>
 <p>Valid for the <code>image</code> and <code>submit</code> input types only. See the {{HTMLElement("input/submit", "submit")}} input type for more information.</p>
 </dd>
 <dt>{{htmlattrdef('formmethod')}}</dt>
 <dd>
 <p>Valid for the <code>image</code> and <code>submit</code> input types only. See the {{HTMLElement("input/submit", "submit")}} input type for more information.</p>
 </dd>
 <dt>{{htmlattrdef('formnovalidate')}}</dt>
 <dd>
 <p>Valid for the <code>image</code> and <code>submit</code> input types only. See the {{HTMLElement("input/submit", "submit")}} input type for more information.</p>
 </dd>
 <dt>{{htmlattrdef('formtarget')}}</dt>
 <dd>
 <p>Valid for the <code>image</code> and <code>submit</code> input types only. See the {{HTMLElement("input/submit", "submit")}} input type for more information.</p>
 </dd>
 <dt>{{ htmlattrdef("height") }}</dt>
 <dd>如果 <strong>type</strong> 属性的值是 image，这个属性定义了按钮图片的高度。</dd>
 <dt>{{htmlattrdef("id")}}</dt>
 <dd>
 <p>Global attribute valid for all elements, including all the input types, it defines a unique identifier (ID) which must be unique in the whole document. Its purpose is to identify the element when linking. The value is used as the value of the {{htmlelement('label')}}'s <code>for</code> attribute to link the label with the form control. See the <a href="#labels">the label element</a> below.</p>
 </dd>
 <dt>{{htmlattrdef("inputmode")}}</dt>
 <dd>
 <p>Global value valid for all elements, it provides a hint to browsers as to the type of virtual keyboard configuration to use when editing this element or its contents. Values include none<br>
  <code>text</code>, <code>tel</code>, <code>url</code>, <code>email</code>, <code>numeric</code>, <code>decimal</code>, and <code>search</code>.</p>
 </dd>
 <dt>{{htmlattrdef("list")}}</dt>
 <dd>
  <p>The values of the list attribute is the {{domxref("Element.id", "id")}} of a {{HTMLElement("datalist")}} element located in the same document. The <code>&lt;datalist&gt;</code>  provides a list of predefined values to suggest to the user for this input. Any values in the list that are not compatible with the {{htmlattrxref("type", "input")}} are not included in the suggested options.  The values provided are suggestions, not requirements: users can select from this predefined list or provide a different value.</p>
 </dd>
</dl>


<pre class="brush: html">
&lt;datalist id="colorsxx"&gt;
  &lt;option&gt;#ff0000&lt;/option&gt;
  &lt;option&gt;#ee0000&lt;/option&gt;
  &lt;option&gt;#dd0000&lt;/option&gt;
  &lt;option&gt;#cc0000&lt;/option&gt;
  &lt;option&gt;#bb0000&lt;/option&gt;
&lt;/datalist&gt;
&lt;datalist id="numbersxx"&gt;
  &lt;option&gt;0&lt;/option&gt;
  &lt;option&gt;2&lt;/option&gt;
  &lt;option&gt;4&lt;/option&gt;
  &lt;option&gt;8&lt;/option&gt;
  &lt;option&gt;16&lt;/option&gt;
  &lt;option&gt;32&lt;/option&gt;
  &lt;option&gt;64&lt;/option&gt;
&lt;/datalist&gt;
&lt;datalist id="fruitsxx"&gt;
  &lt;option&gt;cherry&lt;/option&gt;
  &lt;option&gt;banana&lt;/option&gt;
  &lt;option&gt;mango&lt;/option&gt;
  &lt;option&gt;orange&lt;/option&gt;
  &lt;option&gt;blueberry&lt;/option&gt;
&lt;/datalist&gt;
&lt;datalist id="urlsxx"&gt;
  &lt;option&gt;https://developer.mozilla.org&lt;/option&gt;
  &lt;option&gt;https://caniuse.com/&lt;/option&gt;
  &lt;option&gt;https://mozilla.com&lt;/option&gt;
  &lt;option&gt;https://mdn.github.io&lt;/option&gt;
  &lt;option&gt;https://www.youtube.com/user/firefoxchannel&lt;/option&gt;
&lt;/datalist&gt;

&lt;p&gt;
  &lt;label for="textx"&gt;Text&lt;/label&gt;
  &lt;input type="text" list="fruitsxx" id="textx"/&gt;
&lt;/p&gt;
&lt;p&gt;
  &lt;label for="colorx"&gt;Color&lt;/label&gt;
  &lt;input type="color" list="colorsxx" id="colorx"/&gt;
&lt;/p&gt;
&lt;p&gt;
  &lt;label for="rangex"&gt;Range&lt;/label&gt;
  &lt;input type="range" min="0" max="64" list="numbersxx" id="rangex"/&gt;
&lt;/p&gt;
&lt;p&gt;
  &lt;label for="numberx"&gt;Number&lt;/label&gt;
  &lt;input type="number" min="0" max="64" list="numbersxx" id="numberx"/&gt;
&lt;/p&gt;
&lt;p&gt;
  &lt;label for="urlx"&gt;URL&lt;/label&gt;
  &lt;input type="url" list="urlsxx" id="urlx"/&gt;
&lt;/p&gt;
</pre>

<p>{{EmbedLiveSample("datalist",400,275,"","", "nobutton")}}</p>

<p>It is valid on <code>text</code>, <code>search</code>, <code>url</code>, <code>tel</code>, <code>email</code>, <code>date</code>, <code>month</code>, <code>week</code>, <code>time</code>, <code>datetime-local</code>, <code>number</code>, <code>range</code>, and <code>color</code>. </p>

<p>Per the specifications, the <code>list</code> attribute is not supported by the <code>hidden</code>, <code>password</code>, <code>checkbox</code>, <code>radio</code>, <code>file</code>, or any of the button types.</p>

<p>Depending on the browser, the user may see a custom color palette suggested, tic marks along a range, or even a input that opens like a select but allows for non-listed values. Check out the <a href="/zh-CN/docs/Web/HTML/Element/datalist#Browser_compatibility">browser compatibility table</a> for the other input types.</p>

<p>See the {{htmlelement('datalist')}} element.</p>

<dl>
 <dt>{{ htmlattrdef("max") }}</dt>
 <dd>此项目的最大（数字或日期时间）值，且不得小于其最小值（<strong>min</strong> 属性值）。</dd>
 <dt>{{ htmlattrdef("maxlength") }}</dt>
 <dd>如果 <strong>type</strong> 的值是 text、email、search、password、tel 或 url，那么这个属性指明了用户最多可以输入的字符个数（按照 Unicode 编码方式计数）；对于其他类型的输入框，该属性被忽略。它可以大于 <strong>size</strong> 属性的值。如果不指定这个属性，那么用户可以输入任意多的字符。如果指定为一个负值，那么元素表现出默认行为，即用户可以输入任意多的字符。本属性的约束规则，仅在元素的 value 属性发生变化时才会执行。译者注：ie10+</dd>
 <dt>{{ htmlattrdef("min") }}</dt>
 <dd>此项目的最小（数字或日期时间）值，且不得大于其最大值（<strong>max</strong> 属性值）。</dd>
 <dt>{{htmlattrdef("minlength")}}</dt>
 <dd>
 <p>Valid for <code>text</code>, <code>search</code>, <code>url</code>, <code>tel</code>, <code>email</code>, and <code>password</code>, it defines the minimum number of characters (as UTF-16 code units) the user can enter into the entry field. This must be an non-negative integer value smaller than or equal to the value specified by <code>maxlength</code>. If no <code>minlength</code> is specified, or an invalid value is specified, the input has no minimum length.</p>

 <p>The input will fail <a href="/zh-CN/docs/Web/Guide/HTML/HTML5/Constraint_validation">constraint validation</a> if the length of the text entered into the field is fewer than <code>minlength</code> UTF-16 code units long, preventing form submission. See <a href="#client-side_validation">Client-side validation</a> for more information.</p>
 </dd>
 <dt>{{ htmlattrdef("multiple") }}</dt>
 <dd>这个 <strong>Boolean</strong> 属性指明了用户能否输入多个值，仅在 <strong>type</strong> 属性为 email 或 file 时生效，否则将被忽略。</dd>
 <dt>{{ htmlattrdef("name") }}</dt>
 <dd>控件的名称，与表单数据一起提交。</dd>
 <dt>{{ htmlattrdef("pattern") }}</dt>
 <dd>检查控件值的正则表达式。pattern 必须匹配整个值，而不仅仅是某些子集。使用 title 属性来描述帮助用户的模式。仅在 <strong>type</strong> 属性的值为 text、search、tel、url 或 email 时生效，否则将被忽略。译者注：ie10+</dd>
 <dt>{{ htmlattrdef("placeholder") }}</dt>
 <dd>提示用户输入框的作用。用于提示的占位符文本不能包含回车或换行。仅在 <strong>type</strong> 属性为 text、search、tel、url 或 email 时生效，否则将被忽略。
 <div class="note"><p><strong>备注</strong>：请不要用 <code>placeholder</code> 属性替换 {{ HTMLElement("label") }} 元素。他们的作用不同: {{ HTMLElement("label") }} 属性描述表单元素的角色; 也就是说，它展示预期的信息，而 <code>placeholder</code> 属性是提示用户内容的输入格式。某些情况下 <code>placeholder</code> 属性对用户不可见，所以当没有它时也需要保证 form 能被理解。</p></div>
 </dd>
 <dt>{{ htmlattrdef("readonly") }}</dt>
 <dd>这个布尔属性用于指明用户无法修改控件的值。
 <p>如果控件的 <strong>type</strong> 属性为 hidden、range、color、checkbox、radio、file，此属性将被忽略。</p>
 </dd>
 <dt>{{ htmlattrdef("required") }}</dt>
 <dd>这个属性指定用户在提交表单之前必须为该元素填充值。当 type 属性是 hidden、image 或者按钮类型（submit、reset、button）时不可使用。 {{ cssxref(":optional") }} 和 {{ cssxref(":required") }} CSS 伪元素的样式将可以被该字段应用作外观。</dd>
 <dt>{{ htmlattrdef("selectionDirection") }}</dt>
 <dd>The direction in which selection occurred. This is "forward" if the selection was made from left-to-right in an LTR locale or right-to-left in an RTL locale, or "backward" if the selection was made in the opposite direction. This can be "none" if the selection direction is unknown.</dd>
 <dt>{{ htmlattrdef("size") }}</dt>
 <dd>控件的初始大小。以像素为单位。但当 <strong>type</strong> 属性为 text 或 password 时，它表示输入的字符的长度。从 HTML5 开始，此属性仅在 <strong>type</strong> 属性为 text、search、tel、url、email 或 password 时生效，否则将被忽略。此外，它的值必须大于 0。如果未指定大小，则使用默认值 20。HTML5 概述 "用户代理应该确保至少大部分字符是可见的"，但是不同的字符的用不同的字体表示可能会导致宽度不同。在某些浏览器中，一串带有 x 的字符即使定义了到 x 的大小也将显示不完整。</dd>
 <dt>{{ htmlattrdef("spellcheck") }}</dt>
 <dd>将此属性的值设置为 <code>true</code> 表示元素需要检查其拼写和语法。值为 <code>default</code> 表示该元素将根据默认行为进行操作，可能基于父元素自己的 <code>spellcheck</code> 值。值为 <code>false</code> 表示不应该检查元素</dd>
 <dt>{{ htmlattrdef("src") }}</dt>
 <dd>如果 <strong>type</strong> 属性的值是 image，这个属性指定了按钮图片的路径; 否则将被忽视。</dd>
 <dt>{{ htmlattrdef("step") }}</dt>
 <dd>使用 <strong>min</strong> 和 <strong>max</strong> 属性来限制可以设置数字或日期时间值的增量。它可以是任意字符串或是正浮点数。如果此属性未设置为任何，则控件仅接受大于最小步长值的倍数的值。</dd>
 <dt>{{ htmlattrdef("tabindex") }}</dt>
 <dd>元素在当前文档的 Tab 导航顺序中的位置。</dd>
 <dt>{{htmlattrdef('title')}}</dt>
 <dd>
 <p>Global attribute valid for all elements, including all input types, containing a text representing advisory information related to the element it belongs to. Such information can typically, but not necessarily, be presented to the user as a tooltip. The title should NOT be used as the primary explanation of the purpose of the form control. Instead, use the {{htmlelement('label')}} element with a <code>for</code> attribute set to the form control's {{htmlattrdef('id')}} attribute. See <a href="#labels">Labels</a> below.</p>
 </dd>
 <dt>{{ htmlattrdef("type") }}</dt>
 <dd>要呈现的控件类型。有关各个类型的信息，请参阅 <a href="#&lt;input&gt;_types">Form &lt;input&gt; types</a>，其中包含指向每个类型的更多信息的链接。</dd>
 <dt>{{ htmlattrdef("usemap") }} {{Deprecated_Inline}}</dt>
 <dd>作为图像映射的 {{ HTMLElement("map") }} 元素的名称。</dd>
 <dt>{{ htmlattrdef("value") }}</dt>
 <dd>控件的初始值。此属性是可选的，除非 <strong>type</strong> 属性是 <code>radio</code> 或 <code>checkbox</code>。注意，当重新加载页面时，如果在重新加载之前更改了值，<a href="https://bugzilla.mozilla.org/show_bug.cgi?id=46845#c186">Gecko 和 IE 将忽略 HTML 源代码中指定的值</a>。</dd>
 <dt>{{ htmlattrdef("width") }} </dt>
 <dd>如果 <strong>type</strong> 属性的值是 image，这个属性定义了按钮图片的宽度。</dd>
 <dt>
 <h3 id="非标准_&lt;input>_属性">非标准 <code>&lt;input&gt;</code> 属性</h3>
 </dt>
 <dt>{{htmlattrdef("autocorrect")}} {{non-standard_inline}}</dt>
 <dd>This is a non-standard attribute supported by Safari that is used to control whether autocorrection should be enabled when the user is entering/editing the text value of the <code>&lt;input&gt;</code>. Possible attribute values are:
 <ul>
  <li><code>on</code>：Enable autocorrection.</li>
  <li><code>off</code>：Disable autocorrection.</li>
 </ul>
 <a href="https://developer.apple.com/library/safari/documentation/AppleApplications/Reference/SafariHTMLRef/Articles/Attributes.html#//apple_ref/doc/uid/TP40008058-autocorrect"><code>autocorrect</code> documentation</a> in the Safari HTML Reference.</dd>
 <dt>{{ htmlattrdef("mozactionhint") }} {{ non-standard_inline() }}</dt>
 <dd>Specifies an "action hint" used to determine how to label the enter key on mobile devices with virtual keyboards. Supported values are <code>go</code>, <code>done</code>, <code>next</code>, <code>search</code>, and <code>send</code>; these automatically get mapped to the appropriate string (and are case-insensitive).</dd>
 <dt>{{htmlattrdef("autocapitalize")}} {{non-standard_inline}}</dt>
 <dd>This is a nonstandard attribute used by iOS Safari Mobile which controls whether and how the text value should be automatically capitalized as it is entered/edited by the user. The non-deprecated values are available in iOS 5 and later. Possible values are:
 <ul>
  <li><code>none</code>：Completely disables automatic capitalization</li>
  <li><code>sentences</code>：Automatically capitalize the first letter of sentences.</li>
  <li><code>words</code>：Automatically capitalize the first letter of words.</li>
  <li><code>characters</code>：Automatically capitalize all characters.</li>
  <li><code>on</code>：{{deprecated_inline()}} Deprecated since iOS 5.</li>
  <li><code>off</code>：{{deprecated_inline()}} Deprecated since iOS 5.</li>
 </ul>
 <a href="https://developer.apple.com/library/safari/documentation/AppleApplications/Reference/SafariHTMLRef/Articles/Attributes.html#//apple_ref/doc/uid/TP40008058-autocapitalize"><code>autocapitalize</code> documentation in the Safari HTML Reference</a></dd>
 <dt>{{htmlattrdef("incremental")}} {{non-standard_inline}}</dt>
 <dd>This is a nonstandard attribute supported by WebKit (Safari) and Blink (Chrome) that only applies when the <strong>type</strong> is <code>search</code>. If the attribute is present, regardless of what its value is, the <code>&lt;input&gt;</code> fires <a href="https://developer.mozilla.org/en-US/docs/Web/Events/search"><code>search</code></a> events as the user edits the text value. The event is only fired after an implementation-defined timeout has elapsed since the most recent keystroke, and new keystrokes reset the timeout. In other words, the event firing is debounced. If the attribute is absent, the <a href="https://developer.mozilla.org/en-US/docs/Web/Events/search"><code>search</code></a> event is only fired when the user explicitly initiates a search (e.g. by pressing the Enter key while within field). <a href="https://developer.apple.com/library/safari/documentation/AppleApplications/Reference/SafariHTMLRef/Articles/Attributes.html#//apple_ref/doc/uid/TP40008058-incremental"><code>incremental</code> documentation in the Safari HTML Reference</a></dd>
 <dt>{{htmlattrdef("mozactionhint")}} {{non-standard_inline}}</dt>
 <dd>Specifies an "action hint" used to determine how to label the enter key on mobile devices with virtual keyboards. Supported values are <code>go</code>, <code>done</code>, <code>next</code>, <code>search</code>, and <code>send</code>. These automatically get mapped to the appropriate string and are case-insensitive.</dd>
 <dt>{{htmlattrdef("results")}} {{non-standard_inline}}</dt>
 <dd>This is a nonstandard attribute supported by Safari that only applies when the <strong>type</strong> is <code>search</code>. It is used to control the maximum number of entries that should be displayed in the <code>&lt;input&gt;</code>'s native dropdown list of past search queries. Its value should be a nonnegative decimal integer.</dd>
 <dt>{{htmlattrdef("webkitdirectory")}} {{non-standard_inline}}</dt>
 <dd>This Boolean attribute indicates if the selector used when the <strong>type</strong> attribute is <code>file</code>has to allow for the selection of directories only.</dd>
 <dt>{{htmlattrdef("x-moz-errormessage")}} {{non-standard_inline}}</dt>
 <dd>This Mozilla extension allows you to specify the error message to display when a field doesn't successfully validate.</dd>
</dl>

<h2 id="Methods">Methods</h2>

<p>The following methods are provided by the <a href="/en-US/docs/Web/API/HTMLInputElement"><code>HTMLInputElement</code></a> interface which represents <code>&lt;input&gt;</code> elements in the DOM. Also available are those methods specified by the parent interfaces, <a href="/en-US/docs/Web/API/HTMLElement"><code>HTMLElement</code></a>, <a href="/en-US/docs/Web/API/Element"><code>Element</code></a>, <a href="/en-US/docs/Web/API/Node"><code>Node</code></a>, and <a href="/en-US/docs/Web/API/EventTarget"><code>EventTarget</code></a>.</p>

<dl>
 <dt><a href="/en-US/docs/Web/API/HTMLInputElement/checkValidity"><code>checkValidity()</code></a></dt>
 <dd>Immediately runs the validity check on the element, triggering the document to fire the <a href="/en-US/docs/Web/API/HTMLInputElement/invalid_event"><code>invalid</code></a> event at the element if the value isn't valid.</dd>
 <dt><a href="/en-US/docs/Web/API/HTMLFormElement/reportValidity"><code>reportValidity()</code></a></dt>
 <dd>Returns <code>true</code> if the element's value passes validity checks; otherwise, returns <code>false</code>.</dd>
 <dt><a href="/en-US/docs/Web/API/HTMLInputElement/select"><code>select()</code></a></dt>
 <dd>Selects the entire content of the <code>&lt;input&gt;</code> element, if the element's content is selectable. For elements with no selectable text content (such as a visual color picker or calendar date input), this method does nothing.</dd>
 <dt><a href="/en-US/docs/Web/API/HTMLInputElement/setCustomValidity"><code>setCustomValidity()</code></a></dt>
 <dd>Sets a custom message to display if the input element's value isn't valid.</dd>
 <dt><a href="/en-US/docs/Web/API/HTMLInputElement/setRangeText"><code>setRangeText()</code></a></dt>
 <dd>Sets the contents of the specified range of characters in the input element to a given string. A <code>selectMode</code> parameter is available to allow controlling how the existing content is affected.</dd>
 <dt><a href="/en-US/docs/Web/API/HTMLInputElement/setSelectionRange"><code>setSelectionRange()</code></a></dt>
 <dd>Selects the specified range of characters within a textual input element. Does nothing for inputs which aren't presented as text input fields.</dd>
 <dt><a href="/en-US/docs/Web/API/HTMLInputElement/stepDown"><code>stepDown()</code></a></dt>
 <dd>Decrements the value of a numeric input by one, by default, or by the specified number of units.</dd>
 <dt><a href="/en-US/docs/Web/API/HTMLInputElement/stepUp"><code>stepUp()</code></a></dt>
 <dd>Increments the value of a numeric input by one or by the specified number of units.</dd>
</dl>

<h2 id="CSS">CSS</h2>

<p>Inputs, being replaced elements, have a few features not applicable to non form elements. There are CSS selectors that can specification target form controls based on their UI features, also known as UI pseudo-classes. The input element can also be targeted by type with attribute selectors. There are some properties that are especially useful as well.</p>

<h3 id="UI_pseudo-classes">UI pseudo-classes</h3>

<table class="standard-table">
 <caption>Captions super relevant to the <a href="/en-US/docs/Web/HTML/Element/input"><code>&lt;input&gt;</code></a> element:</caption>
 <thead>
  <tr>
   <th>Pseudo-class</th>
   <th>Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><a href="/en-US/docs/Web/CSS/:enabled"><code>:enabled</code></a></td>
   <td>Any currently enabled element that can be activated (selected, clicked on, typed into, etc.) or accept focus and also has a disabled state, in which it can't be activated or accept focus.</td>
  </tr>
  <tr>
   <td><a href="/en-US/docs/Web/CSS/:disabled"><code>:disabled</code></a></td>
   <td>Any currently disabled element that has an enabled state, meaing it otherwise could be activated (selected, clicked on, typed into, etc.) or accept focus were it not disabled.</td>
  </tr>
  <tr>
   <td><a href="/en-US/docs/Web/CSS/:read-only"><code>:read-only</code></a></td>
   <td>Element not editable by the user</td>
  </tr>
  <tr>
   <td><a href="/en-US/docs/Web/CSS/:read-write"><code>:read-write</code></a></td>
   <td>Element that is editable by the user.</td>
  </tr>
  <tr>
   <td><a href="/en-US/docs/Web/CSS/:placeholder-shown"><code>:placeholder-shown</code></a></td>
   <td>Element that is currently displaying <a href="/zh-CN/docs/Web/HTML/Element/input#attr-placeholder">placeholder text</a>, including input elements with the <a href="#htmlattrdefplaceholder">placeholder</a> attribute present that has, as of yet, no value.</td>
  </tr>
  <tr>
   <td><a href="/en-US/docs/Web/CSS/:default"><code>:default</code></a></td>
   <td>Form elements that are the default in a group of related elements. Matches <a href="/en-US/docs/Web/HTML/Element/input/checkbox">checkbox</a> and <a href="/en-US/docs/Web/HTML/Element/input/radio">radio</a> input types that were checked on page load or render.</td>
  </tr>
  <tr>
   <td><a href="/en-US/docs/Web/CSS/:checked"><code>:checked</code></a></td>
   <td>Matches <a href="/en-US/docs/Web/HTML/Element/input/checkbox">checkbox</a> and <a href="/en-US/docs/Web/HTML/Element/input/radio">radio</a> input types that are currently checked (and the (<a href="/en-US/docs/Web/HTML/Element/option"><code>&lt;option&gt;</code></a> in a <a href="/en-US/docs/Web/HTML/Element/select"><code>&lt;select&gt;</code></a> that is currently selected).</td>
  </tr>
  <tr>
   <td><a href="/en-US/docs/Web/CSS/:indeterminate"><code>:indeterminate</code></a></td>
   <td><a href="/en-US/docs/Web/HTML/Element/input/checkbox">checkbox</a> elements whose indeterminate property is set to true by JavaScript, <a href="/en-US/docs/Web/HTML/Element/input/radio">radio</a> elements, when all radio buttons with the same name value in the form are unchecked, and <a href="/en-US/docs/Web/HTML/Element/progress"><code>&lt;progress&gt;</code></a> elements in an indeterminate state</td>
  </tr>
  <tr>
   <td><a href="/en-US/docs/Web/CSS/:valid"><code>:valid</code></a></td>
   <td>Form controls that can have constraint validation applied and are currently valid.</td>
  </tr>
  <tr>
   <td><a href="/en-US/docs/Web/CSS/:invalid"><code>:invalid</code></a></td>
   <td>Form controls that have constraint validation applied and are currently not valid. Matches a form control whose value doesn't match the constraints set on it by it's attributes, such as <a href="#htmlattrdefrequired">required</a>, <a href="#htmlattrdefpattern">pattern</a> , <a href="#htmlattrdefstep">step</a> and <a href="#htmlattrdefmax">max</a>.</td>
  </tr>
  <tr>
   <td><a href="/en-US/docs/Web/CSS/:in-range"><code>:in-range</code></a></td>
   <td>A non-empty input whose current value is within the range limits specified by the <a href="#htmlattrdefmin">min</a> and <a href="#htmlattrdefmax">max</a> attributes and the <a href="#htmlattrdefstep">step</a> .</td>
  </tr>
  <tr>
   <td><a href="/en-US/docs/Web/CSS/:out-of-range"><code>:out-of-range</code></a></td>
   <td>A non-empty input whose current value is NOT within the range limits specified by the <a href="#htmlattrdefmin">min</a> and <a href="#htmlattrdefmax">max</a> attributes or does not adher to the <a href="#htmlattrdefstep">step</a> constraint.</td>
  </tr>
  <tr>
   <td><a href="/en-US/docs/Web/CSS/:placeholder-shown"><code>:placeholder-shown</code></a></td>
   <td>An <a href="/en-US/docs/Web/HTML/Element/input"><code>&lt;input&gt;</code></a> or <a href="/en-US/docs/Web/HTML/Element/textarea"><code>&lt;textarea&gt;</code></a> element that is currently displaying placeholder text.</td>
  </tr>
  <tr>
   <td><a href="/en-US/docs/Web/CSS/:required"><code>:required</code></a></td>
   <td><a href="/en-US/docs/Web/HTML/Element/input"><code>&lt;input&gt;</code></a>, <a href="/en-US/docs/Web/HTML/Element/select"><code>&lt;select&gt;</code></a>, or <a href="/en-US/docs/Web/HTML/Element/textarea"><code>&lt;textarea&gt;</code></a> element that has the <code><a href="/en-US/docs/Web/HTML/Element/input#attr-required">required</a></code> attribute set on it. Only matches elements that can be required. The attribute included on a non-requirable element will not make for a match.</td>
  </tr>
  <tr>
   <td><a href="/en-US/docs/Web/CSS/:optional"><code>:optional</code></a></td>
   <td><a href="/en-US/docs/Web/HTML/Element/input"><code>&lt;input&gt;</code></a>, <a href="/en-US/docs/Web/HTML/Element/select"><code>&lt;select&gt;</code></a>, or <a href="/en-US/docs/Web/HTML/Element/textarea"><code>&lt;textarea&gt;</code></a> element that does NOT have the <code><a href="/en-US/docs/Web/HTML/Element/input#attr-required">required</a></code> attribute set on it. Does not match elements that can't be required.</td>
  </tr>
  <tr>
   <td><a href="/en-US/docs/Web/CSS/:blank"><code>:blank</code></a></td>
   <td><a href="/en-US/docs/Web/HTML/Element/input"><code>&lt;input&gt;</code></a> and <a href="/en-US/docs/Web/HTML/Element/textarea"><code>&lt;textarea&gt;</code></a> elements that currently have no value.</td>
  </tr>
  <tr>
   <td><a href="/en-US/docs/Web/CSS/:user-invalid"><code>:user-invalid</code></a></td>
   <td>Similar to <code>:invalid</code>, but is activated on blur. Matches invalid input but only after the user interaction, such as by focusing on the control, leaving the control, or attempting to submit the form containing the invalid control.</td>
  </tr>
 </tbody>
</table>

<div id="checkbox_label">
<h4 id="Examples">Examples</h4>

<p>We can style a checkbox label based on whether the checkbox is checked or not. In this example, we are styling the <a href="/en-US/docs/Web/CSS/color"><code>color</code></a> and <a href="/en-US/docs/Web/CSS/font-weight"><code>font-weight</code></a> of the <a href="/en-US/docs/Web/HTML/Element/label"><code>&lt;label&gt;</code></a> that comes immediately after a checked input. We haven't applied any styles if the <code>input</code> is not checked.</p>

<pre class="brush: html hidden">&lt;input id="checkboxInput" type="checkbox"&gt;
&lt;label for="checkboxInput"&gt;Toggle the checkbox on and off&lt;/label&gt;
</pre>

<pre class="brush: css">input:checked + label {
  color: red;
  font-weight: bold;
}
</pre>
</div>

<h3 id="Attribute_selectors">Attribute selectors</h3>

<p>It is possible to target different types of form controls based on their <a href="#htmlattrdeftype">type</a> using <a href="/en-US/docs/Learn/CSS/Building_blocks/Selectors/Attribute_selectors">attribute selectors</a>. CSS attribute selectors match elements based on either just the presence of a attribute or the value of a given attribute.</p>

<pre class="brush: css">/* matches a password input */
input[type="password"] {}

/* matches a form control whose valid values are limited to a range of values*/
input[min][max] {}

/* matches a form control with with a pattern attribute */
 input[pattern] {}</pre>

<h3 id="placeholder">::placeholder</h3>

<p>By default, the appearance of placeholder text is a translucent or light gray. The <a href="/en-US/docs/Web/CSS/::placeholder"><code>::placeholder</code></a> pseudo-element is the input's <a href="/en-US/docs/Web/HTML/Forms_in_HTML#The_placeholder_attribute">placeholder text</a>. It can be styled with a limited subset of CSS properties.</p>

<pre class="brush: css no-line-numbers">::placeholder {
  color: blue;
}</pre>

<p>Only the subset of CSS properties that apply to the <a href="/en-US/docs/Web/CSS/::first-line"><code>::first-line</code></a> pseudo-element can be used in a rule using <code>::placeholder</code> in its selector.</p>

<h3 id="appearance"><a href="/en-US/docs/Web/CSS/appearance"><code>appearance</code></a></h3>

<p>The <a href="/en-US/docs/Web/CSS/appearance"><code>appearance</code></a> property enables the displaying of (almost) any element as a platform-native style based on the operating system's theme as well as the removal of any platform-native styling with the <code>none</code> value.</p>

<p>You could make a <code>&lt;div&gt;</code> look like a radio button with <code>div {appearance: radio;} </code>or a radio look like a checkbox with <code>[type="checkbox] {appearance: checkbox;}</code>, but don't.</p>

<p>Setting <code>appearance: none</code> removes platform native borders, but not functionality.</p>

<h3 id="caret-color"><a href="/en-US/docs/Web/CSS/caret-color"><code>caret-color</code></a></h3>

<p>A property specific to text entry-related elements is the CSS <a href="/en-US/docs/Web/CSS/caret-color"><code>caret-color</code></a> property, which lets you set the color used to draw the text input caret:</p>

<h4 id="HTML">HTML</h4>

<pre class="brush: html">&lt;label for="textInput"&gt;Note the red caret:&lt;/label&gt;
&lt;input id="textInput" class="custom" size="32"&gt;
</pre>

<h4 id="CSS_2">CSS</h4>

<pre class="brush: css">
input.custom {
  caret-color: red;
  font: 16px "Helvetica", "Arial", "sans-serif"
}
</pre>

<h4 id="Result">Result</h4>

<h3 id="object-position_and_object-fit"><a href="/en-US/docs/Web/CSS/object-position"><code>object-position</code></a> and <a href="/en-US/docs/Web/CSS/object-fit"><code>object-fit</code></a></h3>

<p>In certain cases (typically involving non-textual inputs and specialized interfaces), the <code>&lt;input&gt;</code> element is a <a href="/en-US/docs/Web/CSS/Replaced_element">replaced element</a>. When it is, the position and size of the element's size and positioning within its frame can be adjusted using the CSS <a href="/en-US/docs/Web/CSS/object-position"><code>object-position</code></a> and <a href="/en-US/docs/Web/CSS/object-fit"><code>object-fit</code></a> properties</p>

<h3 id="Styling">Styling</h3>

<p>For more information about adding color to elements in HTML, see:</p>

<ul>
 <li><a href="/en-US/docs/Web/HTML/Applying_color">Applying color to HTML elements using CSS</a>.</li>
</ul>

<p>Also see:</p>

<ul>
 <li><a href="/en-US/docs/Learn/HTML/Forms/Styling_HTML_forms">Styling HTML forms,</a> <a href="/en-US/docs/Learn/HTML/Forms/Advanced_styling_for_HTML_forms">advanced styling for HTML forms</a>, and</li>
 <li>the<a href="/en-US/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets"> compatibility table of CSS properties</a>.</li>
</ul>

<h2 id="Additional_Features">Additional Features</h2>

<h3 id="Labels">Labels</h3>

<p>Labels are needed to associate assistive text with an <code>&lt;input&gt;</code>. The <a href="/en-US/docs/Web/HTML/Element/label"><code>&lt;label&gt;</code></a> element provides explanatory information about a form field that is <em>always</em> appropriate (aside from any layout concerns you have). It's never a bad idea to use a <code>&lt;label&gt;</code> to explain what should be entered into an <code>&lt;input&gt;</code> or <a href="/en-US/docs/Web/HTML/Element/textarea"><code>&lt;textarea&gt;</code></a>.</p>

<h4 id="Associated_labels">Associated labels</h4>

<p>The semantic pairing of <code>&lt;input&gt;</code> and <code>&lt;label&gt;</code> elements is useful for assistive technologies such as screen readers. By pairing them using the <code>&lt;label&gt;</code>'s <code><a href="/en-US/docs/Web/HTML/Element/label#attr-for">for</a></code> attribute, you bond the label to the input in a way that lets screen readers describe inputs to users more precisely.</p>

<p>It does not suffice to have plain text adjacent to the <code>&lt;input&gt;</code> element,. Rather, usability and accessibility requires the inclusion of either implicit or explicit <a href="/en-US/docs/Web/HTML/Element/label"><code>&lt;label&gt;</code></a>:</p>

<pre class="brush: html">&lt;!-- inaccessible --&gt;
&lt;p&gt;Enter your name: &lt;input id="name" type="text" size="30"&gt;&lt;/p&gt;

&lt;!-- implicit label --&gt;
&lt;p&gt;&lt;label&gt;Enter your name: &lt;input id="name" type="text" size="30"&gt;&lt;/label&gt;&lt;/p&gt;

&lt;!-- explicit label --&gt;
&lt;p&gt;&lt;label for="name"&gt;Enter your name: &lt;/label&gt;&lt;input id="name" type="text" size="30"&gt;&lt;/p&gt;</pre>

<p>The first example is inaccessible: no relationship exists between the prompt and the <code>&lt;input&gt;</code> element.</p>

<p>In addition to an accessible name, the label provides a larger 'hit' area for mouse and touch screen users to click on or touch. By pairing a <code>&lt;label&gt;</code> with an <code>&lt;input&gt;</code>, clicking on either one will focus the <code>&lt;input&gt;</code>. If you use plain text to "label" your input, this won't happen. Having the prompt part of the activation area for the input is helpful for people with motor control conditions.</p>

<p>As web developers, it's important that we never assume that people will know all the things that we know. The diversity of people using the web—and by extension your web site—practically guarantees that some of your site's visitors will have some variation in thought processes and/or circumstances that leads them to interpret your forms very differently from you without clear and properly-presented labels.</p>

<h4 id="Placeholders_are_not_accessible">Placeholders are not accessible</h4>

<p>The <code><a href="/en-US/docs/Web/HTML/Element/input#attr-placeholder">placeholder</a></code> attribute lets you specify a text that appears within the <code>&lt;input&gt;</code> element's content area itself when empty. The placeholder should never be required in order to understand your forms. It is not a label, and should not be used as a substitute, because it isn't. The placeholder is used to show an example input, not an explanation or prompt. Not only is the placeholder not accessible to screen readers, but once the user enters any text into the form control, or if the form control already has a value, there is no placeholder. Browsers with automatic page translation features may skip over attributes when translating, meaning the <code>placeholder</code> may not get translated.</p>

<div class="blockIndicator note">
<p>Don't use the <code><a href="/en-US/docs/Web/HTML/Element/input#attr-placeholder">placeholder</a></code> attribute if you can avoid it. If you need to label an <code>&lt;input&gt;</code> element, use the <a href="/en-US/docs/Web/HTML/Element/label"><code>&lt;label&gt;</code></a> element</p>
</div>

<h3 id="Client-side_validation">Client-side validation</h3>

<p>In addition to using CSS to style inputs based on the <a href="/en-US/docs/Web/CSS/:valid"><code>:valid</code></a> or <a href="/en-US/docs/Web/CSS/:invalid"><code>:invalid</code></a> UI states based on the current state of each input, as noted in the <a href="#UI_pseudo-classes">UI pseudo-classes</a> section above, the browser provides for client-side validation on (attempted) form submission. On form submission, if their is a form control that fails constraint validation, supporting browsers will display an error message on the first invalid form control; displaying a default message based on the error type, or a message set by you.</p>

<p>Some input types and other attributes place limits on what values are valid for a given input. For example, <code>&lt;input type="number" min="2" max="10" step="2"&gt;</code> means only the number 2, 4, 6, 8, or 10 are valid. Several errors could occur, including a <code>rangeUnderflow</code> error if the value is less than 2, <code>rangeOverflow</code> if greater than 10, <code>stepMismatch</code> if the value is a number between 2 and 10, but not an even integer (does not match the requirements of the <code>step</code> attribute), or <code>typeMismatch</code> if the value is not a number.</p>

<p>Specific attributes and their values can lead to specific error <a href="/en-US/docs/Web/API/ValidityState"><code>ValidityState</code></a></p>

<table class="standard-table">
 <caption>Validity object errors depend on the <a href="/en-US/docs/Web/HTML/Element/input"><code>&lt;input&gt;</code></a> attributes and their values:</caption>
 <thead>
  <tr>
   <th scope="col">Attribute</th>
   <th scope="col">Relevent property</th>
   <th scope="col">Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><a href="#htmlattrdefmax">max</a></td>
   <td><a href="/en-US/docs/Web/API/ValidityState/rangeOverflow"><code>validityState.rangeOverflow</code></a></td>
   <td>Occurs when the value is greater than the maximum value as defined by the <code>max</code> attribute</td>
  </tr>
  <tr>
   <td><a href="#htmlattrdefmaxlength">maxlength</a></td>
   <td><a href="/en-US/docs/Web/API/ValidityState/tooLong"><code>validityState.tooLong</code></a></td>
   <td>Occurs when the number of characters is greater than the number allowed by the <code>maxlength</code> property</td>
  </tr>
  <tr>
   <td><a href="#htmlattrdefmin">min</a></td>
   <td><a href="/en-US/docs/Web/API/ValidityState/rangeUnderflow"><code>validityState.rangeUnderflow</code></a></td>
   <td>Occurs when the value is less than the minimum value as defined by the <code>min</code> attribute</td>
  </tr>
  <tr>
   <td><a href="#htmlattrdefminlength">minlength</a></td>
   <td><a href="/en-US/docs/Web/API/ValidityState/tooShort"><code>validityState.tooShort</code></a></td>
   <td>Occurs when the number of characters is less than the number required by the <code>minlength</code> property</td>
  </tr>
  <tr>
   <td><a href="#htmlattrdefpattern">pattern</a></td>
   <td><a href="/en-US/docs/Web/API/ValidityState/patternMismatch"><code>validityState.patternMismatch</code></a></td>
   <td>Occurs when a pattern attribute is included with a valid regular expression and the <code>value</code> does not match it.</td>
  </tr>
  <tr>
   <td><a href="#htmlattrdefrequired">required</a></td>
   <td><a href="/en-US/docs/Web/API/ValidityState/valueMissing"><code>validityState.valueMissing</code></a></td>
   <td>Occurs when the <code>required</code> attribute is present but the value is <code>null</code> or radio or checkbox is not checked.</td>
  </tr>
  <tr>
   <td><a href="#htmlattrdefstep">step</a></td>
   <td><a href="/en-US/docs/Web/API/ValidityState/stepMismatch"><code>validityState.stepMismatch</code></a></td>
   <td>The value doesn't match the step increment. Increment default is <code>1</code>, so only integers are valid on<code> type="number"</code> is step is not included. <code>step="any"</code> will never throw this error.</td>
  </tr>
  <tr>
   <td><a href="#htmlattrdeftyoe">type</a></td>
   <td><a href="/en-US/docs/Web/API/ValidityState/typeMismatch"><code>validityState.typeMismatch</code></a></td>
   <td>Occurs when the value is not of the correct type, for example a email does not contain an <code>@</code> or a url doesn't contain a protocol.</td>
  </tr>
 </tbody>
</table>

<p>If a form control doesn't have the required attribute, no value, or an empty string, is not invalid. Even if the above attributes are present, with the exception of <code>'required'</code>, and empty string will not lead to an error.</p>

<p>We can set limits on what values we accept, and supporting browsers will natively validate these form values and alert the user if there is a mistake when the form is submitted.</p>

<p>In addition to the errors described in the table above, the <code>validityState</code> interface contains the <code>badInput</code>, <code>valid</code>, and <code>customError</code> boolean readonly properties. The validity object includes:</p>

<ul>
 <li><a href="/en-US/docs/Web/API/ValidityState/valueMissing"><code>validityState.valueMissing</code></a></li>
 <li><a href="/en-US/docs/Web/API/ValidityState/typeMismatch"><code>validityState.typeMismatch</code></a></li>
 <li><a href="/en-US/docs/Web/API/ValidityState/patternMismatch"><code>validityState.patternMismatch</code></a></li>
 <li><a href="/en-US/docs/Web/API/ValidityState/tooLong"><code>validityState.tooLong</code></a></li>
 <li><a href="/en-US/docs/Web/API/ValidityState/tooShort"><code>validityState.tooShort</code></a></li>
 <li><a href="/en-US/docs/Web/API/ValidityState/rangeUnderflow"><code>validityState.rangeUnderflow</code></a></li>
 <li><a href="/en-US/docs/Web/API/ValidityState/rangeOverflow"><code>validityState.rangeOverflow</code></a></li>
 <li><a href="/en-US/docs/Web/API/ValidityState/stepMismatch"><code>validityState.stepMismatch</code></a></li>
 <li><a href="/en-US/docs/Web/API/ValidityState/badInput"><code>validityState.badInput</code></a></li>
 <li><a href="/en-US/docs/Web/API/ValidityState/valid"><code>validityState.valid</code></a></li>
 <li><a href="/en-US/docs/Web/API/ValidityState/customError"><code>validityState.customError</code></a></li>
</ul>

<p>For each of these Boolean properties, a value of <code>true</code> indicates that the specified reason validation may have failed is true, with the exception of the <code>valid</code> property, which is <code>true</code> if the element's value obeys all constraints.</p>

<p>If there is an error, supporting browsers will both alert the user and prevent the form from being submitted. A word of caution: if a custom error is set to a truthy value (anything other than the empty string or <code>null</code>), the form will be be prevented from being submitted. If there is no custom error message, and none of the other properties return true, <code>valid</code> will be true, and the form can be submitted.</p>

<pre class="brush: js">function validate(input) {
  let validityState_object = input.validity;
  if(validityState_object.valueMissing) {
     input.setCustomValidity('A value is required');
  } else if (input.rangeUnderflow) {
    input.setCustomValidity('Your value is too low');
  } else if (input.rangeOverflow) {
    input.setCustomValidity('Your value is too high');
  } else {
    input.setCustomValidity('');
  }
}</pre>

<p>The last line, setting the custom validity message to the error string is vital. If the user makes an error, and the validity is set, it will fail to submit, even if all of the values are valid, until the message is <code>null</code>.</p>

<h4 id="Example">Example</h4>

<p>If you want to present a custom error message when a field fails to validate, you need to use the <a href="/en-US/docs/Web/API/Constraint_validation#Constraint_validation_interfaces">Constraint validation features</a> available on <code>&lt;input&gt;</code> (and related) elements. Take the following form:</p>

<pre class="brush: html">&lt;form&gt;
  &lt;label for="name"&gt;Enter username (upper and lowercase letters): &lt;/label&gt;
  &lt;input type="text" name="name" id="name" required pattern="[A-Za-z]+"&gt;
  &lt;button&gt;Submit&lt;/button&gt;
&lt;/form&gt;</pre>

<p>The basic HTML form validation features will cause this to produce a default error message if you try to submit the form with either no valid filled in, or a value that does not match the <code>pattern</code>.</p>

<p>If you wanted to instead display custom error messages, you could use JavaScript like the following:</p>

<pre class="brush: js">const nameInput = document.querySelector('input');
const form = document.querySelector('form');

nameInput.addEventListener('input', () =&gt; {
  nameInput.setCustomValidity('');
  nameInput.checkValidity();
});

nameInput.addEventListener('invalid', () =&gt; {
  if(nameInput.value === '') {
    nameInput.setCustomValidity('Enter your username!');
  } else {
    nameInput.setCustomValidity('Usernames can only contain upper and lowercase letters. Try again!');
  }
});</pre>

<p>The example renders like so:</p>

<p>In brief:</p>

<ul>
 <li>We check the valid state of the input element every time its value is changed by running the <code>checkValidity()</code> method via the <code>input</code> event handler.</li>
 <li>If the value is invalid, an <code>invalid</code> event is raised, and the <code>invalid</code> event handler function is run. Inside this function we work out whether the value is invalid because it is empty, or because it doesn't match the pattern, using an <code>if()</code> block, and set a custom validity error message.</li>
 <li>As a result, if the input value is invalid when the submit button is pressed, one of the custom error messages will be shown.</li>
 <li>If it is valid, it will submit as you'd expect. For this to happen, the custom validity has to be cancelled, by invoking <code>setCustomValidity()</code> with an empty string value. We therefore do this every time the <code>input</code> event is raised. If you don't do this, and a custom validity was previously set, the input will register as invalid, even if it current contains a valid value on submission.</li>
</ul>

<div class="blockIndicator note">
<p><strong>Note:</strong> Always validate input constraints both client side and server side. Constraint validation doesn't remove the need for validation on the <em>server side</em>. Invalid values can still be sent by older browsers or by bad actors.</p>
</div>

<div class="blockIndicator note">
<p><strong>Note</strong>：Firefox supported a proprietary error attribute — <code>x-moz-errormessage</code> — for many versions, which allowed you set custom error messages in a similar way. This has been removed as of version 66 (see <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=1513890">bug 1513890</a>).</p>
</div>

<h3 id="Localization">Localization</h3>

<p>The allowed inputs for certain <code>&lt;input&gt;</code> types depend on the locale. In some locales, 1,000.00 is a valid number, while in other locales the valid way to enter this number is 1.000,00.</p>

<p>Firefox uses the following heuristics to determine the locale to validate the user's input (at least for <code>type="number"</code>):</p>

<ul>
 <li>Try the language specified by a <code>lang</code>/<code>xml:lang</code> attribute on the element or any of its parents.</li>
 <li>Try the language specified by any <code>Content-Language</code> HTTP header. Or,</li>
 <li>If none specified, use the browser's locale.</li>
</ul>

<h3 id="Technical_summary">Technical summary</h3>

<table class="properties">
 <tbody>
  <tr>
   <th scope="row"><a href="/en-US/docs/Web/HTML/Content_categories">Content categories</a></th>
   <td><a href="/en-US/docs/Web/HTML/Content_categories#Flow_content">Flow content</a>, listed, submittable, resettable, form-associated element, <a href="/en-US/docs/Web/HTML/Content_categories#Phrasing_content">phrasing content</a>. If the <code><a href="/en-US/docs/Web/HTML/Element/input#attr-type">type</a></code> is not <code>hidden</code>, then labelable element, palpable content.</td>
  </tr>
  <tr>
   <th scope="row">Permitted content</th>
   <td>None, it is an <a href="/en-US/docs/Glossary/empty_element">empty element</a>.</td>
  </tr>
  <tr>
   <th scope="row">Tag omission</th>
   <td>Must have a start tag and must not have an end tag.</td>
  </tr>
  <tr>
   <th scope="row">Permitted parents</th>
   <td>Any element that accepts <a href="/en-US/docs/Web/HTML/Content_categories#Phrasing_content">phrasing content</a>.</td>
  </tr>
  <tr>
   <th scope="row">Permitted ARIA roles</th>
   <td>
    <ul>
     <li><code>type=button</code>：<code><a href="https://w3c.github.io/aria/#link">link</a></code>, <code><a href="https://w3c.github.io/aria/#menuitem">menuitem</a></code>, <code><a href="https://w3c.github.io/aria/#menuitemcheckbox">menuitemcheckbox</a></code>, <code><a href="https://w3c.github.io/aria/#menuitemradio">menuitemradio</a></code>, <code><a href="https://w3c.github.io/aria/#radio">radio</a></code>, <code><a href="https://w3c.github.io/aria/#switch">switch</a></code>, <code><a href="https://w3c.github.io/aria/#tab">tab</a></code></li>
     <li><code>type=checkbox</code>：<code><a href="https://w3c.github.io/aria/#button">button</a></code>, <code><a href="https://w3c.github.io/aria/#menuitemcheckbox">menuitemcheckbox</a></code>, <code><a href="https://w3c.github.io/aria/#option">option</a></code>, <code><a href="https://w3c.github.io/aria/#switch">switch</a></code></li>
     <li><code>type=image</code>：<code><a href="https://w3c.github.io/aria/#link">link</a></code>, <code><a href="https://w3c.github.io/aria/#menuitem">menuitem</a></code>, <code><a href="https://w3c.github.io/aria/#menuitemcheckbox">menuitemcheckbox</a></code>, <code><a href="https://w3c.github.io/aria/#menuitemradio">menuitemradio</a></code>, <code><a href="https://w3c.github.io/aria/#radio">radio</a></code>, <code><a href="https://w3c.github.io/aria/#switch">switch</a></code></li>
     <li><code>type=radio</code>：<code><a href="https://w3c.github.io/aria/#menuitemradio">menuitemradio</a></code></li>
     <li><code>type=color|date|datetime|datetime-local|email|file</code>：None</li>
     <li><code>type=hidden|month|number|password|range|reset</code>：None</li>
     <li><code>type=search|submit|tel|text|url|week</code>：None</li>
    </ul>
   </td>
  </tr>
  <tr>
   <th scope="row">DOM interface</th>
   <td><a href="/en-US/docs/Web/API/HTMLInputElement"><code>HTMLInputElement</code></a></td>
  </tr>
 </tbody>
</table>

<h2 id="Accessibility_concerns">Accessibility concerns</h2>

<h3 id="Labels_2">Labels</h3>

<p>When including inputs, it is an accessibilty requirement to add labels along side. This is needed so those who use assistive technologies can tell what the input is for. Also, clicking or touching a label gives focus to the label's associated form control. This improves the accessibility and usability for sighted users, increases the area a user can click or touch to activate the form control. this is especially useful (and even needed) for radio buttons and checkboxes, which are tiny. For more information about labels in general see <a href="#Labels">Labels</a> .</p>

<p>The following is an example of how to associate the <code>&lt;label&gt;</code> with an <code>&lt;input&gt;</code> element in the above style. You need to give the <code>&lt;input&gt;</code> an <code>id</code> attribute. The <code>&lt;label&gt;</code> then needs a <code>for</code> attribute whose value is the same as the input's <code>id</code>.</p>

<pre>&lt;label for="peas"&gt;Do you like peas?&lt;/label&gt;
&lt;input type="checkbox" name="peas" id="peas"&gt;
</pre>

<h3 id="Size">Size</h3>

<p>Interactive elements such as form input should provide an area large enough that it is easy to activate them. This helps a variety of people, including people with motor control issues and people using non-precise forms of input such as a stylus or fingers. A minimum interactive size of 44×44 <a href="https://www.w3.org/TR/WCAG21/#dfn-css-pixels">CSS pixels</a> is recommended.</p>

<ul>
 <li><a href="https://www.w3.org/WAI/WCAG21/Understanding/target-size.html">Understanding Success Criterion 2.5.5: Target Size | W3C Understanding WCAG 2.1</a></li>
 <li><a href="http://adrianroselli.com/2019/06/target-size-and-2-5-5.html">Target Size and 2.5.5 | Adrian Roselli</a></li>
 <li><a href="https://a11yproject.com/posts/large-touch-targets/">Quick test: Large touch targets - The A11Y Project</a></li>
</ul>

<h2 id="规范">规范</h2>

{{Specifications}}

<h2 id="Browser_compatibility">Browser compatibility</h2>

{{Compat}}

<h2 id="参见">参见</h2>

<ul>
 <li>Other form-related elements: {{HTMLElement("form")}}, {{HTMLElement("button")}}, {{HTMLElement("datalist")}}, {{HTMLElement("legend")}}, {{HTMLElement("label")}}, {{HTMLElement("select")}}, {{HTMLElement("optgroup")}}, {{HTMLElement("option")}}, {{HTMLElement("textarea")}}, {{HTMLElement("keygen")}}, {{HTMLElement("fieldset")}}, {{HTMLElement("output")}}, {{HTMLElement("progress")}} and {{HTMLElement("meter")}}.</li>
 <li><a href="http://webdesignerwall.com/tutorials/cross-browser-html5-placeholder-text">Cross-browser HTML5 placeholder text</a></li>
 <li>The CSS {{cssxref("caret-color")}} property</li>
 <li>In certain cases (typically involving non-textual inputs and specialized interfaces), the <code>&lt;input&gt;</code> element is a <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/Replaced_element">replaced element</a>. When it is, the position and size of the elemnt's size and positioning within its frame can be adjusted using the CSS {{cssxref("object-position")}} and {{cssxref("object-fit")}} properties</li>
</ul>