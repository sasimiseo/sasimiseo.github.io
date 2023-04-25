---
layout: single
title: "이벤트 위임"
---

## 이벤트 위임
복수의 요소에 각각 핸들러를 할당하지 않고 상위 요소의 핸들러 하나로 이벤트를 잡아내는 패턴이다.
메모리 소모량을 감소시킬수 있고 칸이 얼마나 많은지에 상관없이 작동시킬수 있다.

     <script>
          const ul = document.querySelector("ul");
          ul.addEventListener("click", (event) => {
            if (event.target.tagName == "LI") {
              event.target.classList.add("selected");
            }
          });
        </script>
		
각각의 ul에 리스너로 할당하지 않고 ul 하나에 이벤트 리스너를 할당해 target으로 위치를 알아내 이벤트를 발동시킨다.

    <div id="menu">
      <button data-action="save">저장하기</button>
      <button data-action="load">불러오기</button>
      <button data-action="search">검색하기</button>
    </div>
    
    <script>
      class Menu {
        constructor(elem) {
          this._elem = elem;
          elem.onclick = this.onClick.bind(this); // (*)
        }
    
        save() {
          alert('저장하기');
        }
    
        load() {
          alert('불러오기');
        }
    
        search() {
          alert('검색하기');
        }
    
        onClick(event) {
          let action = event.target.dataset.action;
          if (action) {
            this[action]();
          }
        };
      }
    
      new Menu(menu);
    </script>
	
data-action에 할당된 이름의 함수를 실행시킨다. 버튼의 클릭할 시 각각의 버튼에 할당된 이벤트를 실행한다.

    <button data-toggle-id="subscribe-mail">
      구독 폼 보여주기
    </button>
    
    <form id="subscribe-mail" hidden>
      메일 주소: <input type="email">
    </form>
    
    <script>
      document.addEventListener('click', function(event) {
        let id = event.target.dataset.toggleId;
        if (!id) return;
    
        let elem = document.getElementById(id);
    
        elem.hidden = !elem.hidden;
      });
    </script>
	
토글러 기능을 구현한 예시이다. 버튼을 클릭 시 버튼의 hidden 프로퍼티를 반전시킨다.
