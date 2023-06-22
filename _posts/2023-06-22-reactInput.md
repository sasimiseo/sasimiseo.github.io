---
layout: single
title: "React Input 상태 관리"
---

input 값을 밑에 출력하고 초기화 버튼을 누르면 input 값이 지워지는 예제를 구현해보겠습니다.

    import "./styles.css";
    import React, { useState } from 'react';
    
    export default function App() {
      const [text, setText] = useState("");
      
      const change = (e) => {
        setText(e.target.value);
      }
    
      const reset = (e) => {
        setText("");
      }
    
      return (
        <div className="App">
          <div>
            <input onChange={change} value={text}/>
            <button onClick={reset}>초기화</button>
          </div>
          <div>
            {text}
          </div>
        </div>
      );
    }
    
값을 입력받는 input 과 input의 값을 지우는 초기화 버튼, input의 값이 출력하는 열이 존재합니다.  input 값을 상태 text로 설정하고 값이 바뀔때마다 함수 change()를 실행합니다.
함수 change()는 input의 value와 아래열에 할당된 상태 text를 e.target으로 재선언하는데
e.target은 이벤트가 발생한 DOM 인 input DOM을 가리킴으로 input에 입력한 값으로 재선언됩니다.
