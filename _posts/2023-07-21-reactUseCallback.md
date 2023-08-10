---
layout: single
title: "React UseCallback 이용한 함수 재사용"
---

useCallback은 React 라이브러리에서 제공하는 Hook 중 하나로, 함수 컴포넌트 내에서 함수를 최적화하고 성능을 개선하는 데 사용됩니다.
주로 이벤트 핸들러 함수나 다른 컴포넌트에 전달되는 콜백 함수를 최적화하는 데 활용됩니다.
React 컴포넌트가 리렌더링될 때마다 함수는 새로 생성되는 불필요한 메모리 사용과 연산을 초래할 수 있습니다.
useCallback을 사용하면 함수가 변하지 않도록 보장하면서도 컴포넌트의 리렌더링 시에 함수를 재생성하지 않습니다.

#### 사용법
useMemo와 마찬가지로 첫번째 파라미터에는 콜백 함수를 두번째 파라미터에는 의존 배열을 할당합니다.
의존성 배열은 어떤 상태나 프롭스의 변화를 감지하여 콜백 함수를 재생성할지 결정합니다.
이 배열이 비어있다면, 콜백 함수는 컴포넌트의 라이프사이클과 무관하게 최초 렌더링 시 한 번만 생성됩니다.

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
   
useCallback을 사용하지 않았을 시 각각의 컴포넌트를 조작시 다른 모든 함수가 호출되는 것을 콘솔을 이용해 확인할 수 있습니다.
반면에 useCallback을 각각의 함수에 할당한 결과는 컴포넌트를 조작시 해당 컴포넌트가 호출하는 함수만이 실행되는것을 확인할 수 있습니다.

#### useMemo와의 차이점

useCallback과 useMemo는 둘 다 리액트에서 최적화를 위해 사용되는 훅이며, 메모이제이션(memoization)이라는 개념을 기반으로 합니다. 그러나 두 훅은 다른 상황에서 사용됩니다.

useMemo는 주로 계산 비용이 높은 값을 계산하고 해당 값을 재사용할 때 사용됩니다. 예를 들어, 복잡한 계산을 하는 경우 해당 계산 결과를 캐시하여 같은 계산을 반복하지 않고 성능을 향상시킬 수 있습니다.

    const expensiveValue = useMemo(() => {
      // 복잡한 계산 수행
      return someExpensiveCalculation();
    }, [dependencies]);
    
useCallback은 주로 함수를 메모이제이션하여 불필요한 함수 재생성을 방지하고 컴포넌트의 렌더링 성능을 개선하는 데 사용됩니다. 이벤트 핸들러나 다른 컴포넌트에 전달되는 콜백 함수를 최적화할 때 유용합니다.

    const optimizedCallback = useCallback(() => {
      // 함수 본문
    }, [dependencies]);
    
요약하자면, useMemo는 값 자체를 메모이제이션하여 계산 비용을 줄이고 useCallback은 함수를 메모이제이션하여 불필요한 함수 재생성을 막습니다. 두 훅 모두 성능 최적화를 위한 도구로 사용되며, 상황에 따라 적절한 훅을 선택하여 사용하는 것이 중요합니다.

#### 주의점
useCallback을 사용하는 것은 항상 모든 함수에 성능 향상을 보장하지 않습니다.
아래에 나열한 경우일 시 useCallback의 사용은 지양하는 것이 좋습니다.

1. 불필요한 최적화인 경우: 모든 함수를 useCallback으로 감싸는 것은 불필요한 최적화로 이어질 수 있습니다. 리렌더링에 의해 함수가 재생성되는 것 자체가 항상 나쁜 것은 아니며, 오히려 작은 규모의 컴포넌트에서는 최적화가 불필요할 수 있습니다.

2. 함수 호출 빈도가 낮은 경우: 함수가 자주 호출되지 않는 경우, 불필요하게 함수를 메모이제이션하는 것은 오히려 더 복잡한 코드를 유발할 수 있습니다. 함수 자체의 생성 비용이 크지 않거나 호출 빈도가 낮은 경우, useCallback을 사용하지 않고 간단하게 함수를 정의하는 것이 더 명확할 수 있습니다.

3. 의존성 배열 관리가 복잡한 경우: 함수가 여러 개의 상태나 프롭스에 의존하고 있는 경우, useCallback의 의존성 배열을 정확하게 관리하기가 어려울 수 있습니다. 잘못된 의존성 배열 설정으로 인해 예상치 못한 버그가 발생할 수 있습니다. 이러한 경우에는 오히려 함수 재생성을 감수하고 의존성을 따로 추적하는 방식을 고려할 수 있습니다.

4. 메모리 누수가 발생할 가능성이 있는 경우: useCallback을 사용할 때 의존성 배열을 잘못 설정하면, 메모리 누수가 발생할 수 있습니다. 의존성 배열에 있는 값들이 자주 업데이트되면, 함수가 새로 생성되어 메모리가 누수될 수 있습니다. 이러한 경우에는 useCallback 대신에 함수를 일반적으로 정의하는 방식을 사용하거나, 메모리 누수를 방지하기 위한 추가적인 조치를 취해야 할 수 있습니다.
