---
layout: single
title: "React 배열 추가"
---

리액트에서 배열에 항목을 추가하는 방법에 대해 설명하겠습니다.
아래처럼 두개의 input에 각각 값을 입력받고 버튼을 클릭하여 추가하는 예제를 작성해보겠습니다.

<iframe src="https://codesandbox.io/embed/jolly-agnesi-7nwgf2?fontsize=14&hidenavigation=1&theme=light"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="reactArrayAdd"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>
   
먼저 값을 입력받을 input 과 버튼을 작성하고 배열을 렌더링 해봅시다.

    import "./styles.css";
    import React, { useRef, useState } from "react";
    
    function BookInfo({ book }) {		// 반복되는 배열 컴포넌트
      return (
        <div>
          <b>{book.name}</b> <span>({book.date})</span>
        </div>
      );
    }
    
    export default function App() {
      const [books, setBooks] = useState([
        {
          id: 1,
          name: "젊은 예술가의 초상",
          date: "2023-01-24"
        },
        {
          id: 2,
          name: "모래의 여자",
          date: "2023-03-17"
        },
        {
          id: 3,
          name: "만엔 원년의 풋볼",
          date: "2023-05-03"
        }
      ]);
    
      return (
        <div>
          <input/>
          <input/>
          <button>확인</button>
          {books.map((book) => (		// map() 내부함수를 이용하여 배열 전체에 함수 실행
            <BookInfo book={book} key={book.id} />
          ))}
        </div>
      );
    }
    
이후에는 input에서 값을 가져오기 위해 이전에 배웠던 복수의 input을 관리하는 방법을 추가해봅시다.

          const [inputs, setInputs] = useState([
            {
              name: "",
              date: ""
            }
          ]);
        
          const { name, date } = inputs;
        
          const onChange = (e) => {			// input에 입력되는 값을 상태 inputs에 저장
            const { name, value } = e.target;
            setInputs({
              ...inputs,
              [name]: value
            });
    		.......		// input을 관리하기 위해 input에 name과 value 값 할당
    		return (
    		    <div>
    		      <input name="name" value={name} onChange={onChange} />
    		      <input name="date" value={date} onChange={onChange} />
    		      <button>확인</button>
    		      {books.map((book) => (
    		        <BookInfo book={book} key={book.id} />
    		      ))}
    		    </div>
      );
     };

아직까지 input에 입력되는 값이 상태에 저장되기만 할 뿐 기능상의 변화는 없습니다. 마지막으로 배열을 생성하는 버튼이 기능하도록 onCreate 이벤트를 작성하고 할당해줍시다.

        const nextId = useRef(4);		// 렌더링되는 변수가 아님으로 useRef사용
          const onCreate = () => {
            const book = {			// input에서 가져온 값을 가진 배열 book을 생성
              id: nextId.current,		// 기존에 배열의 id가 3까지 존재함으로 4부터 시작
              name,
              date
            };
            setBooks(books.concat(book));		// book 배열을 books 배열에 추가
        
            setInputs({			// input 을 다시 공백으로 되돌림
              name: "",
              date: ""
            });
            nextId.current += 1;
          };
    		
			......
    		return (		// 버튼에 onCreate 할당
    		    <div>
    		      <input name="name" value={name} onChange={onChange} />
    		      <input name="date" value={date} onChange={onChange} />
    		      <button onClick={onCreate}>확인</button>
    		      {books.map((book) => (
    		        <BookInfo book={book} key={book.id} />
    		      ))}
    		    </div>
    		  );
	  
배열에 배열을 추가하기 위해 concat() 내부함수를 사용한다. 이제 확인 버튼을 누르면 input 값에 입력된 값을 가진 배열이 추가되고 동적으로 렌더링 된다.
