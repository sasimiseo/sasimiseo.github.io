---
layout: single
title: "React useEffect"
---

useRef() 는 렌더링될 때마다 특정 작업을 실행시키는 훅이다.

##### 컴포넌트 Mount 시

    useEffect(() => {
        console.log("렌더링 될때마다 실행");
      });
	  
deps 부분을 생략했을시 컴포넌트가 렌더링 될 때 마다 특정 작업을 실행한다.

    useEffect(() => {
        console.log("처음 렌더링 될때마다 실행");
      },[]);
	  
deps 부분을 공백으로 작성하였을 시 컴포넌트가 맨 처음 렌더링 될 때만 실행한다.

#### 컴포넌트 Unmount 시

    useEffect(() => {
        console.log("컴포넌트 나타남");
        console.log(name);
        return () => {
          console.log("컴포넌트 사라짐");
        };
      });
	  
렌더링 된 컴포넌트가 사라졌을때 실행한다. 

#### 컴포넌트 Update 시

    useEffect(() => {
        console.log(name);
        console.log("name이라는 값이 업데이트 될 때만 실행");
      },[name]);
	  
특정값이 업데이트 될 때마다 실행한다.
