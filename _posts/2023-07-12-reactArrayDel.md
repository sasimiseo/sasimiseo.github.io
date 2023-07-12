  ---
  layout: single
  title: "React 배열에 항목 제거"
  ---

  <iframe src="https://codesandbox.io/embed/reactarraydel-w7rcdd?fontsize=14&hidenavigation=1&theme=light"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="reactArrayDel"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>

이전의 리엑트에 배열을 추가하는 예문에 각각의 배열에 해당 항목을 제거하는 기능을 가진 버튼을 추가해봅시다.

#### reactArrayAdd.js

    import "./styles.css";
    import React, { useRef, useState } from "react";
    
    function BookInfo({ book }) {
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
    
      const [inputs, setInputs] = useState([
        {
          name: "",
          date: ""
        }
      ]);
    
      const { name, date } = inputs;
    
      const onChange = (e) => {
        const { name, value } = e.target;
        setInputs({
          ...inputs,
          [name]: value
        });
      };
    
      const nextId = useRef(4);
      const onCreate = () => {
        const book = {
          id: nextId.current,
          name,
          date
        };
        setBooks(books.concat(book));
    
        setInputs({
          name: "",
          date: ""
        });
        nextId.current += 1;
      };
    
      return (
        <div>
          <input name="name" value={name} onChange={onChange} />
          <input name="date" value={date} onChange={onChange} />
          <button onClick={onCreate}>확인</button>
          {books.map((book) => (
            <BookInfo book={book} key={book.id} />
          ))}
        </div>
      );
    }
    
	
우선  항목을 제거하는 함수를 작성하여 봅시다.

        export default function App() {
   	 ......
 	   const onRemove = (id) => {
 	          setBooks(books.filter((book) => book.id !== id));
         };

해당 코드는 filter() 배열 내장 함수를 이용하여 book.id 의 id를 가진 배열을 삭제하는 기능을 합니다.
이제 배열의 항목 옆에 버튼을 생성하고 이 기능을 담아보겠습니다.
컴포넌트 Bookinfo에서 onRemove 함수를 가져와야 하기때문에 자식 컴포넌트를 렌더링 시킬때 파라피터를 이용하여 외부함수를 이용할 수 있게 수정합니다.

    return (
        <div>
          <input name="name" value={name} onChange={onChange} />
          <input name="date" value={date} onChange={onChange} />
          <button onClick={onCreate}>확인</button>
          {books.map((book) => (
            <BookInfo book={book} key={book.id} onRemove={onRemove} />
          ))}
        </div>
      );

Bookinfo 컴포넌트에서도 마찬가지로 파라미터를 받아올 수 있도록 수정합시다.

    function BookInfo({ book, onRemove }) {
      return (
        <div>
          <b>{book.name}</b> <span>({book.date})</span>
          <button onClick={() => onRemove(book.id)}>삭제</button>
        </div>
      );
    }
	
여기서 onClick={onRemove(book.id)}로 할당하지 않은 이유는 해당 컴포넌트가 시작과 동시에 렌더링을 하기 때문에 아무것도 출력되지 않기 때문입니다. 이런 문제 때문에 onClick에 콜백 함수를 넣어주고, 해당 함수가 실행 될 때 book.id를 입력받아 실행하는 방법으로 처리한 것입니다.
