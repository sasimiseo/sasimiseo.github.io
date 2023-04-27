---
layout: single
title: "클릭이벤트의 종류"
---
## 마우스클릭 event


|이벤트 종류|발동 조건|
|:---:|:---|
|[click](#click)|좌클릭 시 발동|
|[mousedown / mouseup](#mousedown / mouseup)|클릭하여 눌렀을 시, 뗏을 시|
|[dblclick](#dblclick)|빠르게 2번 좌클릭시|
|[contextmenu](#contextmenu)|우클릭 시 발동
|[mousemove](#mousemove)|커서를 움직였을 시
|[mouseover / mouseout](#mouseover / mouseout )|커서가 요소 안으로 들어왔을 시, 나갔을 시&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

### click

<iframe height="250" style="width: 100%;" scrolling="no" title="eventMouseUp/Down" src="https://codepen.io/sasimi_seo/embed/ZEqyzdz?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/sasimi_seo/pen/ZEqyzdz">
  eventMouseUp/Down</a> by Seo YooJoon (<a href="https://codepen.io/sasimi_seo">@sasimi_seo</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

마우스의 왼쪽 버튼을 클릭하여 mouseup과 mousedown이 연달아 실행되었을 때 발동한다.

### mousedown / mouseup

<iframe height="250" style="width: 100%;" scrolling="no" title="eventMouseUp/Down" src="https://codepen.io/sasimi_seo/embed/BaqZaBP?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/sasimi_seo/pen/BaqZaBP">
  eventMouseUp/Down</a> by Seo YooJoon (<a href="https://codepen.io/sasimi_seo">@sasimi_seo</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

마우스를 클릭하여 누를 때, 누른 버튼을 뗄 때 발동한다.

###   dblclick

<iframe height="250" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/sasimi_seo/embed/KKGqKpL?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/sasimi_seo/pen/KKGqKpL">
  Untitled</a> by Seo YooJoon (<a href="https://codepen.io/sasimi_seo">@sasimi_seo</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

마우스 왼쪽 버튼을 빠르게 2번 클릭하였을 때 발동한다.

### contextmenu

<iframe height="250" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/sasimi_seo/embed/GRYERvX?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/sasimi_seo/pen/GRYERvX">
  Untitled</a> by Seo YooJoon (<a href="https://codepen.io/sasimi_seo">@sasimi_seo</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

마우스 오른쪽을 클릭 시 발동한다.

### mousemove

<iframe height="250" style="width: 100%;" scrolling="no" title="eventMouseMove" src="https://codepen.io/sasimi_seo/embed/wvYevKQ?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/sasimi_seo/pen/wvYevKQ">
  eventMouseMove</a> by Seo YooJoon (<a href="https://codepen.io/sasimi_seo">@sasimi_seo</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

마우스를 움직일 때 발동한다.

### mouseover / mouseout

<iframe height="250" style="width: 100%;" scrolling="no" title="eventMouseOver/Out" src="https://codepen.io/sasimi_seo/embed/rNqwNeO?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/sasimi_seo/pen/rNqwNeO">
  eventMouseOver/Out</a> by Seo YooJoon (<a href="https://codepen.io/sasimi_seo">@sasimi_seo</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

마우스 커서가 해당 요소 안으로 들어왔을 때, 요소 안에있는 커서가 요소 밖으로 나갔을 때 발동한다.
비슷한 이벤트로 mouseenter / mouseleave 이 있다. 차이점은 자식요소는 발동하지 않는다는 점이다.
