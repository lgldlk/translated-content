---
title: HTML_폼_구성_방법
slug: Learn/Forms/How_to_structure_a_web_form
translation_of: Learn/Forms/How_to_structure_a_web_form
original_slug: Learn/HTML/Forms/HTML_폼_구성_방법
---
<p>HTML폼을 만들떄 구조화 하는것은 중요한 것이다. 이것은 두가지 이유로 중요하다. 폼이 사용 할수 있다는 것을 보장하고 접근성도 늘릴수 있기 떄문이다.(즉 장애인들도 쉽게 사용할 수 있다.) <span style="line-height: 1.5;">HTML 폼의 <a href="https://developer.mozilla.org/en-US/docs/Web/Accessibility">접근성</a>은 중요한 점이고 어떻게 폼 접근성을 높일 수 있는지 볼것이다.</span></p>

<p><span style="line-height: 1.5;">HTML 폼들은 그 유연성으로 인해 HTML 중 복잡한 구조를 가지고 있는 요소중 하나이다. </span>폼 요소와 속성을 잘 혼합하면 모든 형태의 기본적인 폼을 만들 수 있다. 즉 몇몇 사람들이 HTML폼이 단순하고 매우 거칠다는 것을 발견했다는 것에 주목할 가치가 있다. <a href="https://developer.mozilla.org/en-US/docs/Archive/Web/XForms">XForms</a>같은 풍부한 기술이 있다는 것은 사실이지만 불행하게도 모든 브라우저에서 폼의 종류를 널리 구현되지 않았다. 왜냐하면 대부분 자바스크립트에 의존하여 HTML폼들을 다루기 떄문이다.이 문서에서는 HTML 폼 요소들을 어떻게 사용해야 하는지 자세하게 설명 할 것이다. 만약 사용자 폼 위젯 만들기에 대하여 자세한 내용을 알고 싶다면 다음 문서를 참조하시오. <a href="/en-US/docs/HTML/Forms/How_to_build_custom_form_widgets" title="/en-US/docs/HTML/Forms/How_to_build_custom_form_widgets">How to build custom form widgets</a></p>

<h2 id="글로벌_구조" style="line-height: 30px;">글로벌 구조</h2>

<h3 id="&lt;form>_요소" style="line-height: 24px;">&lt;form&gt; 요소</h3>

<p>{{HTMLElement("form")}} 요소는 공식적으로 폼을 정의하는 요소로 이 요소의 속성으로 폼의 작동하는 방식을 정의 할 수있다. HTML폼을 생성할떄마다 반드시 이 요소로 시작을 해야한다. 많은 보조 기술이나 브라우저 플러그인이 {{HTMLElement("form")}} 요소를 발견하고 쉽게 사용 할 수 있게 특별한 후크를 구현 할 수 있다.</p>

<p>우리는 저번 문서에서 이미 이 내용을 다루었다.</p>

<div class="note"><strong>주의:</strong>폼을 다른 폼으로 둘러싸는 것은 엄격하게 제한되어 있다. 만약 그렇게 하면 사용자가 사용하는 브라우저에 따라 예측할 수 없는 방식으로 작동하게 된다.</div>

<p>언제든지 폼위젯을 {{HTMLElement("form")}} 요소 바깥에서 사용할 수 있다. 하지만 그렇게 사용한다면, 그 폼위젯은 어떠한 폼과도 관련이 없다. 폼 위젯들은 폼 바깥에서 사용될 수  있지만, 그 위젯들은 스스로 아무것도 하지 않을 것이기 때문에 당신이 그 위젯들 전용 프로세스를 만들어주어야 한다. 당신은 자바스크립트로 그 동작을 정의해주어야 한다.</p>

<div class="note">
<p><strong>주의:</strong>HTML5에서 HTML 폼 요소안의 폼 속성이 지원된다. 폼 속성은 {{HTMLElement("form")}} 바깥에 있는 폼요소라도 폼과 명시적으로 연결한다. 불행하게도 지금 시점에 이 기능은 다양한 브라우저에서 안정적으로 구현되지 않아서 신뢰할 수 없다.</p>
</div>

<p>{{HTMLElement("form")}} 요소는 다음과 같은 속성을 가지고 모든 속성이 필수가 아닌 선택적이다.</p>

<p><br>
 <strong style="font-style: inherit; font-weight: bold; line-height: 1.5;"> {{HTMLElement("form")}} 요소 속성</strong></p>

<table>
 <thead>
  <tr>
   <th scope="col">속성 이름</th>
   <th scope="col">기본값</th>
   <th scope="col">설명</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td style="white-space: nowrap;">{{htmlattrxref("accept-charset","form")}}</td>
   <td><code>UNKNOWN</code></td>
   <td>서버가 받아들일 문자 인코딩의 형식을 지정한다. 기본값은 특수 문자열 <span style="font-family: 'Courier New','Andale Mono',monospace; line-height: normal;">UNKNOWN</span><span style="line-height: 1.5;">이고 이경우에 폼 요소 안에 있는 문서의 인코딩에 맞는 인코딩이다.</span></td>
  </tr>
  <tr>
   <td>{{htmlattrxref("action","form")}}</td>
   <td> </td>
   <td>폼을 통해서 전송한 정보를 처리하는 웹페이지의 URL </td>
  </tr>
  <tr>
   <td>{{htmlattrxref("autocomplete","form")}}</td>
   <td><code>on</code></td>
   <td>이 속성은 이 폼안에 있는 위젯들의 기본값이 브라우저에 의해 자동 완성 하게 하는지 여부를 나타낸다. 이속성은 두가지 값중 하나를 같는다. <code>on</code> 또는 <code>off</code>.</td>
  </tr>
  <tr>
   <td>{{htmlattrxref("enctype","form")}}</td>
   <td><code>application/x-www-form-urlencoded</code></td>
   <td>\<code>method</code> 속성이 <code>post 값으로 지정되면</code>,  서버로 폼을 전송하는 콘텐츠 <a href="http://en.wikipedia.org/wiki/Mime_type">MIME</a>의 타입을 지정한다.:
    <ul>
     <li><code>application/x-www-form-urlencoded</code></li>
     <li><code>multipart/form-data</code>: {{HTMLElement("input")}}요소의 <span style="font-family: 'Courier New','Andale Mono',monospace; line-height: normal;">type</span> 속성을 <em>file</em>로 지정한 경우 이 속성의 값을 사용한다. </li>
     <li><code>text/plain</code></li>
    </ul>
   </td>
  </tr>
  <tr>
   <td>{{htmlattrxref("method","form")}}</td>
   <td><code>get</code></td>
   <td><span style="line-height: 1.5;">브라우저가 폼을 전송하기위해 사용하는 <a href="http://www.w3.org/Protocols/rfc2616/rfc2616.html">HTTP</a>의 방식을 지정한다.</span><br>
    <span style="line-height: 1.5;">이 속성은 두개의 값중 한개를 가진다.</span>  <code>get</code> 또는 <code>post</code>.</td>
  </tr>
  <tr>
   <td>{{htmlattrxref("name","form")}}</td>
   <td> </td>
   <td>폼의 이름이다. 이 속성값은 반드시 문서의 폼 사이에서 고유해야하며 빈 문자열을 지정할 수없다. 일반적으로 <span style="font-family: 'Courier New','Andale Mono',monospace; line-height: normal;">id</span> 속성으로 대신 지정할 수 있다.</td>
  </tr>
  <tr>
   <td>{{htmlattrxref("novalidate","form")}}</td>
   <td>(<em>false</em>)</td>
   <td>이 불리언 속성은 폼이 전송 할떄 유효성 검사를 할수 없음을 나타낸다.</td>
  </tr>
  <tr>
   <td>{{htmlattrxref("target","form")}}</td>
   <td><code>_self</code></td>
   <td>폼 요청을 전송한후 응답을 어떻게 받을것인지 지정한다. 예를들어 {{HTMLElement("iframe")}}, tab, window를 사용 할 수 있다. 이 속성의 키워드로 다음과 같은 값을 사용 할 수있다.
    <ul>
     <li><code>_self</code>: 응답을 현재 브라우징 컨텍스트 ({{HTMLElement("iframe")}}, tab, window 등)에서 불러온다.</li>
     <li><code>_blank</code>: 응답을 새로운 브라우징 컨텍스트로 불러온다.</li>
     <li><code>_parent</code>: 응답을 현재의 브라우징 컨텍스트의 부모 브라우징 컨텍스트에서 불러온다. 만약 부모가 없다면 <code>_self 키워드와 똑같이 작동한다</code>.</li>
     <li><code>_top</code>: 응답을 최상휘 레벨 브라우징 컨텍스트에서 불러온다. 만약 최상위 컨텍스트가 없다면  <code>_self 키워드와 똑같이 작동한다</code>.</li>
    </ul>
   </td>
  </tr>
 </tbody>
</table>

<p>요소 밖에 폼 위젯들을 사용 할 수 있지만, 폼 위젯이 어떠한 폼과도 상관이 없다는 것을 유의 해야 한다.폼의 밖에서 위젯을 사용하는 것은 편리할 수 있지만 위젯들이 작동하기 위해 다른 것들을 해야 한다는 것을 의미한다. 아마 자바스크립트를 이용해서 동작을 정의 해야 할것이다.</p>

<p><span style="line-height: 1.5;">기술적으로 HTML5는 HTML 폼 요소에서 폼 속성을 설명 했다.</span> 이것은 요소들을 실제로  {{ HTMLElement("form") }} 안에 있지 않아도 form요소로 확실하게 바인딩 하도록 해야한다. 불행하게도 모든 브라우저가 아직 이것을 충분히 지원하지 않는다.</p>

<h3 id="&lt;fieldset>_와_&lt;legend>_요소" style="line-height: 24px;"> &lt;fieldset&gt; 와 &lt;legend&gt; 요소</h3>

<p>{{HTMLElement("fieldset")}}요소는 같은 목적을 가진 위젯들을 편리하게 그룹화 하는 방법이다. A {{HTMLElement("fieldset")}} 요소는 라벨인 {{HTMLElement("legend")}} 요소와 같이 사용된다. {{HTMLElement("legend")}} 요소는 공식적으로 {{HTMLElement("fieldset")}} 요소를 설명하는데 사용된다. 많은 보조 기술들이 {{HTMLElement("legend")}} 요소를 {{HTMLElement("fieldset")}} 요소의 라벨로 이용하는데 사용된다. 예를 들어 <span style="line-height: 1.5;"> </span><a href="http://www.freedomscientific.com/products/fs/jaws-product-page.asp" rel="external" style="line-height: 1.5;">Jaws</a>,<span style="line-height: 1.5;"> </span><a href="http://www.nvda-project.org/" rel="external" style="line-height: 1.5;">NVDA</a><span style="line-height: 1.5;">같은 스크린 리더들은 각각의 위젯의 라벨을 읽기전에 legend들을 읽을 것이다.</span><span style="line-height: 1.5;"> </span></p>

<p>아래 조그만 예제가 있다.</p>

<pre class="brush:html;" style="font-size: 14px;">&lt;form&gt;
  &lt;fieldset&gt;
    &lt;legend&gt;Fruit juice size&lt;/legend&gt;
    &lt;p&gt;
      &lt;input type="radio" name="size" id="size_1" value="small" /&gt;
      &lt;label for="size_1"&gt;Small&lt;/label&gt;
    &lt;/p&gt;
    &lt;p&gt;
      &lt;input type="radio" name="size" id="size_2" value="medium" /&gt;
      &lt;label for="size_2"&gt;Medium&lt;/label&gt;
    &lt;/p&gt;
    &lt;p&gt;
      &lt;input type="radio" name="size" id="size_3" value="large" /&gt;
      &lt;label for="size_3"&gt;Large&lt;/label&gt;
    &lt;/p&gt;
  &lt;/fieldset&gt;
&lt;/form&gt;</pre>

<p>이 예제를 스크림 리더가 Fruit juice size small을 먼저 읽고 Fruit juice size medium을 읽은 다음 마지막으로 Fruit juice size large을 읽을 것이다,</p>

<p>이것은 가장 중요한것 중 하나이다. 대부분 라디오 버튼을 설정할떄 마다{{HTMLElement("fieldset")}} 요소 안에 있는지 확인해야한다. 다르게 사용하는 사례가 있지만 일반적으로 {{HTMLElement("fieldset")}}  요소는 폼을 강력하게 사용할 수 있게 해준다. 보조기술의 영향으로 {{HTMLElement("fieldset")}}  요소는 폼 접근 할수 있는 키 요소 중 하나이다. 이것을 남용하지 않는 것은 개발자 책임이다. 가능한 폼을 만들떄마다 스크린리더로 들어보면서 하는 것이 좋다. 만약 말이 이상하게 들린다면 개선 해야 한다는 신호이다.</p>

<p>{{HTMLElement("fieldset")}} 요소는 다음과 같은 속성을 지정한다.</p>

<table>
 <caption>{{HTMLElement("fieldset")}} 요소의 속성</caption>
 <thead>
  <tr>
   <th scope="col">속성 이름</th>
   <th scope="col">기본값</th>
   <th scope="col">설명</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{htmlattrxref("disabled","fieldset")}}</td>
   <td>(<em>false</em>)</td>
   <td>만약 이 불리언 속성이 설정되면 폼은(첫번째 {{ HTMLElement("legend") }}요소에 있는 요소는 예외이다. ) 이것에 파생된 요소를 사용하거나 편집 할 수없게된다. 그리고 마우스 클릭같은 어떠한 브라우저 이벤트들도 받지 않을것이다. 일반적으로 브라우저는 회색으로 이를 표시할 것이다.</td>
  </tr>
 </tbody>
</table>

<h3 id="The_&lt;label>_element" style="line-height: 24px;">The &lt;label&gt; element</h3>

<p>{{HTMLElement("label")}} 요소는 HTML 폼 위젯을 정의하는 공식적인 방법이다. 이것은 접근성 있는 폼을 만드는데 가장 중요한 요소이다.</p>

<p>{{HTMLElement("label")}} 요소는 다음과 같은 속성을 지원한다.</p>

<p><br>
 <strong style="font-style: inherit; font-weight: bold; line-height: 1.5;">{{HTMLElement("label")}} </strong><span style="font-style: inherit; line-height: 1.5;">요소의 속성</span></p>

<p><br>
  </p>

<table>
 <thead>
  <tr>
   <th scope="col">속성 명</th>
   <th scope="col">기본값</th>
   <th scope="col">설명</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{htmlattrxref("for","label")}}</td>
   <td> </td>
   <td>{{HTMLElement("label")}}  요소와 같은 문서에 있는 위젯의 라벨의 ID . 문서안의 ID와 for속성 값이 같으면 그 라벨 요소는 그 위젯의 라벨이된다.</td>
  </tr>
 </tbody>
</table>

<p><span style="line-height: 1.5;">요소는 for속성으로 지정한 위젯과 묶여진다. </span>for속성은 해당 위젯의 실제 id 속성을 참조한다. <span style="line-height: 1.5;">위젯은 요소로 둘러싸게 할수 있지만 이 경우 몇가지 보조 기술이 라벨과 위젯의 암시적인 관계를 이해하지 못하기 떄문에 for 속성을 고려 해봐야한다.</span></p>

<p>심지어 보조 기술을 배제 한다고 하여도 모든 브라우저에서 공식적인 라벨 설정하면 사용자가 라벨을 누르면 해당하는 위젯이 활성화 할수 있다는 것을 알아 두어야한다. 이것은 라디오 버튼이나 체크박스를 사용하는데 특히 유용하다.</p>

<pre class="brush:html;" style="font-size: 14px;">&lt;form&gt;
  &lt;p&gt;
    &lt;input type="checkbox" id="taste_1" name="taste_cherry" value="1"&gt;
    &lt;label for="taste_1"&gt;I like cherry&lt;/label&gt;
  &lt;/p&gt;
  &lt;p&gt;
    &lt;label for="taste_2"&gt;
      &lt;input type="checkbox" id="taste_2" name="taste_banana" value="1"&gt;
      I like banana
    &lt;/label&gt;
  &lt;/p&gt;
&lt;/form&gt;</pre>

<p>몇가지 보조 기술은 여러개의 라벨을 한개의 위젯을 다루면 문제를 가질수 있다. 이 떄문에 위젯을 그에 맞는 폼 요소안에 넣어서 사용해야한다.</p>

<p>다음 예제를 보아라</p>

<pre class="brush:html;" style="font-size: 14px;">&lt;form&gt;
  &lt;p&gt;Required fields are followed by &lt;strong&gt;&lt;abbr title="required"&gt;*&lt;/abbr&gt;&lt;/strong&gt;.&lt;/p&gt;

  &lt;p&gt;
    &lt;label for="name"&gt;
      &lt;span&gt;Name: &lt;/span&gt;
      &lt;input type="text" id="name" name="username" required /&gt;
      &lt;strong&gt;&lt;abbr title="required"&gt;*&lt;/abbr&gt;&lt;/strong&gt;
    &lt;/label&gt;
  &lt;/p&gt;

  &lt;p&gt;
    &lt;label for="birth"&gt;
      &lt;span&gt;Date of birth: &lt;/span&gt;
      &lt;input type="text" id="birth" name="userbirth" maxlength="10" /&gt; &lt;em&gt;formated as mm/dd/yyyy&lt;/em&gt;
    &lt;/label&gt;
  &lt;/p&gt;
&lt;/form&gt;</pre>

<p>이 예제에서 첫번째 단락은 필수적인 요소의 규칙들을 정의한다. 이 것은 스크린 리더와 같은 보조 기술이 필수 요소들을 찾기전에 출력하거나 읽기 위해서는 반드시 시작부분 나타내야 한다. <span style="line-height: 1.5;">이런식으로 사용자는 항상 자신이 무엇을 하는지 알 수있다.</span></p>

<p>첫번째 필드는 필수적이기 떄문에 라벨 요소는 name 과 * 로 필수적인 필드를 나타낸다  이런 식으로 하면 스크린 리더는 "Name star" 또는 "Name required"이라고 읽을 것이다. ( 스크린 리더의 설정에 따라 다르지만 항상 첫번째 단락에서 읽어진 것을 읽는다).  만약 두가지 라벨을 사용한다면, 사용자가 이 요소가 필수 요소 인지 보여지는지 보장 할 수없다.</p>

<p>두번째 폼 요소는 비슷하게 작동한다. 이 기술을 사용하면 사용자에게 어떻게 데이터를 작성하는지 알려주는데 확신 할 수 있다.</p>

<h3 id="&lt;output>_요소" style="line-height: 24px;">&lt;output&gt; 요소</h3>

<p>이 요소는 계산의 출력을 저장하는데 사용된다. It formally defines a relationship between the fields used to get the data required to perform the calculation and an element to be used to display the results. It is also understood as a live region by some assistive technologies (which means that when the content of the {{HTMLElement("output")}} element changes, the assistive technology is aware of that change and can react to it).</p>

<p>{{HTMLElement("output")}} 요소는 다음 속성은 지원한다.</p>

<table>
 <caption>{{HTMLElement("output")}} 요소 속성</caption>
 <thead>
  <tr>
   <th scope="col">Attribute name</th>
   <th scope="col">Default value</th>
   <th scope="col">Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{htmlattrxref("for","output")}}</td>
   <td> </td>
   <td>스페이스로 구분된 다른 요소의 ID로 설정하고 이 요소들에 값을 입력을 계산하는데 기여한다.(또는 다른 효과)</td>
  </tr>
 </tbody>
</table>

<h3 id="form이_사용되는_일반적인_form_구조" style="line-height: 24px;">form이 사용되는 일반적인 form 구조</h3>

<p>HTML 폼의 지정된 구조를 넘어서 하나의 HTML이라고 생각 하는게 좋다. T 이 의미는 HTML 폼을 구성하는데 HTML의 모든 능력을 사용할 수 있다는 것이다.</p>

<p>예제에서 볼 수 있드니 라벨과 위젯을 둘러싸는데 최고의 방법은  {{HTMLElement("p")}}요소 나 {{HTMLElement("div")}}요소를 사용하는 것이다.</p>

<p>게다가 {{HTMLElement("fieldset")}} 요소에 HTML 타이틀을 사용하고 복잡한 폼을 만드는데 구조에 섹션을 사용하는것도 일반적인 관행이다.</p>

<p>HTML 목록은 체크박스나 라디오 버튼을 사용하는데 일반적으로 사용된다.</p>

<p>간단한 지불 폼을 만들어 보자</p>

<pre class="brush:html;" style="font-size: 14px;">&lt;form&gt;
  &lt;h1&gt;Payment form&lt;/h1&gt;
  &lt;p&gt;Required fields are followed by &lt;strong&gt;&lt;abbr title="required"&gt;*&lt;/abbr&gt;&lt;/strong&gt;.&lt;/p&gt;

  &lt;section&gt;
    &lt;h2&gt;Contact information&lt;/h2&gt;

    &lt;fieldset&gt;
      &lt;legend&gt;Title&lt;/legend&gt;
      &lt;ul&gt;
        &lt;li&gt;
          &lt;label for="title_1"&gt;
            &lt;input type="radio" id="title_1" name="title" value="M." /&gt;
            Mister
          &lt;/label&gt;
        &lt;/li&gt;
        &lt;li&gt;
          &lt;label for="title_2"&gt;
            &lt;input type="radio" id="title_2" name="title" value="Ms." /&gt;
            Miss
          &lt;/label&gt;
        &lt;/li&gt;
      &lt;/ul&gt;
    &lt;/fieldset&gt;

    &lt;p&gt;
      &lt;label for="name"&gt;
        &lt;span&gt;Name: &lt;/span&gt;
        &lt;input type="text" id="name" name="username" required /&gt;
        &lt;strong&gt;&lt;abbr title="required"&gt;*&lt;/abbr&gt;&lt;/strong&gt;
      &lt;/label&gt;
    &lt;/p&gt;

     &lt;p&gt;
      &lt;label for="mail"&gt;
        &lt;span&gt;E-mail: &lt;/span&gt;
        &lt;input type="email" id="mail" name="usermail" required /&gt;
        &lt;strong&gt;&lt;abbr title="required"&gt;*&lt;/abbr&gt;&lt;/strong&gt;
      &lt;/label&gt;
    &lt;/p&gt;
  &lt;/section&gt;

  &lt;section&gt;
    &lt;h2&gt;Payment information&lt;/h2&gt;

    &lt;p&gt;
      &lt;label for="card"&gt;
        &lt;span&gt;Card type:&lt;/span&gt;
        &lt;select id="card" name="usercard"&gt;
          &lt;option value="visa"&gt;Visa&lt;/option&gt;
          &lt;option value="mc"&gt;Mastercard&lt;/option&gt;
          &lt;option value="amex"&gt;American Express&lt;/option&gt;
        &lt;/select&gt;
      &lt;/label&gt;
    &lt;/p&gt;
    &lt;p&gt;
      &lt;label for="number"&gt;
        &lt;span&gt;Card number:&lt;/span&gt;
        &lt;input type="text" id="number" name="cardnumber" required /&gt;
        &lt;strong&gt;&lt;abbr title="required"&gt;*&lt;/abbr&gt;&lt;/strong&gt;
      &lt;/label&gt;
    &lt;/p&gt;
    &lt;p&gt;
      &lt;label for="date"&gt;
        &lt;span&gt;Expiration date:&lt;/span&gt;
        &lt;input type="text" id="date" name="expiration" required /&gt;
        &lt;strong&gt;&lt;abbr title="required"&gt;*&lt;/abbr&gt;&lt;/strong&gt;
        &lt;em&gt;formated as mm/yy&lt;/em&gt;
      &lt;/label&gt;
    &lt;/p&gt;
  &lt;/section&gt;

  &lt;section&gt;
    &lt;p&gt;
      &lt;button&gt;Validate the payment&lt;/button&gt;
    &lt;/p&gt;
  &lt;/section&gt;
&lt;/form&gt;</pre>

<p>See this form in action (with a touch of CSS):</p>

<p>{{EmbedLiveSample("A_payment_form","100%",620, "", "Learn/HTML/Forms/How_to_structure_an_HTML_form/Example")}}</p>

<h2 id="HTML_위젯" style="line-height: 30px;">HTML 위젯</h2>

<p>When you build a form, you need to use some widgets to collect data from the user. In this article we will see how to display those widgets; if you want to know more about the way those widgets work, it is detailed in the article: <a href="/en-US/docs/HTML/Forms/The_native_form_widgets" title="/en-US/docs/HTML/Forms/The_native_form_widgets">The native form widgets</a>.</p>

<h3 id="The_&lt;input>_element" style="line-height: 24px;">The &lt;input&gt; element</h3>

<p>이 요소는 거의 모든 것을 할 있기 떄문에 특별 한 종류이다. 간단하게 type속성을 설정하여 완전히 바뀔수 있다. 간단하게 하기 위해서 type속성의 값을 4가지로 분류하였다. 단일 라인 텍스트 필드, 텍스트 입력 없는 컨트롤, 시간이나 날짜 컨트롤, 버튼. <span style="line-height: 1.5;">이와 같은 다형성 떄문에  {{HTMLElement("input")}} 요소는 많은 속성을 지원하지만  type 속성값에 따라 달라지기 떄문에 어느 속성이 적절한지, 어느 것이 필요한지  선택하는 것은 어려울 수 있다. </span></p>

<p>This is all summarized in the following table (for a full list of all attributes, visit the page for the {{HTMLElement("input")}} element):</p>

<table>
 <thead>
  <tr>
   <th scope="col">type 속성 의 값</th>
   <th scope="col">설명</th>
   <th scope="col">필수 속성</th>
   <th scope="col">관련된 속성</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th colspan="4" style="text-align: center;">단일 선 텍스트 필드</th>
  </tr>
  <tr>
   <td><code>text</code></td>
   <td>이것은 가장 기본적인 텍스트 필드이다.  type속성을 위한 텍스트 값은 이 속성의 기본 값이다.(자동 유효성 검사를 하지않음)</td>
   <td> </td>
   <td>{{htmlattrxref("autocomplete","input")}}, {{htmlattrxref("list","input")}}, {{htmlattrxref("maxlength","input")}}, {{htmlattrxref("pattern","input")}}, {{htmlattrxref("placeholder","input")}}, {{htmlattrxref("readonly","input")}}, {{htmlattrxref("required","input")}}, {{htmlattrxref("size","input")}}, {{htmlattrxref("spellcheck","input")}}</td>
  </tr>
  <tr>
   <td><code>email</code></td>
   <td>하나 또는 여러개 이메일 주소를 작성하기 위해 사용되는 필드</td>
   <td> </td>
   <td>{{htmlattrxref("autocomplete","input")}}, {{htmlattrxref("list","input")}}, {{htmlattrxref("maxlength","input")}}, {{htmlattrxref("multiple","input")}}, {{htmlattrxref("pattern","input")}}, {{htmlattrxref("placeholder","input")}}, {{htmlattrxref("readonly","input")}}, {{htmlattrxref("required","input")}}, {{htmlattrxref("size","input")}}</td>
  </tr>
  <tr>
   <td><code>password</code></td>
   <td>텍스트 필드의 값을 가리기 위해 사용되는 텍스트 필드</td>
   <td> </td>
   <td>{{htmlattrxref("autocomplete","input")}}, {{htmlattrxref("list","input")}}, {{htmlattrxref("maxlength","input")}}, {{htmlattrxref("readonly","input")}}, {{htmlattrxref("required","input")}}, {{htmlattrxref("size","input")}}</td>
  </tr>
  <tr>
   <td><code>search</code></td>
   <td>검색 하기 위한 텍스트 필드</td>
   <td> </td>
   <td>{{htmlattrxref("autocomplete","input")}}, {{htmlattrxref("autosave","input")}}, {{htmlattrxref("list","input")}}, {{htmlattrxref("maxlength","input")}}, {{htmlattrxref("pattern","input")}}, {{htmlattrxref("placeholder","input")}}, {{htmlattrxref("readonly","input")}}, {{htmlattrxref("required","input")}}, {{htmlattrxref("size","input")}}, {{htmlattrxref("spellcheck","input")}}</td>
  </tr>
  <tr>
   <td><code>tel</code></td>
   <td>전화 번호를 입력할 수 있는 텍스트 필드</td>
   <td> </td>
   <td>{{htmlattrxref("autocomplete","input")}}, {{htmlattrxref("list","input")}}, {{htmlattrxref("maxlength","input")}}, {{htmlattrxref("pattern","input")}}, {{htmlattrxref("placeholder","input")}}, {{htmlattrxref("readonly","input")}}, {{htmlattrxref("required","input")}}, {{htmlattrxref("size","input")}}</td>
  </tr>
  <tr>
   <td><code>url</code></td>
   <td>절대 URL을 다루기 위한 필드</td>
   <td> </td>
   <td>{{htmlattrxref("autocomplete","input")}}, {{htmlattrxref("list","input")}}, {{htmlattrxref("maxlength","input")}}, {{htmlattrxref("pattern","input")}}, {{htmlattrxref("placeholder","input")}}, {{htmlattrxref("readonly","input")}}, {{htmlattrxref("required","input")}}, {{htmlattrxref("size","input")}}</td>
  </tr>
  <tr>
   <th colspan="4" style="text-align: center;">텍스트 입력 없는 컨트롤</th>
  </tr>
  <tr>
   <td><code>checkbox</code></td>
   <td>체크박스</td>
   <td> </td>
   <td>{{htmlattrxref("checked","input")}}, {{htmlattrxref("required","input")}}</td>
  </tr>
  <tr>
   <td><code>color</code></td>
   <td>색상을 입력 받기위한 필드</td>
   <td> </td>
   <td>{{htmlattrxref("autocomplete","input")}}, {{htmlattrxref("list","input")}}, {{htmlattrxref("required","input")}}</td>
  </tr>
  <tr>
   <td><code>file</code></td>
   <td>A control that lets the user select a file.</td>
   <td> </td>
   <td>{{htmlattrxref("accept","input")}}, {{htmlattrxref("multiple","input")}}, {{htmlattrxref("required","input")}}</td>
  </tr>
  <tr>
   <td><code>hidden</code></td>
   <td>보여주지 않는 컨트롤 이지만 서버로 전송되는 필드</td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td><code>number</code></td>
   <td>소숫점을 입력받는 컨트롤</td>
   <td> </td>
   <td>{{htmlattrxref("autocomplete","input")}}, {{htmlattrxref("list","input")}}, {{htmlattrxref("max","input")}}, {{htmlattrxref("min","input")}}, {{htmlattrxref("readonly","input")}}, {{htmlattrxref("required","input")}}, {{htmlattrxref("step","input")}}</td>
  </tr>
  <tr>
   <td><code>radio</code></td>
   <td>라디오 버튼. 그룹 중 한가지만 선택하기 위한 필드</td>
   <td> </td>
   <td>{{htmlattrxref("checked","input")}}, {{htmlattrxref("required","input")}}</td>
  </tr>
  <tr>
   <td><code>range</code></td>
   <td>정확하지 않는 숫자를 입력받기 위한 필드</td>
   <td> </td>
   <td>{{htmlattrxref("autocomplete","input")}}, {{htmlattrxref("list","input")}}, {{htmlattrxref("max","input")}}, {{htmlattrxref("min","input")}}, {{htmlattrxref("required","input")}}, {{htmlattrxref("step","input")}}</td>
  </tr>
  <tr>
   <th colspan="4" style="text-align: center;">시간 과 날짜 컨트롤</th>
  </tr>
  <tr>
   <td><code>date</code></td>
   <td>(년, 원, 일)날짜를 입력 받을 수 잇는 컨트롤</td>
   <td> </td>
   <td>{{htmlattrxref("autocomplete","input")}}, {{htmlattrxref("list","input")}}, {{htmlattrxref("max","input")}}, {{htmlattrxref("min","input")}}, {{htmlattrxref("readonly","input")}}, {{htmlattrxref("required","input")}}</td>
  </tr>
  <tr>
   <td><code>datetime</code></td>
   <td>UTC 타임 존 기반으로 전체 날짜와 시간(시간, 분, 초 )을 입력 받기 위한 필드</td>
   <td> </td>
   <td>{{htmlattrxref("autocomplete","input")}}, {{htmlattrxref("list","input")}}, {{htmlattrxref("max","input")}}, {{htmlattrxref("min","input")}}, {{htmlattrxref("readonly","input")}}, {{htmlattrxref("required","input")}}</td>
  </tr>
  <tr>
   <td><code>datetime-local</code></td>
   <td>타임존 기반이 아닌 날짜와 시간을 입력받기 위한 컨트롤</td>
   <td> </td>
   <td>{{htmlattrxref("autocomplete","input")}}, {{htmlattrxref("list","input")}}, {{htmlattrxref("max","input")}}, {{htmlattrxref("min","input")}}, {{htmlattrxref("readonly","input")}}, {{htmlattrxref("required","input")}}</td>
  </tr>
  <tr>
   <td><code>month</code></td>
   <td>타임존 기반이 아닌 달과 년도를 입력 받기 위한 컨트롤</td>
   <td> </td>
   <td>{{htmlattrxref("autocomplete","input")}}, {{htmlattrxref("list","input")}}, {{htmlattrxref("max","input")}}, {{htmlattrxref("min","input")}}, {{htmlattrxref("readonly","input")}}, {{htmlattrxref("required","input")}}</td>
  </tr>
  <tr>
   <td><code>time</code></td>
   <td>타임존 기반이 아닌 시간을 입력 받기 위한 컨트롤</td>
   <td> </td>
   <td>{{htmlattrxref("autocomplete","input")}}, {{htmlattrxref("list","input")}}, {{htmlattrxref("max","input")}}, {{htmlattrxref("min","input")}}, {{htmlattrxref("readonly","input")}}, {{htmlattrxref("required","input")}}</td>
  </tr>
  <tr>
   <td><code>week</code></td>
   <td>타임존 기반이 아닌 전체 날짜를 일주일-년도 숫자로 주 번호를 입력하는 컨트롤</td>
   <td> </td>
   <td>{{htmlattrxref("autocomplete","input")}}, {{htmlattrxref("list","input")}}, {{htmlattrxref("max","input")}}, {{htmlattrxref("min","input")}}, {{htmlattrxref("readonly","input")}}, {{htmlattrxref("required","input")}}</td>
  </tr>
  <tr>
   <th colspan="4" style="text-align: center;">버튼</th>
  </tr>
  <tr>
   <td><code>button</code></td>
   <td>기본 행동이 없는 누르는 버튼</td>
   <td> </td>
   <td>{{htmlattrxref("formaction","input")}}, {{htmlattrxref("formenctype","input")}}, {{htmlattrxref("formmethod","input")}}, {{htmlattrxref("formnovalidate","input")}}, {{htmlattrxref("formtarget","input")}}</td>
  </tr>
  <tr>
   <td><code>image</code></td>
   <td>그래픽적인 전송버튼</td>
   <td>{{htmlattrxref("src","input")}}, {{htmlattrxref("alt","input")}}</td>
   <td>{{htmlattrxref("width","input")}}, {{htmlattrxref("height","input")}}, {{htmlattrxref("formaction","input")}}, {{htmlattrxref("formenctype","input")}}, {{htmlattrxref("formmethod","input")}}, {{htmlattrxref("formnovalidate","input")}}, {{htmlattrxref("formtarget","input")}}</td>
  </tr>
  <tr>
   <td><code>reset</code></td>
   <td>폼의 내용을 초기화 하는 컨트롤</td>
   <td> </td>
   <td>{{htmlattrxref("formaction","input")}}, {{htmlattrxref("formenctype","input")}}, {{htmlattrxref("formmethod","input")}}, {{htmlattrxref("formnovalidate","input")}}, {{htmlattrxref("formtarget","input")}}</td>
  </tr>
  <tr>
   <td><code>submit</code></td>
   <td>폼을 전송하는 버튼</td>
   <td> </td>
   <td>{{htmlattrxref("formaction","input")}}, {{htmlattrxref("formenctype","input")}}, {{htmlattrxref("formmethod","input")}}, {{htmlattrxref("formnovalidate","input")}}, {{htmlattrxref("formtarget","input")}}</td>
  </tr>
 </tbody>
</table>

<p><span style="line-height: 1.5;">몇가지 이유 때문에 브라우저에서 특정 type 속성의 값 설정을 지원하지 않으면 {{HTMLElement("input")}} 요소는  text 속성으로 렌더링 한다. </span>이것은 매력적이지 않아도 어쩔 수없이 폼이 작동하도록 한다.</p>

<p>요소는 강력한 도구지만, 모든 것을 할수 없고 다른 것들을 다루기 위해 다른 요소들이 있다.</p>

<h3 id="&lt;textarea>_요소" style="line-height: 24px;">&lt;textarea&gt; 요소</h3>

<p>이 요소는 다중 텍스트 필드로 설정된다. 이 요소는 사용자가 입력한 텍스트에 줄 바꿈을 할수 있다는 것을 제외하고 단일 라인 텍스트 필드와 정확하게 똑같이 작동한다. 또한 여러줄에 걸처 랜더링을 제어 하기위해 몇가지 추가 속성 설정을 허락한다.</p>

<table>
 <caption> {{HTMLElement("textarea")}} 요소 속성</caption>
 <thead>
  <tr>
   <th scope="col">Attribute name</th>
   <th scope="col">기본값</th>
   <th scope="col">설명</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{htmlattrxref("cols","textarea")}}</td>
   <td><code>20</code></td>
   <td>보여지는 문자 너비의 평균을 기준으로 텍스트 컨트롤의 너비</td>
  </tr>
  <tr>
   <td>{{htmlattrxref("rows","textarea")}}</td>
   <td> </td>
   <td>보여지는 텍스트 행의 수</td>
  </tr>
  <tr>
   <td>{{htmlattrxref("wrap","textarea")}}</td>
   <td><code>soft</code></td>
   <td>hard, soft 이 둘중 하나의 값으로 어떻게 텍스트를 둘러쌀것인지 나타낸다.</td>
  </tr>
 </tbody>
</table>

<p> {{HTMLElement("textarea")}} 요소는 {{HTMLElement("input")}} 요소와 다르게 작동한다. {{HTMLElement("input")}} 요소는 자동으로 닫히는 요소이다. 이는 자식 요소를 가질 수 없다는 것을 의미한다. 이와 반대로 요소는 text 콘텐츠를 자식으로 가질 수 있는 일반적인 요소이다.</p>

<p>이는 두가지 영향이 있다.</p>

<ul>
 <li>만약 {{HTMLElement("input")}}요소에 기본값을 정의하기 원한다면, value 속성을 사용하여 지정해야 되나, {{HTMLElement("textarea")}}요소에서는 기본값을 {{HTMLElement("textarea")}} 태그 사이에 넣기만 하면된다.</li>
 <li>자연스러움 때문에  {{HTMLElement("textarea")}} 요소는 오직 텍스트 콘텐츠만 받아들인다. 이 의미는 어떠한 HTML콘텐츠도  {{HTMLElement("textarea")}} 요소에 넣으면 텍스트 콘텐츠로 렌더링 된다.</li>
</ul>

<p> 예제를 따라가면 다음 두 요소는 똑같이 랜더링 되어 질것이다.</p>

<pre class="brush:html;" style="font-size: 14px;">&lt;form&gt;
  &lt;p&gt;
    &lt;label for="text_1"&gt;With regular HTML&lt;/label&gt;&lt;br&gt;
    &lt;textarea id="text_1" name="regular"&gt;&lt;p&gt;I'm a paragraphe&lt;/p&gt;&lt;/textarea&gt;
  &lt;/p&gt;
  &lt;p&gt;
    &lt;label for="text_2"&gt;With escaped HTML&lt;/label&gt;&lt;br&gt;
    &lt;textarea id="text_2" name="escaped"&gt;&amp;lt;p&amp;gt;I'm a paragraphe&amp;lt;/p&amp;gt;&lt;/textarea&gt;
  &lt;/p&gt;
  &lt;p&gt;
    &lt;button&gt;Send me&lt;/button&gt;
  &lt;/p&gt;
&lt;/form&gt;</pre>

<h3 id="&lt;select>_&lt;option>그리고_&lt;optgroup>_요소" style="line-height: 24px;">&lt;select&gt;, &lt;option&gt;그리고 &lt;optgroup&gt; 요소</h3>

<p>요소는 선택 박스를 만들 수 있게 해준다(떄로는 콤보 박스라고 한다). 선택 박스는 사용자가 하나 이상 미리 정의 된 값을 선택하는 위젯이다. 단일 값 선택  박스와 다중 값 선택 박스는 다르다. 이에 대한 자세한 내용은 다음 문서를 확인해라 <a href="/en-US/docs/HTML/Forms/The_native_form_widgets" title="/en-US/docs/HTML/Forms/The_native_form_widgets">The native form widgets</a>.</p>

<p>선택 박스 안의 값들은  {{HTMLElement("option")}} 요소에서 정의되고 {{HTMLElement("optgroup")}} 요소 안에서 그룹화 될 수 있다.</p>

<p>Let's take an example:</p>

<pre class="brush:html;" style="font-size: 14px;">&lt;form&gt;
  &lt;p&gt;
    &lt;label for="myFruit"&gt;Pick a fruit&lt;/label&gt;
    &lt;select id="myFruit" name="fruit"&gt;
      &lt;!-- There is a trick here you think you'll pick
         a banana but you'll eat an orange &gt;:-) --&gt;
      &lt;option value="orange"&gt;Banana&lt;/option&gt;
      &lt;option&gt;Cherry&lt;/option&gt;
      &lt;optgroup label="berries"&gt;
        &lt;option&gt;Blueberry&lt;/option&gt;
        &lt;option&gt;Raspberry&lt;/option&gt;
        &lt;option&gt;Strawberry&lt;/option&gt;
      &lt;/optgroup&gt;
    &lt;/select&gt;
  &lt;/p&gt;
&lt;/form&gt;</pre>

<p><span style="line-height: 1.5;">{HTMLElement("option")}} 요소는 폼이 전송되면 전송될 value속성을 설정한다.</span> <span style="line-height: 1.5;">만약 value 속성을 바뜨리면 {{HTMLElement("option")}} 요소는 value 값을 선택 박스 값으로 사용된다.</span></p>

<p><span style="line-height: 1.5;">{{HTMLElement("optgroup")}} 요소의 라벨 속성은 값이 나오기전에 보여주고 옵션 같은 요소들은 선택할 수 없게 나온다.</span>.</p>

<table>
 <caption>{{HTMLElement("option")}} 요소 의 속성</caption>
 <thead>
  <tr>
   <th scope="col">속성 이름</th>
   <th scope="col">기본값</th>
   <th scope="col">설명</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{htmlattrxref("label","option")}}</td>
   <td> </td>
   <td>이 속성은 옵션을 설명하는 라벨의 텍스트이다. 만약 라벨 속성이 정의되지 않으면 이 값은 요소의 텍스트 콘텐츠로 설정된다.</td>
  </tr>
  <tr>
   <td>{{htmlattrxref("selected","option")}}</td>
   <td>(<em>false</em>)</td>
   <td>만약 이 속성이 불리언 값으로 설정되는 경우 처음에 선택된 상태로 시작하게된다.</td>
  </tr>
 </tbody>
</table>

<table>
 <caption>Attributes for the {{HTMLElement("optgroup")}} element</caption>
 <thead>
  <tr>
   <th scope="col">Attribute name</th>
   <th scope="col">Default value</th>
   <th scope="col">Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{htmlattrxref("label","optgroup")}}</td>
   <td> </td>
   <td>The name of the group of options. <strong>This attribute is mandatory.</strong></td>
  </tr>
 </tbody>
</table>

<h3 id="&lt;datalist>요소" style="line-height: 24px;">&lt;datalist&gt;요소 </h3>

<p>이 요소는 기존에 있는 위젯들에 사전 설정 값을 제공 함으로써 위젯들을 확장시킨다. 가장 잘 알려진 사용 방법은 텍스트 필드의 자동 완성 목록이다. 값들은 {{HTMLElement("datalist")}} 요소 안에 있는 {{HTMLElement("option")}}요소의 값으로 사용할 수 있다.</p>

<p>{{HTMLElement("datalist")}}요소와 바인드 하기위해서는 사용하는 요소의 list속성을 이용하여 설정해야한다. 이 속성은 {{HTMLElement("datalist")}} 요소의 id로 설정된다.</p>

<p>요소는 최근에 HTML 폼으로 추가 되었다. 그러므로 아직 이를 지원하지 않는 브라우저들도 있다. 이 문제를 처리하기 위하여 아래에 약간 까다로운 예제가 있다.</p>

<pre class="brush:html;" style="font-size: 14px;">&lt;form&gt;
  &lt;p&gt;
    &lt;label for="myFruit"&gt;What is your favorite fruit?&lt;/label&gt;
    &lt;input type="text" id="myFruit" name="fruit" list="fruitList" /&gt;

    &lt;datalist id="fruitList"&gt;
      &lt;label for="suggestion"&gt;or pick a fruit&lt;/label&gt;
      &lt;select id="suggestion" name="altFruit"&gt;
        &lt;option value="banana"&gt;Banana&lt;/option&gt;
        &lt;option value="cherry"&gt;Cherry&lt;/option&gt;
        &lt;option value="strawberry"&gt;Strawberry&lt;/option&gt;
      &lt;/select&gt;
    &lt;/datalist&gt;
  &lt;/p&gt;
&lt;/form&gt;</pre>

<p>한편 {{HTMLElement("datalist")}} 요소를 지원하는 브라우저는 {{HTMLElement("option")}} 요소를 무시하고 이를 사용하는 요소를 확장 할 것이다. 이와 반대로 {{HTMLElement("datalist")}} 요소를 지원하지 않는 브라우저는 라벨과 선택 박스를 표시 할 것이다. 물론 {{HTMLElement("datalist")}} 요소를 지원하지 않는 브라우저에 대해 자바스크립트로 하는 다른 방법이 있지만 항상 자바스크립트만 사용하는 것은 좋은 것이 아니다.</p>

<table>
 <tbody>
  <tr>
   <th scope="row">Safari 6</th>
   <td><img alt="Screenshot of the datalist element fallback with Safari on Mac OS" src="/files/4583/datalist-safari.png" style="height: 32px; width: 495px;"></td>
  </tr>
  <tr>
   <th scope="row">Firefox 18</th>
   <td><img alt="Screenshot of the datalist element with Firefox on Mac OS" src="/files/4581/datalist-firefox-macos.png" style="height: 102px; width: 353px;"></td>
  </tr>
 </tbody>
</table>

<h3 id="&lt;meter>_와_&lt;progress>_요소들" style="line-height: 24px;">&lt;meter&gt; 와 &lt;progress&gt; 요소들 </h3>

<p>이 두요소는 그래픽적으로 숫자 값을 표현 하는방법이다. 이 두 요소의 차이점은 두 요소의 의미가 다르다는 것이다.</p>

<ul>
 <li>{{HTMLElement("meter")}} 요소는 정적인 값을 최소와 최대 값사이에 상대적인 위치를 나타낸다</li>
 <li>The {{HTMLElement("progress")}} 요소는 최소와 최대값을 시간에 따라 바뀌는 가변적인 값을 나타낸다. 값이 변하면 자바스크립트를 이용하여 다룰수 있다는것을 주목할 필요가 있다. 요소 자신은 값을 변화시키기 위한 어떠한 매커니즘도 가지고 있지 않다.</li>
</ul>

<p>속성으로 인해 이 요소들은 다음 속성을 지정 가능하다.</p>

<p><br>
 <strong style="font-style: inherit; font-weight: bold; line-height: 1.5;">{{HTMLElement("meter")}} 요소는 다음과 같은 속성을 가진다</strong></p>

<table>
 <thead>
  <tr>
   <th scope="col">Attribute name</th>
   <th scope="col">Default value</th>
   <th scope="col">Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{htmlattrxref("min","meter")}}</td>
   <td>0</td>
   <td>The lower numeric bound of the measured range.</td>
  </tr>
  <tr>
   <td>{{htmlattrxref("max","meter")}}</td>
   <td>1</td>
   <td>The upper numeric bound of the measured range.</td>
  </tr>
  <tr>
   <td>{{htmlattrxref("low","meter")}}</td>
   <td>the <code>min</code> value</td>
   <td>The upper numeric bound of the low end of the measured range.</td>
  </tr>
  <tr>
   <td>{{htmlattrxref("high","meter")}}</td>
   <td>the <code>max</code> value</td>
   <td>The lower numeric bound of the high end of the measured range.</td>
  </tr>
  <tr>
   <td>{{htmlattrxref("optimum","meter")}}</td>
   <td> </td>
   <td>The optimal numeric value.</td>
  </tr>
 </tbody>
</table>

<table>
 <caption>Attributes for the {{HTMLElement("progress")}} element</caption>
 <thead>
  <tr>
   <th scope="col">Attribute name</th>
   <th scope="col">Default value</th>
   <th scope="col">Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{htmlattrxref("max","progress")}}</td>
   <td> </td>
   <td>This attribute describes how much work the task indicated by the {{HTMLElement("progress")}} element requires before it's complete.</td>
  </tr>
 </tbody>
</table>

<h3 id="The_&lt;button>_element" style="line-height: 24px;">The &lt;button&gt; element </h3>

<p>{{HTMLElement("button")}} 요소는 폼 버튼을 만드는 가장 쉬운 방법이다. <span style="line-height: 1.5;">버튼은 type속성에 따라 3가지 타입을 가진다.</span></p>

<ul>
 <li>전송 버튼은 폼 데이터들을 {{HTMLElement("form")}}요소에 action 속성에 정의 된 웹 페이지에 보낸다.</li>
 <li>리셋 버튼은 폼의 모든 위젯들을 기본 값으로 재설정한다. 폼 사용자 경험 관점에서 이 버튼을 사용하는것은 좋지 않은 사례로 간주되고 이를 피해야 한다. 이것은 사용자가 단순히 실수로 한것이 모든 작업을 잃게 할 수 있다.</li>
 <li>익명 버튼은 어떠한 의미도 없는 대신 자바스크립트를 이용하여 다룰 수 있다..</li>
</ul>

<p><br>
 <strong style="font-style: inherit; font-weight: bold; line-height: 1.5;">{HTMLElement("button")}} 요소의 속성</strong></p>

<table>
 <thead>
  <tr>
   <th scope="col">속성 이름</th>
   <th scope="col">기본값</th>
   <th scope="col">설명</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{htmlattrxref("type","button")}}</td>
   <td><code>submit</code></td>
   <td>버튼의 타입.  <code>button</code>, <code>reset</code>, <code>submit 이 있다.</code></td>
  </tr>
  <tr>
   <td>{{htmlattrxref("formaction","button")}}</td>
   <td> </td>
   <td>만약 버튼이 submit 버튼이면 이 속성은  {{HTMLElement("form")}}요소의 action 속성에 오버라이드 된다.</td>
  </tr>
  <tr>
   <td>{{htmlattrxref("formenctype","button")}}</td>
   <td> </td>
   <td>만약 버튼이 submit 버튼이면 이 속성은  {{HTMLElement("form")}}요소의 enctype 속성에 오버라이드 된다.</td>
  </tr>
  <tr>
   <td>{{htmlattrxref("formmethod","button")}}</td>
   <td> </td>
   <td>만약 버튼이 submit 버튼이면 이 속성은  {{HTMLElement("form")}}요소의 method 속성에 오버라이드 된다.</td>
  </tr>
  <tr>
   <td>{{htmlattrxref("formnovalidate","button")}}</td>
   <td> </td>
   <td>만약 버튼이 submit 버튼이면 이 속성은  {{HTMLElement("form")}}요소의 novalidate 속성에 오버라이드 된다.</td>
  </tr>
  <tr>
   <td>{{htmlattrxref("formtarget","button")}}</td>
   <td> </td>
   <td>만약 버튼이 submit 버튼이면 이 속성은  {{HTMLElement("form")}}요소의 target 속성에 오버라이드 된다.</td>
  </tr>
 </tbody>
</table>

<p>기술적으로 말하면 {{HTMLElement("button")}} 요소와 {{HTMLElement("input")}} 요소의 속성에 정의된 버튼 요소는 거의 차이가 없다. 단 한가지 차이점은 버튼 자체의 라벨 이다.요소 안에서는 라벨은 오직 문자 데이터로만 나타 낼 수 있지만 {{HTMLElement("button")}} 요소에서는 어떠한 HTML이 될 수있다. 그래서 이에 따른 스타일을 디자인 할 수있다.</p>

<div class="note"><strong>Note:</strong> For historical reasons, the {{HTMLElement("button")}} element wasn't used very often and in many forms developers preferred to use buttons made with the {{HTMLElement("input")}} element. This is due to a bug in legacy versions of Internet Explorer (IE). In IE6 and IE7, if you add a <code>name</code> and a <code>value</code> attribute to a {{HTMLElement("button")}} element, they do not send the content of the <code>value</code> attribute but the raw content of the button instead. This has been fixed since IE8, so there is no longer any reason to avoid using the {{HTMLElement("button")}} element.</div>

<div class="note"> </div>

<h3 id="공통_속성" style="line-height: 24px;">공통 속성</h3>

<p>Many of the elements used to define form widgets have some their own attributes. However, there is a set of attributes common to all form elements that give you some control over those widgets. Here is a list of those common attributes:</p>

<table>
 <thead>
  <tr>
   <th scope="col">Attribute name</th>
   <th scope="col">Default value</th>
   <th scope="col">Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><code>autofocus</code></td>
   <td>(<em>false</em>)</td>
   <td>This Boolean attribute lets you specify that the element should automatically have input focus when the page loads, unless the user overrides it, for example by typing in a different control. Only one form-associated element in a document can have this attribute specified.</td>
  </tr>
  <tr>
   <td><code>disabled</code></td>
   <td>(<em>false</em>)</td>
   <td>This Boolean attribute indicates that the user cannot interact with the element. If this attribute is not specified, the element inherits its setting from the containing element, for example {{HTMLElement("fieldset")}}; if there is no containing element with the <code>disabled</code> attribute set, then the element is enabled.</td>
  </tr>
  <tr>
   <td><code>form</code></td>
   <td> </td>
   <td>The form element that the widget is associated with. The value of the attribute must be the <code>id</code> attribute of a {{HTMLElement("form")}} element in the same document. In theory, it lets you set a form widget outside of a {{HTMLElement("form")}} element. In practice, however, there is no browser which supports that feature.</td>
  </tr>
  <tr>
   <td><code>name</code></td>
   <td> </td>
   <td>The name of the element; this is submitted with the form data.</td>
  </tr>
  <tr>
   <td><code>value</code></td>
   <td> </td>
   <td>The element's initial value.</td>
  </tr>
 </tbody>
</table>

<h2 id="Using_ARIA_to_structure_HTML_forms" style="line-height: 30px;">Using <a href="/en-US/docs/Accessibility/ARIA" title="/en-US/docs/Accessibility/ARIA">ARIA</a> to structure HTML forms</h2>

<p><a href="/en-US/docs/Accessibility/ARIA" title="/en-US/docs/Accessibility/ARIA">ARIA</a> is <a href="http://www.w3.org/TR/wai-aria/" rel="external">a W3C Candidate Recommendation</a> which adds to HTML improved accessibility for rich Internet applications, including for forms. We will discuss its use in more detail in the "<a href="/en-US/docs/HTML/Forms/How_to_build_custom_form_widgets" title="/en-US/docs/HTML/Forms/How_to_build_custom_form_widgets">How to build custom form widgets</a>" article, but there are some basics that are good to know.</p>

<p>Before going further, it's worth noting that support for ARIA and assistive technologies among browsers is far from perfect, but it's improving. Just to understand the issue, when a browser encounters an ARIA attribute, it has to send information to the operating system's accessibility layer. Not all browsers are good at doing this cross platform. The assistive technologies, on their own, have to connect themselves to the OS accessibility layer to handle the information that comes from the browsers. Surprisingly, not all assistive technologies do it well. So using ARIA does not mean that your web application will be accessible, but it means that you do your best to achieve this. Unfortunately, for the time being, ARIA remains a best effort technology, but it's always better than nothing.</p>

<p>If you want to dig into using ARIA with HTML forms, feel free to <a href="/en-US/docs/Accessibility/ARIA/forms" title="/en-US/docs/Accessibility/ARIA/forms">read the related section in the ARIA documentation</a>.</p>

<h3 id="The_aria-labelledby_attribute" style="line-height: 24px;">The <a href="/en-US/docs/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-labelledby_attribute" title="/en-US/docs/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-labelledby_attribute"><code>aria-labelledby</code></a> attribute</h3>

<p>This attribute is a convenient way to define a label without using the {{HTMLElement("label")}} element. The attribute is set on the widget element and references the <code>id</code> attribute of the element to use as a label.</p>

<pre class="brush:html;" style="font-size: 14px;">&lt;form&gt;
  &lt;p id="fruitLabel"&gt;What's your favorite fruit&lt;/p&gt;
  &lt;p&gt;
    &lt;input type="text" name="fruit" aria-labelledby="fruitLabel"&gt;
  &lt;/p&gt;
&lt;/form&gt;</pre>

<p>Conceptually, it's the opposite of the <code>for</code> attribute on the {{HTMLElement("label")}} element. With the <code>for</code> attribute, you reference the <code>id</code> of the widget but with the <code>aria-labbeldby</code> attribute, you reference the <code>id</code> of the label.</p>

<h3 id="The_aria-describedby_attribute" style="line-height: 24px;">The <a href="/en-US/docs/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-describedby_attribute" title="/en-US/docs/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-describedby_attribute"><code>aria-describedby</code></a> attribute</h3>

<p>This attribute works like the <code>aria-labelledby</code> attribute. The difference is mainly semantic. A label defines the essence of an object, while a description provides more information that the user might need. This attribute is not advised for form elements, you should rely on the <code>aria-labelledby</code> attribute, except if you want to provide extensive information on the current form element. It is to be used as a provider for a longer description.</p>

<h3 id="The_aria-label_attribute" style="line-height: 24px;">The <a href="/en-US/docs/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-label_attribute" title="/en-US/docs/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-label_attribute"><code>aria-label</code></a> attribute</h3>

<p>This attribute is used when there is no explicit label in the DOM for a given widget. It lets you provide a widget that will be passed to assitive technologies without actually creating a DOM node for it.</p>

<pre class="brush:html;" style="font-size: 14px;">&lt;form&gt;
  &lt;p&gt;
    &lt;input type="search" name="q" aria-label="Search" /&gt;
    &lt;input type="submit" value="Go" /&gt;
  &lt;/p&gt;
&lt;/form&gt;</pre>

<h3 id="The_role_attribute" style="line-height: 24px;">The <a href="/en-US/docs/Accessibility/ARIA/ARIA_Techniques" title="/en-US/docs/Accessibility/ARIA/ARIA_Techniques"><code>role</code></a> attribute</h3>

<p>This is the most important ARIA attribute. It lets you give specific semantic information, understandable by assitive technologies, for a given HTML element. There are many roles available and some of them are dedicated to form widgets.</p>

<p>ARIA tries to provide semantics for widgets that are not currently available in HTML as well as for elements that already exist. We will see in detail how to use those roles in the article: How to build custom form widgets.</p>

<p>Those roles for form widgets are :</p>

<ul>
 <li><a href="/en-US/docs/Accessibility/ARIA/ARIA_Techniques/Using_the_button_role" title="/en-US/docs/Accessibility/ARIA/ARIA_Techniques/Using_the_button_role">Button</a></li>
 <li><a href="/en-US/docs/Accessibility/ARIA/ARIA_Techniques/Using_the_checkbox_role" title="/en-US/docs/Accessibility/ARIA/ARIA_Techniques/Using_the_checkbox_role">Checkbox</a></li>
 <li><a href="/en-US/docs/Accessibility/ARIA/ARIA_Techniques/Using_the_progressbar_role" title="/en-US/docs/Accessibility/ARIA/ARIA_Techniques/Using_the_progressbar_role">Progressbar</a></li>
 <li>Radio</li>
 <li><a href="/en-US/docs/Accessibility/ARIA/ARIA_Techniques/Using_the_slider_role" title="/en-US/docs/Accessibility/ARIA/ARIA_Techniques/Using_the_slider_role">Slider</a></li>
 <li>Spinbutton</li>
 <li><a href="/en-US/docs/Accessibility/ARIA/ARIA_Techniques/Using_the_textbox_role" title="/en-US/docs/Accessibility/ARIA/ARIA_Techniques/Using_the_textbox_role">textbox</a></li>
</ul>

<p>It's also worth noting that there's something called a composite role:</p>

<ul>
 <li><a href="/en-US/docs/Accessibility/ARIA/ARIA_Techniques/Using_the_listbox_role" title="/en-US/docs/Accessibility/ARIA/ARIA_Techniques/Using_the_listbox_role">Listbox</a></li>
 <li>Radiogroup</li>
</ul>

<p>If those roles are extremely useful, know that <a href="/en-US/docs/Accessibility/ARIA/ARIA_Techniques" title="/en-US/docs/Accessibility/ARIA/ARIA_Techniques">there are more</a>; ARIA is a very large specification. Digging into it can help you improve accessibility in areas far afield from HTML forms.</p>

<h2 id="결론" style="line-height: 30px;">결론</h2>

<p>You now have all the knowledge to properly structure your HTML forms; the next article will dig into implementation details and functional expectations: <a href="/en-US/docs/HTML/Forms/The_native_form_widgets" title="/en-US/docs/HTML/Forms/The_native_form_widgets">The native form widgets</a>.</p>

<h2 id="볼거리" style="line-height: 30px;">볼거리</h2>

<ul>
 <li><a href="http://www.alistapart.com/articles/sensibleforms/" rel="external">A List Apart: <em>Sensible Forms: A Form Usability Checklist</em></a></li>
</ul>