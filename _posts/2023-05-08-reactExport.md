---
layout: single
title: "React 컴포넌트 출력"
---

### export default 출력 방식

자바스크립트에서 jsx를 이용하여 표현한 컴포넌트는 페이지에 자동으로 출력되지 않기때문에 아래의 방법을 사용하려 출력해주어야 한다.

     <script>
        	function App() {
        	return(
        		<div>
           	     <h1>Hello, react!</h1>
                </div>
        		);
       	 }
  	      export default App;
        </script>
		
가장 흔히 사용하는 방식으로 default export로는 오직 하나의 컴포넌트만을 출력할 수 있기 때문에 하나의 컴포넌트를 출력하는 경우 주로 이 방식을 사용한다.

         <script>
            	export default function App() {
            	return(
            		<div>
               	     <h1>Hello, react!</h1>
                    </div>
            		);
           	 }
            </script>
    		
조금 더 간략하게 출력하고 싶다면 컴포넌트에 바로 export default를 이어붙여 표현할 수 있다.

### 다중 컴포넌트 출력

##### named exports

    function Component1(props){
        return(
            <div>함수형 컴포넌트1</div>
        );
    }
    
    const Component2 =(props) =>{
        return(
            <div>함수형 컴포넌트2</div>
        );
    }
    
    
    // export default Component1;
    // export default Component2;
    export  {Component1 , Component2}
	
복수의 컴포넌트를 출력할 경우 주로 named exports 방식을 사용한다. default export 방식과 달리 여러개의 컴포넌트를 출력할 수 있다.

##### export default 다중 출력
    import logo from './logo.svg';
    import './App.css';
    import {Component1,Component2} from './ComponentEx';
    
    import React from 'react';
    
    class App extends React.Component{
      render(){
        return(
          <div className="App">
            <Component1></Component1>
            <Component2></Component2>
          </div>
        );
      }
    }
    export default App;
	
export default 방식으로 복수의 컴포넌트를 출력하는 방식으로 하나의 컴포넌트에 출력하길 원하는 2개의 컴포넌트를 묶어서 출력하는 방식이다.

### 이전에 사용하던 출력 방식

    <body>
    	<div id="root">
   	 </div>
    
    </body>
    
    <script>
    	function App() {
    	return(
    		<div>
           	 <h1>Hello, react!</h1>
            </div>
    		);
  	  }
  	  ReactDOM.render(App, document.getElementById("root"));
    </script>
	

HTML에 root라는 id를 가진 div를 만들어 준 후 컴포넌트를 div에 렌더링 시켜주는 방식이다.
요즘은 별로 사용하지 않는다.
