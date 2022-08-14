---
title: 'Django 튜토리얼 파트 9: 폼(form)으로 작업하기'
slug: Learn/Server-side/Django/Forms
translation_of: Learn/Server-side/Django/Forms
---
<div>{{LearnSidebar}}</div>

<div>{{PreviousMenuNext("Learn/Server-side/Django/authentication_and_sessions", "Learn/Server-side/Django/Testing", "Learn/Server-side/Django")}}</div>

<p class="summary">이 튜토리얼에서 우리는 Django에서 HTML Form 작업 방법을 보여주고 특히 model Instance를 생성,수정,제거 하는 Form을 작성하는 가장 쉬운 방법을 보여줄 것이다. 이 예제의 일부분으로 우리는 도서관직원이 (admin 앱을 이용하기 보다) 우리가 만든 form을 이용하여 책 대여기간을 연장하거나 작가 정보를 생성,수정,제거할 수 있도록 <a href="https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Tutorial_local_library_website">LocalLibrary</a> 웹사이트를 확장할 것이다.</p>

<table class="learn-box standard-table">
 <tbody>
  <tr>
   <th scope="row">사전학습:</th>
   <td>아래 파트를 포함하여 앞선 모든 튜토리얼 파트의 학습을 완료할것 <a href="/en-US/docs/Learn/Server-side/Django/authentication_and_sessions">Django 튜토리얼 파트 8: 사용자 인증과 이용권한</a>.</td>
  </tr>
  <tr>
   <th scope="row">학습목표:</th>
   <td>사용자로 부터 정보를 얻고 database를 수정하는 form을 작성하는 방법을 이해하기. 일반 클래스 기반 form 편집용 view가  단독 model로 동작하는 form을 작성할 때 얼마나 많이 단순화할 수 있는지 이해하기. </td>
  </tr>
 </tbody>
</table>

<h2 id="개요">개요</h2>

<p><a href="/ko/docs/Web/Guide/HTML/Forms">HTML 폼(Form)</a> 은 웹 페이지상에서 한개 이상의 필드나 위젯들의 묶음을 말하며, 사용자로부터 정보를 수집하여 서버에 제출하는데 사용된다. 다양한 종류의 데이타 입력을 지원하는 위젯들( 텍스트 박스, 체크 박스, 라디오 버튼, 날짜 선택기 등등)이 많이 존재하기 때문에, 폼은 사용자 입력을 수집하는데 유연한 장치라고 할 수 있다. 폼은 또한, 교차 사이트 요청 위조 방지(CSRF protection, cross-site request forgery protection)와 함께 <code>POST</code>요청으로 데이타를 보낼수 있도록 지원하므로, 데이타를 서버와 공유하는데 있어서 비교적 안전한 방법이다.</p>

<p>지금까지 이 튜토리얼에서 우리가 직접 폼을 생성한 적은 없지만, Django 관리 사이트에서 이미 경험해 보았다. 예를 들면, 아래 스크린 샷에서 <a href="/ko/docs/Learn/Server-side/Django/Models">Book</a> 모델중 하나를 편집하는 폼을 보여주고 있는데, 몇개의 선택 목록과 텍스트 에디터를 볼 수 있다.</p>

<p><img alt="Admin Site - Book Add" src="https://mdn.mozillademos.org/files/13979/admin_book_add.png" style="border-style: solid; border-width: 1px; display: block; margin: 0px auto;"></p>

<p>폼을 개발하는 것은 복잡한 작업이 될수도 있다! 개발자는 일단, 폼을 위한 HTML을 작성해야 하며, 서버로 입력된 (아마도 브라우저로도 입력된) 데이타의 유효성을 검증하고 적절하게 수정하도록 하고, 유효하지 않은 입력에 대해서 사용자가 알 수 있도록 폼을 에러 메시지와 함께 다시 표시해야하며,성공적으로 제출된 데이타를 적절히 처리하고, 마지막으로 성공했을 경우 사용자가 알수 있게 응답하도록 개발 해야 한다. <em>Django 폼은 다음과 같은 기능의 프레임워크를 제공하여 이 모든 단계중 많은 부분을 덜어내 준다. 이 프레임워크는 폼과 그에 연관된 필드를 프로그램적으로 정의하여 객체를 만들고, 폼 HTML 코드를 작성하는 작업과 데이타 유효성 검증과 사용자 상호작용에 이 객체들을 사용한다.</em></p>

<p>이번 튜토리얼에서는, 폼을 생성하고 폼으로 작업하는 몇가지 방법을 보여줄 것이다. 특히, 모델을 처리하는 폼을 작성하는데 필요한 작업량을, generic 편집 폼 view를 이용하여 어떻게 획기적으로 줄일 수 있는지 보여줄 것이다. 그 과정에서, 도서관 사서들이 도서관 책 상태를 갱신할 수 있는 폼을 추가하고 책과 저자를 생성, 편집, 삭제할수 있는 페이지를  생성할 것이다. (즉, 위와 같이 책을 편집하는 폼의 기본적인 버전을 다시 개발하는 것이다).</p>

<h2 id="HTML_폼Form_이란">HTML 폼(Form) 이란?</h2>

<p>첫번째로 <a href="/en-US/docs/Learn/HTML/Forms">HTML 폼(Form</a>)에 대한 간단한 개요이다. 어떤 "team"의 이름을 입력하는 단일 텍스트 필드와 관련 라벨을 가진 간단한 HTML 폼을 생각해보자:</p>

<p><img alt="Simple name field example in HTML form" src="https://mdn.mozillademos.org/files/14117/form_example_name_field.png" style="border-style: solid; border-width: 1px; display: block; height: 44px; margin: 0px auto; width: 399px;"></p>

<p>폼은 HTML에서 적어도 한 개 이상의 <code>type="submit"</code>인 <code>input</code> 요소를 포함하는 <code>&lt;form&gt;...&lt;/form&gt;</code> 태그 사이의 요소들의 집합으로 정의된다.</p>

<pre class="brush: html">&lt;form action="/team_name_url/" method="post"&gt;
    &lt;label for="team_name"&gt;Enter name: &lt;/label&gt;
    &lt;input id="team_name" type="text" name="name_field" value="Default name for team."&gt;
    &lt;input type="submit" value="OK"&gt;
&lt;/form&gt;</pre>

<p>위 코드에서는 팀 이름을 입력하기 위한 텍스트 필드를 단지 한개만 가지는데, 폼이 가질수 있는 입력 요소와 관련 라벨의 갯수에는 제한이 없다. 필드의  <code>type</code> 속성은 어떤 종류의 위젯이 표시될지 정의한다.  필드의 <code>name</code>과 <code>id</code> 가 JavaScript/CSS/HTML에 있는 필드를 확인하는데 사용되고 <code>value</code>는 필드가 처음 표시될 때의 초기값을 정의한다. 관련 팀 라벨은 <code style="font-style: normal; font-weight: normal;">label</code>태그(  위 코드에서 "Enter name"을 확인)를 이용해 명시된다.  여기서 <code style="font-style: normal; font-weight: normal;">for</code>필드는 관련된 <code style="font-style: normal; font-weight: normal;">input</code>의  <code style="font-style: normal; font-weight: normal;">id</code>값을 포함하고 있다. </p>

<p><code>submit</code> 타입의 input 태그는 (기본적으로) 사용자가 누를수 있는 버튼으로 표시되는데, 버튼의 동작에 의해 폼의 다른 모든 input 요소의 데이터가 서버로 업로드된다 (위의 경우는 <code>team_name</code>만 업로드된다).  폼 속성으로는 데이터를 보내기 위해 사용되는 HTTP <code>method</code>와 서버상에서 데이타의 목적지를 ( <code>action</code>으로) 정의한다:</p>

<ul>
 <li><code>action</code>: 폼이 제출(submit)될 때 처리가 필요한 데이타를 전달받는 곳의 자원/URL 주소. 설정이 안되면 (혹은 빈 문자열로 설정되면), 폼은 현재 페이지 URL로 다시 제출된다.</li>
 <li><code>method</code>: 데이터를 보내는데 사용되는 HTTP 메소드: <em>post</em> 이거나 <em>get 이다.</em>
  <ul>
   <li><code>POST</code> 메소드는 사이트간 요청 위조 공격에 좀 더 저항성이 좋게 만들 수 있기  때문에, 관련 데이터에 의해 서버 데이터베이스가 변경될 경우에는 항상 사용 되어야 한다. </li>
   <li><code>GET</code> 메소드는 사용자 데이터를 변경하지 않는 폼(예를 들면 , 탐색 폼)에서만 사용되어야 한다. URL을 북마크하길 원하거나 공유하기를 원하는 경우에 추천한다. </li>
  </ul>
 </li>
</ul>

<p>서버의 역할은 첫번째로 - 필드를 비워두거나 초기값으로 채워두도록 - 초기 폼 상태를 표시하는 것이다. 사용자가 제출 버튼을 누른후에, 서버는 웹 브라우저로부터 폼의 데이타를 념겨 받고, 데이타의 유효성 검증을 해야한다. 폼이 유효하지 않은 데이타를 담고 있다면, 서버는 폼을 다시 표기해야 하는데, 이번에는 사용자가 입력한 유효한 데이타는 그대로 표시하며, 유효하지 않은 필드만 경고 메시지와 함께 표기해야 한다. 일단 모든 필드의 데이타가 유효한 폼 데이타의 제출요청을 서버가 받게 되면, 서버는 적절한 동작(예를 들면, 데이타를 저장하거나, 검색결과를 반화하거나, 파일을 업로딩하는 등등의 작업)을 수행하고 사용자에게 알려주게된다.</p>

<p>당신이 상상할 수 있듯이, HTML을 작성하고, 입력된 데이타의 유효성을 검증하고, 필요시에 입력된 데이타를 검증 결과와 함게 다시 표시하며, 유효한 데이타에 대해 요구되는 동작을 수행하는 것은 "올바르게 하기"위해서는 꽤 많은 노력이 필요한 작업이다. Django는 일부 과중한 작업과 반복 코드를 줄여줌으로서, 이 작업을 훨씬 쉽게 만든다!</p>

<h2 id="Django_폼_처리_과정">Django 폼 처리 과정</h2>

<p>Django의 폼 처리 과정은 (모델에 대한 정보를 보여주는데 있어서) 우리가 앞선 튜토리얼에서 배웠던 것과 같은 기술을 사용한다. : 뷰는 요청을 받고, 모델로 부터 데이타를 읽는것을 포함한 요구되는 동작을 수행한다. 그런 다음, (보여줄 데이타를 포함한 context를 전달받은 템플릿으로 부터) HTML page를 생성하고 반환한다. 서버 또한 사용자가 입력한 데이타를 처리가능 해야 하며,  에러가 있으면 그 페이지를 다시 보여줄 필요가 있기 때문에 상황을 더욱 복잡하게 만든다. </p>

<p>아래에 Django가 어떻게 요청읕 처리하는지 보여주는 플로우 차트가 있다. 폼을 포함하는 페이지에 대한 요청 (초록색으로 표시함) 으로 시작하고 있다. </p>

<p><img alt="Updated form handling process doc." src="https://mdn.mozillademos.org/files/14205/Form%20Handling%20-%20Standard.png" style="display: block; height: 569px; margin: 0px auto; width: 800px;"></p>

<p>위의 다이어그램에 기반하여, Django 폼이 주요하게 다루는 것은 다음과 같다. :</p>

<ol>
 <li>사용자가 처음으로 폼을 요청할 때 기본 폼을 보여준다.
  <ul>
   <li>폼은 비어있는 필드가 있을 수 있다 (예를 들면, 새로운 책을 등록할 경우) 아니면 초기값으로 채워진 필드가 있을 수도 있다. ( 예를 들면, 기존의 책을 수정하거나, 흔히 사용하는 초기값이 있을경우)</li>
   <li>이 시점의 폼은 (초기값이 있긴해도) 유저가 입력한 값에 연관되지 않았기에  unbound 상태라고 불린다.</li>
  </ul>
 </li>
 <li>제출 요청으로 부터 데이타를 수집하고 그것을 폼에 결합한다.
  <ul>
   <li>데이타를 폼에 결합(binding) 한다는 것은 사용자 입력 데이타와 유효성을 위반한 경우의 에러메시지가 폼을 재표시할 필요가 있을 때 준비되었다는 의미이다.</li>
  </ul>
 </li>
 <li>데이타를 다듬어서 유효성을 검증한다.
  <ul>
   <li>데이타를 다듬는다는 것은 사용자 입력을 정화(sanitisation) 하고 (예를 들면, 잠재적으로 악의적인 콘덴츠를 서버로 보낼수도 있는 유효하지 않은 문자를 제거하는 것)  python에서 사용하는 타입의 데이타로 변환하는 것이다.</li>
   <li>유효성검증은 입력된 값이 해당 필드에 적절한 값인지 검사한다. (예를 들면, 데이타가 허용된 범위에 있는 값인지, 너무 짧거나 길지 않은지 등등) </li>
  </ul>
 </li>
 <li>입력된 어떤 데이타가 유효하지 않다면, 폼을 다시 표시하는데 이번에는 초기값이 아니라 유저가 입력한 데이타와 문제가 있는 필드의 에러 메시지와 함께 표시한다.</li>
 <li>입력된 모든 데이타가 유효하다면, 요청된 동작을 수행한다. (예를 들면, 데이타를 저장하거나, 이메일을 보내거나, 검색결과를 반환하거나, 파일을 업로딩하는 작업 등등)</li>
 <li>일단 모든 작업이 완료되었다면, 사용자를 새로운 페이지로 보낸다.</li>
</ol>

<p>Django는 위에 설명된 작업을 도와줄 수많은 도구와 접근법을 제공한다. 가장 기초적인 것은 <code>Form</code> 클래스 인데 form HTML의 생성과 데이터 정화와 유효성검증을 간단하게 만든다. 다음 단계에서는, 도서관 사서가 책의 대여갱신을 할수 있도록 해주는 페이지의 실제적인 예제를 이용해 폼이 어떻게 동작하는지 살펴보도록 한다.</p>

<div class="note">
<p><strong>참고사항:</strong>  <code>Form</code> 이 어떻게 사용되는지 이해해두면 Django의 "고급 레벨" 폼 프레임워크 클래스를 논의하는데 도움이 된다.</p>
</div>

<h2 id="책_대여갱신_form과_함수_view">책 대여갱신 form과 함수 view</h2>

<p>다음으로 도서관직원이 대여기간을 갱신할수 있는 페이지를 추가할 것이다. 이 작업을 위해 사용자가 날짜 정보를 입력할 수 있는 form을 생성할 것이다.  그 필드는 현재날짜로 부터 3주의 기간 (일반적인 대여기간)으로 초기화될 것이다. 그리고 도서관직원이 과거날짜를 입력하거나 너무 긴 대여기간을 입력하지 않도록 유효성 체크기능을 추가할 것이다.  유효 날짜가 입력되면, 현재 record의 <code>BookInstance.due_back</code> 필드에 써넣을 것이다.</p>

<p>아래 예제는 함수기반 view와 <code>Form</code> 클래스를 이용할 것이다. 이어지는 내용에서 form 동작 방법과 현재진행중인 LocalLibray 프로젝트에서 변경할 내용을 설명한다.</p>

<h3 id="Form_작성하기">Form 작성하기</h3>

<p><code>Form</code> 클래스는 Django form 관리 시스템의 핵심이다. <code>Form</code> 클래스는 form내 field들, field 배치, 디스플레이 widget, 라벨, 초기값, 유효한 값과 (유효성 체크이후에) 비유효 field에 관련된 에러메시지를 결정한다. <code>Form</code> 클래스는 또한 미리 정의된 포맷(테이블, 리스트 등등) 의 템플릿으로 그자신을 렌더링하는 method나 (세부 조정된 수동 렌더링을 가능케하는) 어떤 요소의 값이라도 얻는 method를 제공한다.</p>

<h4 id="Form_선언하기">Form 선언하기</h4>

<p><code>Form</code> 을 선언하는 문법은 <code>Model</code>을 선언하는 것과 많이 닮았으며, 같은 필드타입을 사용한다. ( 또한 일부 매개변수도 유사하다) . 두가지 경우 모두 각 필드가 데이타에 맞는 (유효성 규칙에 맞춘) 타입인지 확인할 필요가 있고, 각 필드가 보여주고 문서화할 description을 가진다는 것에서 Form과 Model이 유사한 문법으로 구성된다는 점을 납득할 수 있다. </p>

<p>Form 데이타는 어플리케이션 디렉토리 안의 forms.py 파일에 저장되어야 한다. <strong>locallibrary/catalog/forms.py</strong> 파일을 생성하고 열어보자. <code>Form</code>을 생성하기 위해, <code>Form</code>클래스에서 파생된, <code>forms</code>라이브러리를 import 하고 폼 필드를 생성한다. 아래는 도서관 책 갱신 폼에 대한 아주 기본적인 폼 클래스이며 이를 생성한 파일에 추가하자.</p>

<pre class="brush: python">from django import forms

class RenewBookForm(forms.Form):
    renewal_date = forms.DateField(help_text="Enter a date between now and 4 weeks (default 3).")
</pre>

<h4 id="Form_필드">Form 필드</h4>

<p>우리가 구현할 구체적인 내용은 다음과 같다. 대여갱신 날짜를 입력할 한 개의 <code><a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#datefield">DateField</a></code> 를 가지는데, 이 필드는 "Renewal date:"라는 라벨로 초기값 없이 빈 칸으로 HTML에 표시되게 된다. 그리고 다음과 같은 도움문구가 추가 된다: "<em>Enter a date between now and 4 weeks (default 3 weeks).</em>" 따로 추가지정할 선택사항 없이, 이 필드는 Django의 <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#django.forms.DateField.input_formats">input_formats</a>: YYYY-MM-DD (2016-11-06), MM/DD/YYYY (02/26/2016), MM/DD/YY (10/25/16) 을 이용하여 날짜를 입력받는다. 그리고 Django의 기본 <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#widget">widget</a>: <a href="https://docs.djangoproject.com/en/2.0/ref/forms/widgets/#django.forms.DateInput">DateInput</a> 를 이용하여 표시될 것이다.</p>

<p>다음과 같이, 대응되는 모델 필드와 유사성 때문에, 여러분이 의미를 대체로 알만한 수많은 종류의 폼필드가 있다 : <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#booleanfield"><code>BooleanField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#charfield"><code>CharField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#choicefield"><code>ChoiceField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#typedchoicefield"><code>TypedChoiceField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#datefield"><code>DateField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#datetimefield"><code>DateTimeField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#decimalfield"><code>DecimalField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#durationfield"><code>DurationField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#emailfield"><code>EmailField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#filefield"><code>FileField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#filepathfield"><code>FilePathField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#floatfield"><code>FloatField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#imagefield"><code>ImageField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#integerfield"><code>IntegerField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#genericipaddressfield"><code>GenericIPAddressField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#multiplechoicefield"><code>MultipleChoiceField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#typedmultiplechoicefield"><code>TypedMultipleChoiceField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#nullbooleanfield"><code>NullBooleanField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#regexfield"><code>RegexField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#slugfield"><code>SlugField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#timefield"><code>TimeField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#urlfield"><code>URLField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#uuidfield"><code>UUIDField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#combofield"><code>ComboField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#multivaluefield"><code>MultiValueField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#splitdatetimefield"><code>SplitDateTimeField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#modelmultiplechoicefield"><code>ModelMultipleChoiceField</code></a>, <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#modelchoicefield"><code>ModelChoiceField</code></a> .</p>

<p>대부분의 필드에 공통적인 인자들은 아래와 같다. ( 이들은 적절한 기본값을 가지고 있다 ):</p>

<ul>
 <li><a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#required">required</a>: <code>True</code> 로 설정되면, 필드를 빈칸으로 두거나 <code>None</code> 값을 줄 수 없게된다. 보통필드는 required는 True로 기본 설정되므로, 폼에서 빈 칸을 허용하기 위해서는<code>required=False</code> 로 설정해야 한다. </li>
 <li><a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#label">label</a>: HTML에서 필드를 렌더링할때 사용하는 레이블이다. <a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#label">label</a> 이 지정되지 않으면,  Django는 필드 이름에서 첫번째 문자를 대문자로, 밑줄을 공백으로 변형한 레이블을 새로 생성할 것이다. (예를 들면, renewal_date  --&gt; <em>Renewal date</em>).</li>
 <li><a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#label-suffix">label_suffix</a>: 기본적으로, 콜론(:)이 레이블 다음에 표시된다. (예를 들면, Renewal date<strong>:</strong>). 이 인자는 다른 문자(들)를 포함한 접미사를 지정할 수 있도록 해준다.</li>
 <li><a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#initial">initial</a>: 폼이 나타날 때 해당 필드의 초기 값.</li>
 <li><a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#widget">widget</a>: 사용할 디스플레이 위젯.</li>
 <li><a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#help-text">help_text</a> (위의 예에서 봤듯이): 필드 사용법을 보여주는 추가적인 문구.</li>
 <li><a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#error-messages">error_messages</a>: 해당 필드의 에러 메시지 목록. 필요하면 문구를 수정할 수 있다.</li>
 <li><a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#validators">validators</a>: 해당 필드가 유효한 값을 가질 때 호출되는 함수의 목록.</li>
 <li><a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#localize">localize</a>: 폼 데이타 입력의 현지화(localisation)를 허용함 (자세한 정보는 해당 링크 참조).</li>
 <li><a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/#disabled">disabled</a>: 이 옵션이 <code>True</code> 일때 해당 필드를 볼 수는 있지만 편집이 안됨. 기본 값은 <code>False</code>.</li>
</ul>

<h4 id="유효성_체크">유효성 체크</h4>

<p>Django는 데이타의 유효성을 체크할 수 있는 수많은 지점을 제공한다. 어떤 필드의 유효성을 체크하는 가장 쉬운 방법은 해당 필드의  <code>clean_<strong>&lt;fieldname&gt;</strong>()</code> 메소드를  덮어쓰는 것이다. 예를 들면, 입력된 <code>renewal_date</code> 값이 현재로 부터 4 주이후 사이에 있는지는, <code>clean_<strong>renewal_date</strong>()</code> 를 아래와 같이 구현하여 유효성 체크를 수행할 수 있다.</p>



<p>forms.py 파일을 업데이트 하면 아래와 같은 모습이 된다:</p>



<pre class="brush: python"><code><strong>import datetime</strong>

from django import forms
<strong>from django.core.exceptions import ValidationError
from django.utils.translation import ugettext_lazy as _
</strong>
class RenewBookForm(forms.Form):
    renewal_date = forms.DateField(help_text="Enter a date between now and 4 weeks (default 3).")

<strong>    def clean_renewal_date(self):
        data = self.cleaned_data['renewal_date']

        # Check if a date is not in the past.
        if data &lt; datetime.date.today():
            raise ValidationError(_('Invalid date - renewal in past'))

        # Check if a date is in the allowed range (+4 weeks from today).
        if data &gt; datetime.date.today() + datetime.timedelta(weeks=4):
            raise ValidationError(_('Invalid date - renewal more than 4 weeks ahead'))

        # Remember to always return the cleaned data.
        return data</strong></code></pre>

<p>주목해야할 지점이 두개 있다. 첫 번째 지점은 <code>self.cleaned_data['renewal_date']</code> 를 이용하여 데이타를 획득하고 이 데이타의 수정여부에 상관없이 함수가 끝나면 이 데이타를 반환한 다는 것이다. 이 단계는 기본 유효성 검사도구를 이용해 입력값을 "다듬고(cleaned)" 잠재적으로 안전하지 않을 수 있는 입력 값을 정화하며 , 해당 입력값에 맞는 표준 형식으로 변환해준다. ( 이 경우에는 Python  <code>datetime.datetime</code> 객체 형식이다.).</p>

<p>두 번째 지점은 입력값이 지정한 범위를 벗어날 경우 <code>ValidationError</code> 에러를 발생시키고, 유효하지 않은 입력값일 때 폼에 보여주고자 하는 에러 문구를 지정하는 부분이다. 위의 예에서는, <a href="https://docs.djangoproject.com/en/2.0/topics/i18n/translation/">Django의 번역 함수들</a> 중하나인 <code>ugettext_lazy()</code> (<code>_()</code> 로 import 됨)로 이 문구를 감싸고 있는데, 당신의 사이트를 나중에 번역하고자 한다면 좋은 예제가 된다.</p>

<div class="note">
<p><strong>참고사항:</strong> <a href="https://docs.djangoproject.com/en/2.0/ref/forms/validation/">폼과 필드 유효성 체크</a> (장고 문서임) 에 폼의 유효성 체크에 대한 수많은 다른메소드및 예제가 있다. 예를 들면, 서로 의존관계에 있는 여러개의 필드가 있을 경우,  <a href="https://docs.djangoproject.com/en/2.0/ref/forms/api/#django.forms.Form.clean">Form.clean()</a> 함수를 덮어써서,   <code>ValidationError</code> 를 다시 발생시킬수도 있다.</p>
</div>

<p>여기까지가 본 예제에서 필요한 폼에 대한 모든 내용이다!</p>

<h3 id="URL_Configuration_작성하기">URL Configuration 작성하기</h3>

<p>뷰를 생성하기 전에, 책 대여갱신 페이지를 위해 URL 설정을 추가 하자. 아래 설정코드를 <strong>locallibrary/catalog/urls.py </strong>아랫 부분에 복사하라.</p>

<pre class="brush: python">urlpatterns += [
    path('book/&lt;uuid:pk&gt;/renew/', views.renew_book_librarian, name='renew-book-librarian'),
]</pre>

<p>위 URL 설정코드는 <strong>/catalog/book/<em>&lt;bookinstance id&gt;</em>/renew/</strong> 형식의  URL을 <strong>views.py</strong> 에 있는 <code>renew_book_librarian()</code> 라는 이름의 함수를 호출하고  <code>BookInstance</code> id를 <code>pk</code>라고 이름지은 매개변수로 전송한다. 위 패턴은 <code>pk</code>가 정확히 <code>uuid</code>의 형식일때만 일치한다.</p>

<div class="note">
<p><strong>주목할점</strong>: 추출된 URL 데이타 "<code>pk</code>" 는 당신 마음대로 이름을 정할 수 있다. 왜냐하면 view 함수에 대해서는 어떤  조작이라도 가능하기 때문이다.  ( 특정 이름을 기대하는 매개변수를 가진 Generic detail view 클래스를 사용하지 않고 있다.) 하지만 <code>pk</code>는 "primary key"의 약자으로 합리적인 관례상 이름이다 !</p>
</div>

<h3 id="View_작성하기">View 작성하기</h3>

<p>위의 <a href="#django_form_handling_process">Django 폼 처리 과정</a> 에서 설명된대로, 위의 폼 뷰는 첫번째로 호출될 때는 기본 폼을 표시해야 한다. 그리고 나서 데이터가 유효하지 않은 경우 에러 메시지를 재 표시하고, 데이터가 유효한 경우에는 데이타를 처리하고 새로운 페이지를 표시해야 한다. 이런 서로 다른 동작을 수행하기 위해, 해당 뷰가 기본 폼을 표시하도록 현재 첫번째로 호출되고 있는지, 데이터 유효성을 체크하기 위해 연속되어 이어지는 호출인지 알 수 있어야 한다.  </p>

<p>서버에 정보를 제출하는 <code>POST</code>리퀘스트를 사용하는 폼에 대해서, 가장 흔한 패턴은 뷰에서  <code>POST</code> 요청 타입 인지 판단 (<code>if request.method == 'POST':</code>) 하여 유효한 요청 여부를 확인하고 <code>GET</code> ( <code>else</code> 조건으로 ) 요청 타입인 경우 초기 폼 생성을 요청한다. <code>GET</code>요청으로 데이터를 제출하려고 한다면 첫 번째 뷰 호출인지 두 번째 이상의 뷰 호출인지 판단하는 전형적인 접근 방법은 폼 데이터를 읽어보는 (즉 폼에서 숨겨진 값을 읽는)것이다.</p>

<p>책 대여갱신 과정은 데이터베이스에 결과를 보내기 때문에, 관례상 <code>POST</code>요청 방법을 사용한다. 아래 코드는 이런 종류의 function 뷰에 대해 가장 기본적인 형식을 보여준다.</p>

<pre class="brush: python">import datetime

from django.shortcuts import get_object_or_404
from django.http import HttpResponseRedirect
from django.urls import reverse

from catalog.forms import RenewBookForm

def renew_book_librarian(request, pk):
    book_instance = get_object_or_404(BookInstance, pk=pk)

    # POST 요청이면 폼 데이터를 처리한다
<strong>    if request.method == 'POST':</strong>

        # 폼 인스턴스를 생성하고 요청에 의한 데이타로 채운다 (binding):
        book_renewal_form = RenewBookForm(request.POST)

        # 폼이 유효한지 체크한다:
        <strong>if book_renewal_form.is_valid():</strong>
            # form.cleaned_data 데이타를 요청받은대로 처리한다(여기선 그냥 모델 due_back 필드에 써넣는다)
            book_instance.due_back = book_renewal_form.cleaned_data['renewal_date']
            book_instance.save()

            # 새로운 URL로 보낸다:
            return HttpResponseRedirect(reverse('all-borrowed') )

    # GET 요청 (혹은 다른 메소드)이면 기본 폼을 생성한다.
<strong>    else:</strong>
        proposed_renewal_date = datetime.date.today() + datetime.timedelta(weeks=3)
        book_renewal_form = RenewBookForm(initial={'renewal_date': proposed_renewal_date})

    context = {
        'form': book_renewal_form,
        'book_instance': book_instance,
    }

    return render(request, 'catalog/book_renew_librarian.html', context)</pre>

<p>첫부분에서는 미리 작성된 폼 (<code>RenewBookForm</code>)을 import 하고 뷰 함수의 내부에서 쓰일 유용한 객체나 메소드를 import 한다:</p>

<ul>
 <li><code><a href="https://docs.djangoproject.com/en/2.0/topics/http/shortcuts/#get-object-or-404">get_object_or_404()</a></code>: 해당 모델의 기본 키(primary key) 값에 연결되는 특정 객체를 반환하거나 해당 record가 없을경우 <code>Http404</code>예외를 발생시킨다. </li>
 <li><code><a href="https://docs.djangoproject.com/en/2.0/ref/request-response/#django.http.HttpResponseRedirect">HttpResponseRedirect</a></code>: 특정 URL로의 재전송을 생성한다. (HTTP status code 302). </li>
 <li><code><a href="https://docs.djangoproject.com/en/2.0/ref/urlresolvers/#django.urls.reverse">reverse()</a></code>: URL 설정(configuration) 의 이름과 전달인자들로 부터 URL을 만들어낸다.  템플릿에서 사용했던 <code>url</code>태그에 해당하는 파이썬 형식의 동일 표현이다.</li>
 <li><code><a href="https://docs.python.org/3/library/datetime.html">datetime</a></code>: 날짜와 시간을 다루는 파이썬 라이브러리 이다. </li>
</ul>

<p>뷰 코드는 첫번째로 현재 <code>BookInstance</code>를 얻기위해 <code>get_object_or_404()</code>함수에 <code>pk</code> 전달인자를 사용한다( <code>BookInstance</code>가 없으면 뷰는 그 즉시 완료되며 페이지에는 "발견 하지 못함" 에러가 뜨게된다). <code>POST</code>요청이아니라면 ( <code>else</code>절로 처리되어) <code>renewal_date</code>필드에 대해 <code>initial</code>값을 넘겨주는 기본 폼을 생성한다. ( 기본 값은  아래 코드에서 볼드체로 표시된대로, 현재 날짜로 부터 3주후이다). </p>

<pre class="brush: python">    book_instance = get_object_or_404(BookInstance, pk=pk)

    # GET 요청(혹은 다른 메소드)이면 기본 폼을 생성한다.
    <strong>else:</strong>
        proposed_renewal_date = datetime.date.today() + datetime.timedelta(<strong>weeks=3</strong>)
        <strong>book_renewal_form = RenewBookForm(initial={'</strong>renewal_date<strong>': </strong>proposed_renewal_date<strong>})</strong>

    context = {
        'form': book_renewal_form,
        'book_instance': book_instance,
    }

    return render(request, 'catalog/book_renew_librarian.html', context)</pre>

<p>폼을 생성한이후, HTML 페이지를 생성하기 위해 <code>render()</code>를 호출하는데, 이 함수에서 템플릿과 폼을 포함하는 context를 특정한다. 이 경우에 context는 <code>BookInstance</code> 또한 포함하는데, <code>BookInstance</code>는 갱신하고자 하는 책의 정보를 템플릿에 제공하는데 사용한다.</p>

<p>하지만 <code>POST</code>요청이라면, <code>form</code>객체를 생성하고 <code>POST</code>요청에서의 데이터로 <code>form</code>을 채운다. 이 처리과정은 "binding"으로 불리며 폼의 유효성 체크를 할수 있도록 해준다. 여기에서 모든 필드에 관련된 유효성 체크 코드 - 날짜필드가 실제상황에서 유효한 값을 가지는지 체크하는 일반적인 코드와 날짜가 정해진 범위의 값을 가지는지 체크하는 폼의 특별한 함수인 <code>clean_renewal_date()</code> 를 포함하는 코드 -  를 실행하며 폼의 데이타가 유효한지 체크한다.  </p>

<pre class="brush: python">    book_instance = get_object_or_404(BookInstance, pk=pk)

    # POST 요청이면 폼 데이터를 처리한다
    if request.method == 'POST':

        # 폼 인스턴스를 생성하고 요청에 의한 데이타로 채운다 (binding):
<strong>        book_renewal_form = RenewBookForm(request.POST)</strong>

        # 폼이 유효한지 체크한다:
        if book_renewal_form.is_valid():
            # form.cleaned_data 데이타를 요청받은대로 처리한다(여기선 그냥 모델 due_back 필드에 써넣는다)
            book_inst.due_back = form.cleaned_data['renewal_date']
            book_inst.save()

            # 새로운 URL로 보낸다:
            return HttpResponseRedirect(reverse('all-borrowed') )

    context = {
        'form': book_renewal_form,
        'book_instance': book_instance,
    }

    return render(request, 'catalog/book_renew_librarian.html', context)</pre>

<p>폼의 데이터가 유효하지 않다면 <code>render()</code>함수가 다시 호출된다. 하지만 이번에 context로 넘겨지는 폼의 값에는 에러메시지가 포함될 것이다.  </p>

<p>폼의 데이터가 유효하다면, <code>form.cleaned_data</code>속성을 통해 데이타 사용을 시작할수 있다(즉, 다음과 같다. <code>data = form.cleaned_data['renewal_date']</code>). 여기에서는 단지 폼 데이터를 <code>BookInstance</code>객체에 관련된 <code>due_back</code>변수에 저장했다. </p>

<div class="warning">
<p><strong>중요사항</strong>: 'request'객체를 통해 직접 폼 데이터를 가져올수는 있으나 ( 예를 들면 <code>request.POST['renewal_date']</code>나 GET 요청인경우 <code>request.GET['renewal_date']</code>처럼), 이 방식은 <strong>절대</strong> 추천하지 않는다. 위 코드에서 깔끔한 데이타(cleaned_data)란 것은  정제되고(sanitised), 유효성체크가되고, 파이썬에서 많이쓰는 타입의 데이타이다.</p>
</div>

<p>뷰에서 폼 처리의 마지막 단계는 , 대개는 "Success" 페이지라는 다른 페이지로 주소를 바꾸는 것이다. 여기서는 <code>'all-borrowed'</code>라는 뷰( 이 뷰는 <a href="/en-US/docs/Learn/Server-side/Django/authentication_and_sessions#Challenge_yourself">Django 튜토리얼 파트 8: 사용자 인증과 사용권한</a> 파트에서 "도전과제로" 생성했었다) 로 주소를 바꾸기 위해 <code>HttpResponseRedirect</code>와 <code>reverse()</code>를 사용한다. 당신이 이 페이지를 생성하지 않았다면 URL 주소가 '/'인 홈페이지로 주소를 변경하는 것을 고려해보자.</p>

<p>여기까지가 폼을 다루기 위해 필요한 모든 것이지만, 해당 폼 뷰의 사용권한을 도서관사서로 한정해야 하는 문제가 남아있다. <code>BookInstance</code>모델에 "<code>can_renew</code>"라는 새로운 사용권한을 추가해야 하겠지만, 작업을 간단하게 하기위해  그냥 기존의 사용권한<code>can_mark_returned</code>에 함수 데코레이터<code>@permission_required</code>를 사용하도록 하겠다.</p>

<p>그러므로 최종 뷰의 코드는 다음과 같다. 이 코드를 <strong>locallibrary/catalog/views.py</strong> 의 아랫부분에 복사해넣어라.</p>

<pre class="brush: python">import datetime

<strong>from django.contrib.auth.decorators import permission_required</strong>
from django.shortcuts import get_object_or_404
from django.http import HttpResponseRedirect
from django.urls import reverse

from catalog.forms import RenewBookForm

<strong>@permission_required('catalog.<code>can_mark_returned</code>')</strong>
def renew_book_librarian(request, pk):
    """도서관 사서에 의해 특정 BookInstance를 갱신하는 뷰 함수."""
    book_instance = get_object_or_404(BookInstance, pk=pk)

    # POST 요청이면 폼 데이터를 처리한다
    if request.method == 'POST':

        # 폼 인스턴스를 생성하고 요청에 의한 데이타로 채운다 (binding):
        book_renewal_form = RenewBookForm(request.POST)

        # 폼이 유효한지 체크한다:
        if book_renewal_form.is_valid():
            # book_renewal_form.cleaned_data 데이타를 요청받은대로 처리한다(여기선 그냥 모델 due_back 필드에 써넣는다)
            book_instance.due_back = book_renewal_form.cleaned_data['renewal_date']
            book_instance.save()

            # 새로운 URL로 보낸다:
            return HttpResponseRedirect(reverse('all-borrowed') )

    # GET 요청(혹은 다른 메소드)이면 기본 폼을 생성한다.
    else:
        proposed_renewal_date = datetime.date.today() + datetime.timedelta(weeks=3)
        book_renewal_form = RenewBookForm(initial={'renewal_date': proposed_renewal_date})

    context = {
        'form': book_renewal_form,
        'book_instance': book_instance,
    }

    return render(request, 'catalog/book_renew_librarian.html', context)
</pre>

<h3 id="Template_작성하기">Template 작성하기</h3>

<p>뷰 에서 참조되는 템플릿 (<strong>/catalog/templates/catalog/book_renew_librarian.html</strong>)을 생성하고 아래 코드를 복사해넣어라 :</p>

<pre class="brush: html">{% extends "base_generic.html" %}

{% block content %}
    &lt;h1&gt;Renew: \{{ book_instance.book.title }}&lt;/h1&gt;
    &lt;p&gt;Borrower: \{{ book_instance.borrower }}&lt;/p&gt;
    &lt;p{% if book_instance.is_overdue %} class="text-danger"{% endif %}&gt;Due date: \{{book_instance.due_back}}&lt;/p&gt;

<strong>    &lt;form action="" method="post"&gt;
        {% csrf_token %}
        \{{ form.as_table }}
        &lt;input type="submit" value="Submit"&gt;
    &lt;/form&gt;</strong>
{% endblock %}</pre>

<p>이 작업의 대부분은 앞선 튜토리얼에서 익숙해진 작업이다. 우리는 베이스 템플릿을 확장하고 콘텐츠 블럭을 재설정한다.  <code>\{{bookinst}}</code>(와 그에 따른 변수) 가  <code>render()</code> 함수 내의 컨텍스트 객체로 넘겨졌기 때문에 <code>\{{bookinst}}</code>를 참조할수 있다. 이들을 이용해 책 제목, 대여자 그리고 이전 대여마감일의 목록을 열거한다.</p>

<p>폼 코드는 상대적으로 간단하다. 우선 form이 어디에 제출될 것인지(<code>action</code>)(POST인지 PUT인지) 명시하여 <code>form</code> 태그를 선언하고, 데이터를 제출하는 <code>method</code> 를 명시한다(이 경우에는 "HTTP POST") — 해당 페이지 위 쪽의 <a href="#HTML_forms">HTML Forms</a> overview에서 보았듯이,  <code>action</code>을 비워 놓았는데, 이렇게 하면 form 데이터가 현재 URL페이지로 다시 POST 된다(지금 우리가 하고자 하는 것입니다!). <code>form</code> 태그 안에는 <code>submit</code> input 태그 또한 만들어서 페이지 사용자가 눌러서 데이터를 제출(submit)할 수 있도록 한다. <code>form</code> 태그 안에정의된 또 다른 하나인 <code>{% csrf_token %}</code>는 Django의 cross-site 위조 방지의 방식 중 하나이다. </p>

<div class="note">
<p><strong>Note:</strong> Add the <code>{% csrf_token %}</code> to every Django template you create that uses <code>POST</code> to submit data. This will reduce the chance of forms being hijacked by malicious users.</p>
</div>

<p>마지막으로 템플릿에 context라는 dictionary형 데이터로 넘기는 <code>\{{form}}</code> 변수가 남았다. 별로 놀랍지 않을 수 있지만, 아래처럼 하면 form의 모든 field의 필드, 위젯, 도움말을 함께 렌더링하는 기본 렌더링기능을 사용할 수 있다 — 렌더링된 결과는 다음과 같다.</p>

<pre class="brush: html">&lt;tr&gt;
  &lt;t&gt;&lt;label for="id_renewal_date"&gt;Renewal date:&lt;/label&gt;&lt;/th&gt;
  &lt;td&gt;
    &lt;input id="id_renewal_date" name="renewal_date" type="text" value="2016-11-08" required /&gt;
    &lt;br /&gt;
    &lt;span class="helptext"&gt;Enter date between now and 4 weeks (default 3 weeks).&lt;/span&gt;
  &lt;/td&gt;
&lt;/tr&gt;
</pre>

<div class="note">
<p><strong>Note:</strong> 필드가 하나만 있기 때문에 분명하지는 않지만 기본적으로 모든 필드는 자체 테이블 행에 정의되어 있습니다. 템플릿 변수 <code>\{{ form.as_table }}</code>을 참조하면이 동일한 렌더링이 제공됩니다. </p>
</div>

<p>유효하지 않은 날짜를 입력하는 경우 페이지에서 렌더링 된 오류 목록 (아래 굵게 표시)을 얻게됩니다.</p>

<pre class="brush: html">&lt;tr&gt;
  &lt;th&gt;&lt;label for="id_renewal_date"&gt;Renewal date:&lt;/label&gt;&lt;/th&gt;
   &lt;td&gt;
<strong>      &lt;ul class="errorlist"&gt;
        &lt;li&gt;Invalid date - renewal in past&lt;/li&gt;
      &lt;/ul&gt;</strong>
      &lt;input id="id_renewal_date" name="renewal_date" type="text" value="2015-11-08" required /&gt;
      &lt;br /&gt;
      &lt;span class="helptext"&gt;Enter date between now and 4 weeks (default 3 weeks).&lt;/span&gt;
    &lt;/td&gt;
&lt;/tr&gt;</pre>

<h4 id="Form_template_variable을_사용하는_다른_방법">Form template variable을 사용하는 다른 방법</h4>

<p>위와 같이 <code>\{{form.as_table</code><code>}}</code> 을 사용하면 각 필드가 테이블 행으로 렌더링됩니다. 또한 각 필드를 <code>\{{form.as_ul}}</code> 을 사용하여 목록항목(list item)으로 렌더링하거나 <code>\{{form.as_p}}</code>를 사용하여 단락(paragraph)으로 렌더링 할 수도 있습니다.</p>

<p>또한 dot notation을 사용하여 form 속성을 인덱싱하여 각 부분 렌더링을 완벽하게 제어 할 수도 있습니다. 예를 들어, <code>renewal_date</code> 필드에 대한 여러 개의 개별 항목에 접근 할 수 있습니다.</p>

<ul>
 <li><code>\{{form.renewal_date}}:</code> The whole field.</li>
 <li><code>\{{form.renewal_date.errors}}</code>: The list of errors.</li>
 <li><code>\{{form.renewal_date.id_for_label}}</code>: The id of the label.</li>
 <li><code>\{{form.renewal_date.help_text}}</code>: The field help text.</li>
</ul>

<p>템플릿의 양식을 수동으로 렌더링하고 템플릿 필드를 동적으로 반복하는 방법에 대한 자세한 예제는, <a href="https://docs.djangoproject.com/en/2.0/topics/forms/#rendering-fields-manually">Working with forms &gt; Rendering fields manually</a> (Django docs)를 참고.</p>

<h3 id="Page를_시험하기">Page를 시험하기</h3>

<p>If you accepted the "challenge" in <a href="/en-US/docs/Learn/Server-side/Django/authentication_and_sessions#Challenge_yourself">Django Tutorial Part 8: User authentication and permissions</a> you'll have a list of all books on loan in the library, which is only visible to library staff. We can add a link to our renew page next to each item using the template code below.</p>

<pre class="brush: html">{% if perms.catalog.can_mark_returned %}- &lt;a href="{% url 'renew-book-librarian' bookinst.id %}"&gt;Renew&lt;/a&gt;  {% endif %}</pre>

<div class="note">
<p><strong>Note</strong>: Remember that your test login will need to have the permission "<code>catalog.can_mark_returned</code>" in order to access the renew book page (perhaps use your superuser account).</p>
</div>

<p>You can alternatively manually construct a test URL like this — <a href="http://127.0.0.1:8000/catalog/book/&lt;bookinstance id>/renew/">http://127.0.0.1:8000/catalog/book/<em>&lt;bookinstance_id&gt;</em>/renew/</a> (a valid bookinstance id can be obtained by navigating to a book detail page in your library, and copying the <code>id</code> field).</p>

<h3 id="What_does_it_look_like">What does it look like?</h3>

<p>If you are successful, the default form will look like this:</p>

<p><img alt="" src="https://mdn.mozillademos.org/files/14209/forms_example_renew_default.png" style="border-style: solid; border-width: 1px; display: block; height: 292px; margin: 0px auto; width: 680px;"></p>

<p>The form with an invalid value entered, will look like this:</p>

<p><img alt="" src="https://mdn.mozillademos.org/files/14211/forms_example_renew_invalid.png" style="border-style: solid; border-width: 1px; display: block; height: 290px; margin: 0px auto; width: 658px;"></p>

<p>The list of all books with renew links will look like this:</p>

<p><img alt="" src="https://mdn.mozillademos.org/files/14207/forms_example_renew_allbooks.png" style="border-style: solid; border-width: 1px; display: block; height: 256px; margin: 0px auto; width: 613px;"></p>

<h2 id="ModelForms">ModelForms</h2>

<p>Creating a <code>Form</code> class using the approach described above is very flexible, allowing you to create whatever sort of form page you like and associate it with any model or models.</p>

<p>However if you just need a form to map the fields of a <em>single</em> model then your model will already define most of the information that you need in your form: fields, labels, help text, etc. Rather than recreating the model definitions in your form, it is easier to use the <a href="https://docs.djangoproject.com/en/2.0/topics/forms/modelforms/">ModelForm</a> helper class to create the form from your model. This <code>ModelForm</code> can then be used within your views in exactly the same way as an ordinary <code>Form</code>.</p>

<p>A basic <code>ModelForm</code> containing the same field as our original <code>RenewBookForm</code> is shown below. All you need to do to create the form is add <code>class Meta</code> with the associated <code>model</code> (<code>BookInstance</code>) and a list of the model <code>fields</code> to include in the form (you can include all fields using <code>fields = '__all__'</code>, or you can use <code>exclude</code> (instead of <code>fields</code>) to specify the fields <em>not </em>to include from the model).</p>

<pre class="brush: python">from django.forms import ModelForm
from .models import BookInstance

class RenewBookModelForm(ModelForm):
<strong>    class Meta:
        model = BookInstance
        fields = ['due_back',]</strong>
</pre>

<div class="note">
<p><strong>Note</strong>: This might not look like all that much simpler than just using a <code>Form</code> (and it isn't in this case, because we just have one field). However if you have a lot of fields, it can reduce the amount of code quite significantly!</p>
</div>

<p>The rest of the information comes from the model field definitions (e.g. labels, widgets, help text, error messages). If these aren't quite right, then we can override them in our <code>class Meta</code>, specifying a dictionary containing the field to change and its new value. For example, in this form we might want a label for our field of "<em>Renewal date</em>" (rather than the default based on the field name: <em>Due date</em>), and we also want our help text to be specific to this use case. The <code>Meta</code> below shows you how to override these fields, and you can similarly set <code>widgets</code> and <code>error_messages</code> if the defaults aren't sufficient.</p>

<pre class="brush: python">class Meta:
    model = BookInstance
    fields = ['due_back',]
<strong>    labels = { 'due_back': _('Renewal date'), }
    help_texts = { 'due_back': _('Enter a date between now and 4 weeks (default 3).'), } </strong>
</pre>

<p>To add validation you can use the same approach as for a normal <code>Form</code> — you define a function named <code>clean_<em>field_name</em>()</code> and raise <code>ValidationError</code> exceptions for invalid values. The only difference with respect to our original form is that the model field is named <code>due_back</code> and not "<code>renewal_date</code>".</p>

<pre class="brush: python">from django.forms import ModelForm
from .models import BookInstance

class RenewBookModelForm(ModelForm):
<strong>    def clean_due_back(self):
       data = self.cleaned_data['due_back']

       #Check date is not in past.
       if data &lt; datetime.date.today():
           raise ValidationError(_('Invalid date - renewal in past'))

       #Check date is in range librarian allowed to change (+4 weeks)
       if data &gt; datetime.date.today() + datetime.timedelta(weeks=4):
           raise ValidationError(_('Invalid date - renewal more than 4 weeks ahead'))

       # Remember to always return the cleaned data.
       return data
</strong>
    class Meta:
        model = BookInstance
        fields = ['due_back',]
        labels = { 'due_back': _('Renewal date'), }
        help_texts = { 'due_back': _('Enter a date between now and 4 weeks (default 3).'), }
</pre>

<p>The class <code>RenewBookModelForm</code> below is now functionally equivalent to our original <code>RenewBookForm</code>. You could import and use it wherever you currently use <code>RenewBookForm</code>.</p>

<h2 id="Generic_editing_views">Generic editing views</h2>

<p>The form handling algorithm we used in our function view example above represents an extremely common pattern in form editing views. Django abstracts much of this "boilerplate" for you, by creating <a href="https://docs.djangoproject.com/en/2.0/ref/class-based-views/generic-editing/">generic editing views</a> for creating, editing, and deleting views based on models. Not only do these handle the "view" behaviour, but they automatically create the form class (a <code>ModelForm</code>) for you from the model.</p>

<div class="note">
<p><strong>Note: </strong>In addition to the editing views described here, there is also a <a href="https://docs.djangoproject.com/en/2.0/ref/class-based-views/generic-editing/#formview">FormView</a> class, which lies somewhere between our function view and the other generic views in terms of "flexibility" vs "coding effort". Using <code>FormView</code> you still need to create your <code>Form</code>, but you don't have to implement all of the standard form-handling pattern. Instead you just have to provide an implementation of the function that will be called once the submitted is known to be be valid.</p>
</div>

<p>In this section we're going to use generic editing views to create pages to add functionality to create, edit, and delete <code>Author</code> records from our library — effectively providing a basic reimplementation of parts of the Admin site (this could be useful if you need to offer admin functionality in a more flexible way that can be provided by the admin site).</p>

<h3 id="Views">Views</h3>

<p>Open the views file (<strong>locallibrary/catalog/views.py</strong>) and append the following code block to the bottom of it:</p>

<pre class="brush: python">from django.views.generic.edit import CreateView, UpdateView, DeleteView
from django.urls import reverse_lazy
from .models import Author

class AuthorCreate(CreateView):
    model = Author
    fields = '__all__'
    initial={'date_of_death':'05/01/2018',}

class AuthorUpdate(UpdateView):
    model = Author
    fields = ['first_name','last_name','date_of_birth','date_of_death']

class AuthorDelete(DeleteView):
    model = Author
    success_url = reverse_lazy('authors')</pre>

<p>As you can see, to create the views you need to derive from <code>CreateView</code>, <code>UpdateView</code>, and <code>DeleteView</code> (respectively) and then define the associated model.</p>

<p>For the "create" and "update" cases you also need to specify the fields to display in the form (using in same syntax as for <code>ModelForm</code>). In this case we show both the syntax to display "all" fields, and how you can list them individually. You can also specify initial values for each of the fields using a dictionary of <em>field_name</em>/<em>value</em> pairs (here we arbitrarily set the date of death for demonstration purposes — you might want to remove that!). By default these views will redirect on success to a page displaying the newly created/edited model item, which in our case will be the author detail view we created in a previous tutorial. You can specify an alternative redirect location by explicitly declaring parameter <code>success_url</code> (as done for the <code>AuthorDelete</code> class).</p>

<p>The <code>AuthorDelete</code> class doesn't need to display any of the fields, so these don't need to be specified. You do however need to specify the <code>success_url</code>, because there is no obvious default value for Django to use. In this case we use the <code><a href="https://docs.djangoproject.com/en/2.0/ref/urlresolvers/#reverse-lazy">reverse_lazy()</a></code> function to redirect to our author list after an author has been deleted — <code>reverse_lazy()</code> is a lazily executed version of <code>reverse()</code>, used here because we're providing a URL to a class-based view attribute.</p>

<h3 id="Templates">Templates</h3>

<p>The "create" and "update" views use the same template by default, which will be named after your model: <em>model_name</em><strong>_form.html</strong> (you can change the suffix to something other than <strong>_form</strong> using the <code>template_name_suffix</code> field in your view, e.g. <code>template_name_suffix = '_other_suffix'</code>)</p>

<p>Create the template file <strong>locallibrary/catalog/templates/catalog/author_form.html</strong> and copy in the text below.</p>

<pre class="brush: html">{% extends "base_generic.html" %}

{% block content %}

&lt;form action="" method="post"&gt;
    {% csrf_token %}
    &lt;table&gt;
    \{{ form.as_table }}
    &lt;/table&gt;
    &lt;input type="submit" value="Submit" /&gt;

&lt;/form&gt;
{% endblock %}</pre>

<p>This is similar to our previous forms, and renders the fields using a table. Note also how again we declare the <code>{% csrf_token %}</code> to ensure that our forms are resistant to CSRF attacks.</p>

<p>The "delete" view expects to find a template named with the format <em>model_name</em><strong>_confirm_delete.html</strong> (again, you can change the suffix using <code>template_name_suffix</code> in your view). Create the template file <strong>locallibrary/catalog/templates/catalog/author_confirm_delete</strong><strong>.html</strong> and copy in the text below.</p>

<pre class="brush: html">{% extends "base_generic.html" %}

{% block content %}

&lt;h1&gt;Delete Author&lt;/h1&gt;

&lt;p&gt;Are you sure you want to delete the author: \{{ author }}?&lt;/p&gt;

&lt;form action="" method="POST"&gt;
  {% csrf_token %}
  &lt;input type="submit" action="" value="Yes, delete." /&gt;
&lt;/form&gt;

{% endblock %}
</pre>

<h3 id="URL_configurations">URL configurations</h3>

<p>Open your URL configuration file (<strong>locallibrary/catalog/urls.py</strong>) and add the following configuration to the bottom of the file:</p>

<pre class="brush: python">urlpatterns += [
    path('author/create/', views.AuthorCreate.as_view(), name='author_create'),
    path('author/&lt;int:pk&gt;/update/', views.AuthorUpdate.as_view(), name='author_update'),
    path('author/&lt;int:pk&gt;/delete/', views.AuthorDelete.as_view(), name='author_delete'),
]</pre>

<p>There is nothing particularly new here! You can see that the views are classes, and must hence be called via <code>.as_view()</code>, and you should be able to recognise the URL patterns in each case. We must use <code>pk</code> as the name for our captured primary key value, as this is the parameter name expected by the view classes.</p>

<p>The author create, update, and delete pages are now ready to test (we won't bother hooking them into the site sidebar in this case, although you can do so if you wish).</p>

<div class="note">
<p><strong>Note</strong>: Observant users will have noticed that we didn't do anything to prevent unauthorised users from accessing the pages! We leave that as an exercise for you (hint: you could use the <code>PermissionRequiredMixin</code> and either create a new permission or reuse our <code>can_mark_returned</code> permission).</p>
</div>

<h3 id="Testing_the_page">Testing the page</h3>

<p>First login to the site with an account that has whatever permissions you decided are needed to access the author editing pages.</p>

<p>Then navigate to the author create page: <a href="http://127.0.0.1:8000/catalog/author/create/">http://127.0.0.1:8000/catalog/author/create/</a>, which should look like the screenshot below.</p>

<p><img alt="Form Example: Create Author" src="https://mdn.mozillademos.org/files/14223/forms_example_create_author.png" style="border-style: solid; border-width: 1px; display: block; height: 184px; margin: 0px auto; width: 645px;"></p>

<p>Enter values for the fields and then press <strong>Submit</strong> to save the author record. You should now be taken to a detail view for your new author, with a URL of something like <em>http://127.0.0.1:8000/catalog/author/10</em>.</p>

<p>You can test editing records by appending <em>/update/</em> to the end of the detail view URL (e.g. <em>http://127.0.0.1:8000/catalog/author/10/update/</em>) — we don't show a screenshot, because it looks just like the "create" page!</p>

<p>Last of all we can delete the page, by appending delete to the end of the author detail-view URL (e.g. <em>http://127.0.0.1:8000/catalog/author/10/delete/</em>). Django should display the delete page shown below. Press <strong>Yes, delete.</strong> to remove the record and be taken to the list of all authors.</p>

<p><img alt="" src="https://mdn.mozillademos.org/files/14221/forms_example_delete_author.png" style="border-style: solid; border-width: 1px; display: block; height: 194px; margin: 0px auto; width: 561px;"></p>



<h2 id="Challenge_yourself">Challenge yourself</h2>

<p>Create some forms to create, edit and delete <code>Book</code> records. You can use exactly the same structure as for <code>Authors</code>. If your <strong>book_form.html</strong> template is just a copy-renamed version of the <strong>author_form.html</strong> template, then the new "create book" page will look like the screenshot below:</p>

<p><img alt="" src="https://mdn.mozillademos.org/files/14225/forms_example_create_book.png" style="border-style: solid; border-width: 1px; display: block; height: 521px; margin: 0px auto; width: 595px;"></p>

<ul>
</ul>

<h2 id="Summary">Summary</h2>

<p>Creating and handling forms can be a complicated process! Django makes it much easier by providing programmatic mechanisms to declare, render and validate forms. Furthermore, Django provides generic form editing views that can do <em>almost all</em> the work to define pages that can create, edit, and delete records associated with a single model instance.</p>

<p>There is a lot more that can be done with forms (check out our See also list below), but you should now understand how to add basic forms and form-handling code to your own websites.</p>

<h2 id="See_also">See also</h2>

<ul>
 <li><a href="https://docs.djangoproject.com/en/2.0/topics/forms/">Working with forms</a> (Django docs)</li>
 <li><a href="https://docs.djangoproject.com/en/2.0/intro/tutorial04/#write-a-simple-form">Writing your first Django app, part 4 &gt; Writing a simple form</a> (Django docs)</li>
 <li><a href="https://docs.djangoproject.com/en/2.0/ref/forms/api/">The Forms API</a> (Django docs)</li>
 <li><a href="https://docs.djangoproject.com/en/2.0/ref/forms/fields/">Form fields</a> (Django docs) </li>
 <li><a href="https://docs.djangoproject.com/en/2.0/ref/forms/validation/">Form and field validation</a> (Django docs)</li>
 <li><a href="https://docs.djangoproject.com/en/2.0/topics/class-based-views/generic-editing/">Form handling with class-based views</a> (Django docs)</li>
 <li><a href="https://docs.djangoproject.com/en/2.0/topics/forms/modelforms/">Creating forms from models</a> (Django docs)</li>
 <li><a href="https://docs.djangoproject.com/en/2.0/ref/class-based-views/generic-editing/">Generic editing views</a> (Django docs)</li>
</ul>

<p>{{PreviousMenuNext("Learn/Server-side/Django/authentication_and_sessions", "Learn/Server-side/Django/Testing", "Learn/Server-side/Django")}}</p>



<h2 id="In_this_module">In this module</h2>

<ul>
 <li><a href="/en-US/docs/Learn/Server-side/Django/Introduction">Django introduction</a></li>
 <li><a href="/en-US/docs/Learn/Server-side/Django/development_environment">Setting up a Django development environment</a></li>
 <li><a href="/en-US/docs/Learn/Server-side/Django/Tutorial_local_library_website">Django Tutorial: The Local Library website</a></li>
 <li><a href="/en-US/docs/Learn/Server-side/Django/skeleton_website">Django Tutorial Part 2: Creating a skeleton website</a></li>
 <li><a href="/en-US/docs/Learn/Server-side/Django/Models">Django Tutorial Part 3: Using models</a></li>
 <li><a href="/en-US/docs/Learn/Server-side/Django/Admin_site">Django Tutorial Part 4: Django admin site</a></li>
 <li><a href="/en-US/docs/Learn/Server-side/Django/Home_page">Django Tutorial Part 5: Creating our home page</a></li>
 <li><a href="/en-US/docs/Learn/Server-side/Django/Generic_views">Django Tutorial Part 6: Generic list and detail views</a></li>
 <li><a href="/en-US/docs/Learn/Server-side/Django/Sessions">Django Tutorial Part 7: Sessions framework</a></li>
 <li><a href="/en-US/docs/Learn/Server-side/Django/Authentication">Django Tutorial Part 8: User authentication and permissions</a></li>
 <li><a href="/en-US/docs/Learn/Server-side/Django/Forms">Django Tutorial Part 9: Working with forms</a></li>
 <li><a href="/en-US/docs/Learn/Server-side/Django/Testing">Django Tutorial Part 10: Testing a Django web application</a></li>
 <li><a href="/en-US/docs/Learn/Server-side/Django/Deployment">Django Tutorial Part 11: Deploying Django to production</a></li>
 <li><a href="/en-US/docs/Learn/Server-side/Django/web_application_security">Django web application security</a></li>
 <li><a href="/en-US/docs/Learn/Server-side/Django/django_assessment_blog">DIY Django mini blog</a></li>
</ul>