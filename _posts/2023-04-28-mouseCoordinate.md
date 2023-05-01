---
layout: single
title: "마우스 좌표"
---

<iframe height="370" style="width: 100%;" scrolling="no" title="MouseCoordinates" src="https://codepen.io/sasimi_seo/embed/YzJQRqx?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/sasimi_seo/pen/YzJQRqx">
  MouseCoordinates</a> by Seo YooJoon (<a href="https://codepen.io/sasimi_seo">@sasimi_seo</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

### offsetX, offsetY
해당 이벤트가 할당되어 있는 DOM 노드의 안쪽 여백을 기준으로 좌표를 표시한다.
노드의 좌측상단 모서리가 (0, 0) 이다.

### screenX, screenY
사용자의 모니터 화면을 기준으로 좌표를 표시한다.

### clientX, clientY
사용자에게 보여지는 화면을 기준으로 좌표를 표시한다.
커서가 같은자리에 위치해있고 스크롤 될 때 해당 좌표는 변하지않는다.

### screenX, screenY
전체 문서를 기준으로 좌표를 표시한다.
커서가 같은자리에 위치해잇고 스크롤 될 때 pageY값은 변경된다.

[![Coordinate](https://github.com/sasimiseo/sasimiseo.github.io/blob/master/_posts/post_images/2023-05-01-mouseCoordinate.png?raw=true "mouseCoordinate")](https://raw.githubusercontent.com/sasimiseo/sasimiseo.github.io/master/_posts/post_images/2023-05-01-mouseCoordinate "mouseCoordinate")
