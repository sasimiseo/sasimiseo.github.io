---
layout: single
title: "pointer-events 포인터 이벤트 제어 프로퍼티"
---

pointer-events 프로퍼티는 핸들러 된 이벤트, :hover 셀렉터 등 할당된 포인터 이벤트의 작동을 제어할 수 있다.


##### auto
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;pointer-events가 지정되지 않은 것처럼 기본의 기능을 한다. 요소의 포인터 이벤트들은 활성화 된다. 
##### none
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;요소에 할당된 포인터 이벤트들을 비활성화 시킨다.  자손 요소에 pointer-events 값이 지정되어 있을 경우 자손 요소는 그대로 활성화 된 상태일 수도 있다.
##### inherit
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;부모의 pointer-events 값을 상속받는다.



<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/sasimi_seo/embed/WNaZEav?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/sasimi_seo/pen/WNaZEav">
  Untitled</a> by Seo YooJoon (<a href="https://codepen.io/sasimi_seo">@sasimi_seo</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

버튼을 클릭 시 pointer-events의 값은 none으로 지정된다.
아래의 텍스트는 현재의 pointer-events의 값을 불러온 것이고 클릭 시 pointer-events의 값은 none / auto 로 전환된다.
