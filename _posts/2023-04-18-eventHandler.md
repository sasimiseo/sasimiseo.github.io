---
layout: single
title: "이벤트 핸들러"
---

## 이벤트 핸들러

이벤트를 발동시킬려면 핸들러를 할당해야한다.
### HTML 속성

	<input value="클릭해 주세요." onclick="alert('클릭!')" type="button">

<input value="클릭해 주세요." onclick="alert('클릭!')" type="button">

### DOM 프로퍼티

    <input id="elem" type="button" value="클릭해 주세요.">
    <script>
      elem.onclick = function() {
        alert('감사합니다.');
      };
    </script>
<input id="elem" type="button" value="클릭해 주세요.">
<script>
  elem.onclick = function() {
    alert('감사합니다.');
  };
</script>

### addEventListener
HTML 속성과 DOM 프로퍼티의 할당 방식으로는 복수의 이벤트 핸들러를 할당 할 수 없다.
핸들러를 여러개 할당 하려면 이 방식을 사용한다.

	element.addEventListener(event, handler, [options]);
	
event는 이벤트의 이름을 handler에는 이벤트 함수를 할당한다.
