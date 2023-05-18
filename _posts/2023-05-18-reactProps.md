---
layout: single
title: "React Props를 컴포넌트에 전달"
---

### 컴포넌트에게 props 전달

#### App.js
부모 컴포넌트

    import "./styles.css";
    import Grade from "./Grade";
    
    export default function App() {
      return (
        <>
          <Grade name="젊은 예술가의 초상" score="3" />
          <Grade name="모래의 여자" score="5" />
        </>
      );
    }
	
props는 부모 컴포넌트가 자식 컴포넌트에게 정보를 전달할 때 사용한다.
자식 컴포넌트 Grade에게 name과 score의 값을 넘겨준다.

#### Grade.js
자식 컴포넌트

    export default function Grade(props) {
      let stars = "";
      for (let i = 0; i < props.score; i++) {
        stars += "★";
      }
      for (let i = 0; i < 5 - props.score; i++) {
        stars += "☆";
      }
    
      return (
        <h3>
          {props.name} : {stars}
        </h3>
      );
    }
	
props를 이용하여 부모 컴포넌트에게서 값을 불러올 수 있다. props는 객체 형태로 전달되고
props.name과 props.score로 값을 조회할 수 있다.

<iframe src="https://codesandbox.io/embed/reactprops-forked-kw73sy?fontsize=14&hidenavigation=1&theme=light"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="reactProps (forked)"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>
   
#### props 비구조화 할당
위의 예시에서는 props.name 과 같이 조회를 할때마다 props. 를 입력했다. 비구조화 할당 문법을 사용하면 좀 더 간결하게 표현할 수 있다.

    export default function Grade({name, score}) {
          let stars = "";
          for (let i = 0; i < score; i++) {
            stars += "★";
          }
          for (let i = 0; i < 5 - score; i++) {
            stars += "☆";
          }
        
          return (
            <h3>
              {name} : {stars}
            </h3>
          );
        }
		
#### 복수의 컴포넌트 spread 문법으로 전달

    function Profile({ person, size, isSepia, thickBorder }) {
      return (
        <div className="card">
          <Avatar
            person={person}
            size={size}
            isSepia={isSepia}
            thickBorder={thickBorder}
          />
        </div>
      );
    }
	
위와 같이 반복되는 모든 props를 전달할 때 spread 문법을 이용하면 간결하게 표현할 수 있다.

    function Profile(props) {
      return (
        <div className="card">
          <Avatar {...props} />
        </div>
      );
    }

spread 문법을 모든 컴포넌트에서 사용하는 것은 지양해야한다. 가능한 비구조화 할당 방법을 이용하여 자식 컴포넌트의 JSX에 전달하는 것이 좋다.

#### props의 기본값 설정

    function Avatar({ person, size = 100 }) {
      // ...
    }
	
컴포넌트의 JSX안에 props를 설정하지 않고 기본적으로 사용할 값을 설정해야 한다면 파라미터의 뒤에 바로 = 을 붙여서 표현할 수 있다.

     function Avatar({ person, size}) {
          return(
    			Avatar.defaultprops = {
    				size = 100
    			}
    		);
        }
위와 같은 방식으로도 default값을 설정할 수 있다.
#### JSX를 자식에게 전달

    <Card>
    	<Profile />
    </Card>
	
컴포넌트를 JSX에서 브라우저 태그처럼 중첩시킬때 Card 컴포넌트는 자식 props로 설정된 Profile에게 값을 받아온 후 wrapper div에 랜더링시킨다.

    import Profile from "./Profile.js";
    import "./styles.css";
    
    function Card({ children }) {
      return <div className="card">{children}</div>;
    }
    
    export default function Gallery() {
      return (
        <Card>
          <Profile />
        </Card>
      );
    }
    
Card에 props.children을 렌더링 시켜주면 아래와 같이 컴포넌트 Card의 className="card"의 div에 둘러쌓인 Profile을 렌더링 한다.
    
<iframe src="https://codesandbox.io/embed/reactpropschildren-ttrpeq?fontsize=14&hidenavigation=1&theme=light"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="reactPropsChildren"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>
   
