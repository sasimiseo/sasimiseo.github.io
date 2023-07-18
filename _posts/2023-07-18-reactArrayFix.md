---
layout: single
title: "React 배열 항목 수정하기"
---

배열의 항목을 수정하는 법에대해 알아보겠습니다.
책 이름명을 클릭할 시 초록색으로 변하고 재클릭시 다시 검정색으로 돌아오도록 코드를 작성해보겠습니다.
색이 변하도록 참고하는 값으로 active 라는 불린값을 가진 속성을 배열에 추가해줍시다.

    const [books, setBooks] = useState([
        {
          id: 1,
          name: "젊은 예술가의 초상",
          date: "2023-01-24",
          active: true
        },
        {
          id: 2,
          name: "모래의 여자",
          date: "2023-03-17",
          active: false
        },
        {
          id: 3,
          name: "만엔 원년의 풋볼",
          date: "2023-05-03",
          active: false
        }
      ]);
	  

그 다음에는 마우스가 책 제목명 위에 올라갈 시 커서가 포인터로 표시되고 active 값에 따라 폰트의 색상을 다르게 표현되도록 스타일을 작성하겠습니다.

    function BookInfo({ book, onRemove, onToggle }) {
      return (
        <div>
          <b
            onClick={() => onToggle(book.id)}
            style={{
              cursor: "pointer",
              color: book.active ? "green" : "black"
            }}
          >
            {book.name}
          </b>{" "}
          <span>({book.date})</span>
          <button onClick={() => onRemove(book.id)}>삭제</button>
        </div>
      );
    }

제목명을 클릭시 그 배열의 active 값이 반전되도록 onToggle 이라는 함수를  작성해보겠습니다. 그 후 onToggle 함수를 BookInfo로 전달시키겠습니다.

    const onToggle = (id) => {
        setBooks(
          books.map((book) =>
            book.id === id ? { ...book, active: !book.active } : book
          )
        );
      };
	  
onToggle 작동 시, 클릭한 배열의 id를 전달받고 그 id와 다르다면 아무런 변화도 하지않고 id가 같다면 active의 불린값을 반전시키는 함수를 모든 함수에 실행시킵니다.

<iframe src="https://codesandbox.io/embed/reactarrayfix-mn9kz8?fontsize=14&hidenavigation=1&theme=light"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="reactArrayFix"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>
