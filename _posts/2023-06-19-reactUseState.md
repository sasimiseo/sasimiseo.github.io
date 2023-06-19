---
layout: single
title: "React useState"
---
리액트는 다양한 종류의 hook을 제공하는데, 그 중 하나인 useState에 대한 내용을 서술한다.
useState는 리액트 컴포넌트에서 동적인 값의 상태(state)를  간편하게 생성하고 업데이트 하는 기능을 가지고있다. 아래에 나열할 특징들을 축약해서 표현하면 state는 동적인 변수이다.

#### Import

	import React, { useState } from 'react';

사용전 react 패키지에서 useState를 불러온다.

#### useState 선언

    const [value, setValue] = useState(초기값);
	
첫번째 요소에서 state를 저장할 변수의 이름을 설정한다. (value)
두번째 요소에서 state를 재선언할때 사용할 함수의 이름을 설정한다. (setValue)
마지막으로 state의 초기값을 설정한다. (useState(초기값))

#### useState 재선언
state를 재선언 하는 방법은 일반 변수를 재선언하는 방식과 다르다.

	setValue(9);
	
선언할 때 설정한 재선언 함수를 사용하여야 한다.
변수와 다르게 재선언 될때마다 랜더링된다. 이해가 안된다면 일반 변수와 차이점을 확인해보자.

<iframe src="https://codesandbox.io/embed/sleepy-fog-c8tmpt?fontsize=14&hidenavigation=1&theme=light"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="reactUseState"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>

