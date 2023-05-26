---
layout: single
title: "React 조건부 렌더링 4가지 방법"
---

조건부 렌더링은 조건에 따라 각기 다른 결과물을 화면에 출력하는 것이다. 여기선 if문, 삼항연산자( ? : ), 논리연산자( && ), 변수를 사용한 조건부 렌더링 방법 4가지를 나열한다.

#### if문

    function Item({ name, isRead }) {
      if (isRead) {
        return <li className="item">{name}✔</li>;
      }
      return <li className="item">{name}</li>;
    }

isRead라는 이름의 props값을 불러들여 true라면 name props 뒤에 ✔ 를 출력,
그렇지 않다면 name props의 값만을 출력한다.

<iframe src="https://codesandbox.io/embed/reactconren-6xpvq3?fontsize=14&hidenavigation=1&theme=light"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="reactConRen(if)"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>
   
위의 예시는 특정 책의 이름을 name, 완독유무를 isRead props로 불러들인다. BookList컴포넌트에서 item 컴포넌트에 정보를 담아 출력시킨다. isRead 완독 유무가 true라면 name props의 값과 ✔를 출력한다.
false라면 name props의 값만 출력한다.

#### 삼항연산자

    return (
      <li className="item">
        {isRead ? name + ' ✔' : name}
      </li>
    );
	
삼항연산자를 이용하는 방법으로 위의 if문을 이용한 방식과 완전히 동일하다.

#### 논리연산자

    return (
      <li className="item">
        {name} {isRead && '✔'}
      </li>
    );

&&연산자를 이용한 방법으로 false라면 아무것도 출력하지 않는 상황일 때 주로 사용한다.

#### 변수

    function Item({ name, isRead }) {
      let itemContent = name;
      if (isRead) {
        itemContent = name + " ✔";
      }
      return (
        <li className="item">
          {itemContent}
        </li>
      );
    }

name의 값을 가진 변수 itemContent를 만들고 조건이 true라면 qustn itemContent를 name = " ✔" 로 변환한다.
코드의 길이는 가장 길지만 유연하게 작동시킬수 있다.
