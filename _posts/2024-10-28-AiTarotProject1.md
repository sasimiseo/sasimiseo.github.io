---
layout: single
title: "AI 타로 카드 사이트 프로젝트 1"
---

AI를 이용한 타로 카드 사이트를 기획하였다. 
일단은 웹 사이트에서 어떤 타로 리딩을 받을지 질문을 받은 후 카드 3장을 고르고 응답한 질문과 선택한 카드의 값을 백엔드로 넘겨 ChatGPT Api에서 응답을 받은 후 다시 웹에 출력하는 간단한 방식으로 구현할 예정이다.
suffle deck 버튼을 누르면 타로카드의 배열을 무작위로 정렬한 후 shuffledDeck state에 삽입하고 뒤집어진 상태의 카드들이 나열되게 된다.
이때 카드의 속성에 preserve-3d를 부여하여 앞뒷면이 존재하고 뒤집을 수 있도록 구현하였다.

<iframe src="https://codesandbox.io/p/github/sasimiseo/TarotReading/draft/goofy-lake?workspaceId=0b88a3d6-2894-4731-b2e7-b80640a77051&embed=1&file=%2Fsrc%2Fcomponents%2FTarotCards.js"
     style="width:100%; height: 500px; border:0; border-radius: 4px; overflow:hidden;"
     title="sasimiseo/TarotReading/draft/goofy-lake"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>
   
