---
layout: single
title: "React useMemo를 이용한 컴포넌트 최적화"
---

useMemo 는 컴포넌트의 성능을 최적화하는데에 사용하는 훅이다. 이미 연산된 값을 재사용함으로써 동일한 계산의 반복 수행을 제거한다.

#### useMemo 문법
    const value = useMemo(() => {
        return calculate();
    },[item])
	
첫번째 파라미터에 어떻게 연산할지 정의할 콜백함수를 입력하고 두번째 파라미터에는 deps 배열을 입력한다.  배열안에 있는 값이 업데이트 될때에만 콜백함수를 호출한다.
