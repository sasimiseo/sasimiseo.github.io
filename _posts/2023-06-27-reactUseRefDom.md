---
layout: single
title: "React useRef를 사용한 DOM 조작"
---
useRef는 렌더링에 필요하지 않은 값을 참조하거나 DOM을 조작할 때 사용하는 리액트 hook 입니다. 


    import React, { useState, useRef } from 'react';
    
    export default function App() {
      const  inputRef = useRef(null)		// ref객체 와 초기값 선언
      const onFocus = () => inputRef.current.focus()		// DOM 엑세스 후 메서드 호출
      return(
    
        <div>
          <input ref={inputRef}/>		// 조작할 위치에 ref객체 할당
          <button onClick={onFocus}>focus</button>
        </div>
      );
    }`
	
useRef를 사용하는 방법은 먼저 ref객체를 선언한다. 
조작할 DOM 노드의 JSX에 속성에 ref객체를 할당해 준다.
ref객체의 .current 값은 조작할 DOM을 가르키게 된다.

##### ref의 특징, 주의점
- 재렌더링 사이에 정보를 저장할 수 있다.
- 이를 변경해도 상태와는 다르게 다시 렌더링 하지 않는다.
- 정보는 local 변수처럼 외부와 공유되지 않는다.
- 초기화를 제외하고 렌더링중에는 읽거나 쓰면안된다.
