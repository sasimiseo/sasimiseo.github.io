---
layout: single
title: "Map의 사용방법과 객체와의 차이점"
---

Map객체는 ES6 부터 추가된 객체로 기존의 객체와 같이 데이터를 저장하고 검색하는데 사용하는 자료구조 입니다. 하지만 서로 큰 차이점이 존재하기 때문에 두 객체의 장단점과 사용상황을 구별하기 위해 포스팅합니다. 일단 차이점을 서술하기 이전에 Map객체의 생성자와 주요 메서드와 속성에 대해 알아보도록 합시다.

####목차
- [메서드와 속성](#생성자)
- [차이점](#map과-객체의-차이점)
- [사용 상황](#map을-사용하는-상황)

####생성자
**new Map()**: 빈 Map객체를 생성합니다. 초기값을 가진 Map객체를 생성하고 싶다면 매개변수에 객체를 입력하면 됩니다.

    // 빈 객체 생성
    let myMap = new Map();
    
    // 초기값을 가진 객체 생성
    let myMap = new Map([
              ['name', 'John'],
              ['age', 30]
            ]);

기존 객체를 이용하여 Map객체를 생성하고 싶다면 Object.entries()를 사용하여 객체의 속성을 키-값 쌍 배열로 변환하고, 이를 Map 객체로 변환하면됩니다.

    // 기존 객체를 이용한 Map 객체
    let myObject = { name: 'John', age: 30 };
    let myMap = new Map(Object.entries(myObject));


###주요 메서드
**set(key, value)**: Map에 키-값 쌍을 추가하거나 업데이트합니다. 만약 이미 동일한 키가 존재한다면 값을 업데이트하고, 그렇지 않으면 새로운 키-값 쌍을 추가합니다.

    let myMap = new Map();
    myMap.set('name', 'John');
    myMap.set('age', 30);

**get(key**): 주어진 키에 해당하는 값을 반환합니다.

    let myMap = new Map();
    myMap.set('name', 'John');
    console.log(myMap.get('name')); // 'John'
	
**has(key)**: 주어진 키가 Map에 존재하는지 여부를 확인합니다.

    let myMap = new Map();
    myMap.set('name', 'John');
    console.log(myMap.has('name')); // true
	
**delete(key)**: 주어진 키에 해당하는 키-값 쌍을 제거합니다.

    let myMap = new Map();
    myMap.set('name', 'John');
    myMap.delete('name');
	
**clear()**: Map의 모든 키-값 쌍을 제거하여 비웁니다.

    let myMap = new Map();
    myMap.set('name', 'John');
    myMap.clear();
	
**keys()**: Map의 키를 나타내는 이터레이터 객체를 반환합니다.

    let myMap = new Map();
    myMap.set('name', 'John');
    let keysIterator = myMap.keys();
	

**values()**: Map의 값들을 나타내는 이터레이터 객체를 반환합니다.

    let myMap = new Map();
    myMap.set('name', 'John');
    let valuesIterator = myMap.values();
	
**entries()**: Map의 키-값 쌍을 나타내는 이터레이터 객체를 반환합니다.

    let myMap = new Map();
    myMap.set('name', 'John');
    let entriesIterator = myMap.entries();

**forEach(callbackFn[, thisArg])**: Map의 각 요소에 대해 콜백 함수를 호출합니다. thisArg를 통해 콜백 함수 내부에서 사용할 this를 지정할 수 있습니다.

    let myMap = new Map();
    myMap.set('name', 'John');
    myMap.forEach((value, key) => {
      console.log(key, value);
    });
	
####속성
**size**: Map 객체에 저장된 키-값 쌍의 개수를 나타냅니다.

    let myMap = new Map();
    myMap.set('name', 'John');
    myMap.forEach((value, key) => {
      console.log(key, value);
    });
	
###Map과 객체의 차이점
#### 키의 자료형:

**객체(Object)**: 객체의 키는 문자열 또는 심볼만 가능합니다. 객체에서 문자열 이외의 자료형을 키로 사용하면 자동으로 문자열로 변환됩니다. 예를 들어, 객체에 숫자를 키로 사용하면 해당 숫자가 문자열로 변환되어 저장됩니다.

    let myObject = { 1: "one" };
    console.log(myObject["1"]); // "one"
	
**Map**: Map은 모든 자료형을 키로 사용할 수 있습니다. 따라서 숫자, 객체, 함수, 심볼 등을 직접 키로 사용할 수 있습니다.

    let myMap = new Map();
    let keyObj = {};
    let keyFunc = function() {};
    
    myMap.set(keyObj, "Value for keyObj");
    myMap.set(keyFunc, "Value for keyFunc");
    
    console.log(myMap.get(keyObj)); // "Value for keyObj"
    console.log(myMap.get(keyFunc)); // "Value for keyFunc"
	
#### 키 순서 및 반복:

**객체(Object)**: 객체의 속성 순서는 보장되지 않으며, 객체를 순회할 때 키의 순서가 일관되지 않습니다.

    let myObject = { b: 2, a: 1 };
    for (let key in myObject) {
      console.log(key); // 순서 보장되지 않음
    }
	
**Map**: Map은 요소들의 삽입 순서를 보장하며, 키의 순서가 일관되게 유지됩니다. 따라서 Map을 순회할 때 키의 순서가 예측 가능합니다.

    let myMap = new Map();
    myMap.set('b', 2);
    myMap.set('a', 1);
    
    for (let [key, value] of myMap) {
      console.log(key); // 순서 보장됨
    }
	
#### 크기 속성:

**객체(Object)**: 객체의 크기를 직접 확인하기 위한 내장 메서드나 속성이 없습니다. 크기를 알기 위해서는 객체를 순회하면서 요소를 카운트해야 합니다.

    function countProperties(obj) {
      let count = 0;
      for (let prop in obj) {
        if (obj.hasOwnProperty(prop)) {
          count++;
        }
      }
      return count;
    }
    
    let myObject = { a: 1, b: 2 };
    console.log(countProperties(myObject)); // 2
	
**Map**: Map은 size 속성을 통해 맵의 크기를 직접 확인할 수 있습니다.

    let myMap = new Map();
    myMap.set('a', 1);
    myMap.set('b', 2);
    
    console.log(myMap.size); // 2
	
### Map을 사용하는 상황

**키의 자료형 다양성**: 다양한 자료형을 키로 사용해야 하는 경우에 Map이 더 적합합니다. 일반 객체는 키로 문자열 또는 심볼만 사용할 수 있지만, Map은 모든 자료형을 키로 사용할 수 있습니다.

**키 순서 중요성**: 데이터의 순서가 중요하고 그 순서를 보장해야 하는 경우 Map을 사용하는 것이 좋습니다. Map은 요소의 삽입 순서를 보장하므로 순서가 중요한 경우에 유용합니다.
