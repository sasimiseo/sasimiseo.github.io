---
layout: single
title: "React 배열 렌더링"
---

    const books = [
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
      ]
	  
다음과 같은 배열을 리액트에서 렌더링하는 방법은 여러가지가 있습니다.
첫번째는 비효율적이지만 하나하나 직접 불러오는 방법입니다.

    return (
        <div>
          <div>
            <b>{books[0].name}</b> <span>({books[0].email})</span>
          </div>
          <div>
            <b>{users[1].username}</b> <span>({users[1].email})</span>
          </div>
          <div>
            <b>{users[2].username}</b> <span>({users[1].email})</span>
          </div>
        </div>
      );
    }
	
그러나 이런경우 코드가 반복되기 때문에 컴포넌트를 재사용하는 방식으로 바꾸어봅시다.

#### BookInfo.js

    function BookInfo({ book }) {
      return (
        <div>
          <b>{book.name}</b> <span>({book.date})</span>
        </div>
      );
    }
	

#### App.js

    return (
        <div>
          <BookInfo book={books[1]}/>
          <BookInfo book={books[2]}/>
          <BookInfo book={books[3]}/>
        </div>
      );
    }

고정된 배열이라면 이런 방식이 유효하지만 동적인 배열을 렌더링 할때는 적합하지 못합니다.
동적인 배열을 렌더링 하기 위해서는 내장 함수 [map()](https://learnjs.vlpt.us/basics/09-array-functions.html#map "map()")을 사용합니다.

    return(
        <div>
          {books.map(book =>
            <BookInfo book={book})}
        </div>
      );
    }
	
배열의 모든 원소가 렌더링 되지만 콘솔에서는 오류를 출력합니다. 리액트에서 배열을 렌더링 할때는 key라는 props를 설정해야합니다. key값은 원소들이 가지고 있는 고유값으로 설정합니다.

    return(
        <div>
          {books.map(book =>
            <BookInfo book={book} key={book.id}/>)}
        </div>
      );
    }
	
<iframe src="https://codesandbox.io/embed/reactarrayrender-tdsc8v?fontsize=14&hidenavigation=1&theme=light"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="reactArrayRender"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>
