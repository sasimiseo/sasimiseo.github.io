---
layout: single
title: "React UseMemo를 이용한 함수 재사용"
---

useCallback은 특정 함수를 새로 만들지 않으면서 재사용 하기위해 사용됩니다.
useMemo와 유사한 기능을 가지고 있는데 useMemo는 재사용되는 특정 결과값에 사용하는 반면, useCallback은 재사용되는 함수에 사용합니다.
리액트는 컴포넌트가 렌더링 될 때 마다 함수를 실행시키기 때문에 불필요한 함수의 재사용을 방지하여 컴포넌트를 최적화 하기위해 사용한다.

#### 사용법
useMemo와 마찬가지로 첫번째 파라미터에는 입력할 함수를 두번째 파라미터에는 deps 배열을 할당합니다.

    const onToggle = useCallback(
        (id) => {
          setBooks(
            books.map((book) =>
              book.id === id ? { ...book, active: !book.active } : book
            )
          );
        },
        [books]
      );
	  

#### 예제 

<iframe src="https://codesandbox.io/embed/react-use-callback-37drk?fontsize=14&hidenavigation=1&theme=dark"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="react-use-callback"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>
   
useCallback을 사용하지 않았을 시 각각의 컴포넌트를 조작시 다른 모든 함수가 호출되는 것을 콘솔을 이용해 확인할 수 있다. useCallback을 각각의 함수에 할당한 결과는 컴포넌트를 조작시 해당 컴포넌트가 호출하는 함수만이 실행되는것을 확인할 수 있다.
   
