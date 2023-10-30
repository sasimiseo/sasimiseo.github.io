---
layout: single
title: Pagination
---

https://codepen.io/challenges/2023/september/1
기존의 코드에서 DOMContentLoaded 이벤트 리스너를 사용하여 페이지 로딩중에 DOM을 조작하는 Javascript가 실행되는 것을 방지하는 방법과 button의 disabled 속성은 기존에는 알지 못했던 유익한 정보였다.

예제로 작성된 페이지네이션에 페이지가 전환될 때에 각각의 li 요소들을 옆으로 이동시키는 애니메이션을 적용하였다. 

<iframe height="400" style="width: 100%;" scrolling="no" title="Pagination" src="https://codepen.io/sasimi_seo/embed/wvNvZOx?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/sasimi_seo/pen/wvNvZOx">
  Pagination</a> by Seo YooJoon (<a href="https://codepen.io/sasimi_seo">@sasimi_seo</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

li 요소들에게 시간차로 각각 애니메이션을 적용하기 위해 page별로 렌더링되던 방식을 5개의 li가 렌더링 되는 방식으로 변경하였다. 하지만 for을 사용하여 timeout을 5번 반복하도록 함수를 작성하였지만 원하는 방식대로 애니메이션 사이에 딜레이를 적용되지 않았다.
이 문제가 콜백함수의 비동기처리에 의한 것임을 알고 async/await을 사용하여 해당 코드를 동기적으로 실행되게끔 변경하였다. 
요소들을 .vegetable 너머로 이동시켜 overflow: hidden 을 사용하여 숨기는 방식을 사용했는데 이 방식은 요소들이 여전히 DOM에 존재하고 렌더링 되기때문에 이동후에 display: none을 사용하여 DOM에 완전히 제거시켜 메모리 소모량과 렌더링 속도를 줄일수있을 것 같다.
