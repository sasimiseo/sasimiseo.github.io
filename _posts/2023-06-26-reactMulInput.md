---
layout: single
title: "React 다중 input 상태 관리"
---
<iframe src="https://codesandbox.io/embed/reactmultiinputs-jdvchf?fontsize=14&hidenavigation=1&theme=light"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="reactMultiInputs"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>

복수의 input을 관리할 때에는 useState와 onChange를 여러번 사용하는 방법보다는 input에 name 속성을 할당하여 이벤트를 발동할 때 이 값을 참조하는 편이 낫다.
 이 방법을 사용할 때에는 문자열 형태의 상태가 아닌 객체형태의 상태를 사용해야한다.
 
 	import React, { useState } from "react";
    
    function InputSample() {		// 객체의 초기값 설정
      const [inputs, setInputs] = useState({
        name: "",
        nickname: ""
      });
    
      const { name, nickname } = inputs;		// 객체에서 name과 nickname을 추출한다.
    
      const onChange = (e) => {
        const { value, name } = e.target;
        setInputs({
          ...inputs,			// spread문법을 사용하여 새로운 객체로 복사 후 수정한다.
          [name]: value			//input의 name에 할당된 값을 프로퍼티 이름으로 설정한다.
        });
      };
    
      const onReset = () => {
        setInputs({
          name: "",
          nickname: ""
        });
      };
    
      return (
        <div>
          <input name="name" value={name} onChange={onChange} placeholder="이름" />
          <input
            name="nickname"
            value={nickname}
            onChange={onChange}
            placeholder="닉네임"
          />
          <button onClick={onReset}>초기화</button>
          <div>
            <b>값: </b>
            {name} ({nickname})
          </div>
        </div>
      );
    }
    
    export default InputSample;
    
리액트에서는 객체를 직접 수정하면 안되기 때문에 새로운 객체를 만들어 그 객체를 수정해야한다. 이 과정에서 대괄호 표기법을 사용한 이유는 프로퍼티 name에 value를 할당하는 것이 아닌 input의 name 값을 프로퍼티 이름으로 설정해야 하기 때문이다.
