# 📝 `box-sizing`  정리

## 🎯 Box Model

- 요소 그 자체이다. 크기는  `콘텐츠 크기` + `padding` 값 + `border` 값 + `margin` 값이다.  
    
<img width="338" height="221" alt="image" src="https://github.com/user-attachments/assets/310c399b-49dd-4b33-97b9-9df39f956605" />  

    

## 🎯 크기 조절할 때 문제점

<table>
  <tr>
    <td valign="top" width="50%">
      <pre><code class="language-css">.container {
  width: 1000px;
  height: 500px;
  border: 1px solid black;
}
.green_box {
  width: 1000px;
  height: 250px;
  border: 10px solid green;
  padding: 10px;
  box-sizing: border-box; /* 추가 */
}
.red_box {
  width: 1000px;
  height: 250px;
  border: 10px solid red;
  padding: 10px;
}
</code></pre>
    </td>
    <td valign="top" width="50%">
      <strong>결과 이미지</strong><br/>
      <img
        src="https://github.com/user-attachments/assets/b4353ea8-e8f9-4bda-b7ef-38d8cda9f3cf"
        alt="border-box vs content-box 결과"
        width="100%">
    </td>
  </tr>
</table>

- `.container`의 `width`는 1000px 이다. 그런데 그 내부 `.red_box`의 `width` 또한 1000px 인데 옆으로 튀어나온 모습을 볼 수 있다. 그 외에 `height` 또한 튀어나왔다.
- 그에 반해 `.green_box`는 `width`, `height`, `padding`, `border` 모두 `.red_box`와 동일하지만 `.container` 크기에 딱 맞다.
    
    → **⭐️ 핵심은  `box-sizing: border-box;` 속성이다.**

  
    

## 🎯 원인

- 우리가 평소에 지정하는 `<div style={ { width: ‘1000px’ } } />` 에서 `width`은 콘텐츠 크기를 의미한다.
    <img width="172" height="49" alt="image" src="https://github.com/user-attachments/assets/05d7d0e3-c0c1-4fae-8f1e-7ca9c55f6b82" />  

    
    - Box Model 에서 가장 안쪽에 있는 것이 `content`이다.
- 근데 여기서 `padding` 과 `border`의 크기를 각각 10px 씩 늘리면 `width: ‘1000px’` 에 추가되기 때문에 전체 Box Model의 `width`가 1040px이 된다.  
    
<img width="335" height="294" alt="image" src="https://github.com/user-attachments/assets/531cfa30-ad40-46a4-9f06-5fdfba766e0c" />  

    
    →** ⭐️그래서 예시처럼 부모 박스에서 튀어나오는 것 **
    

## 🎯 해결 방법 : **`border-box`**

- `box-sizing` 에는 두 가지 속성이 있다.
    1. **`content-box`**
        - 설정한 `width`와 `height` 값이 곧 요소 내부의 `content` 크기를 의미한다. 이게 디폴트 값이다.
    2. **`border-box`**
        - 설정한 `width`와 `height` 값이 안쪽 여백과 테두리까지 포함한 크기를 의미한다.  
        
        <img width="304" height="184" alt="image" src="https://github.com/user-attachments/assets/61bb01b0-3ad6-4c68-b641-c5716b91bc15" />  

        
        `<div style={ { width: ‘1000px’ } } />` 에서 정한 `width` 1000px은 `padding`과 `border`를 포함한 크기이다.
        
        이제 `padding` 과 `border`의 크기를 각각 10px 씩 늘려도 `content`크기가 줄어들며 `border-box` 크기가 고정된다.  
        
        <img width="288" height="193" alt="image" src="https://github.com/user-attachments/assets/9523ca90-867d-45e0-a5a8-856680f23ffe" />  

        

## 🎯 요약

- `boxSizing: 'border-box'` 는 정밀한 레이아웃 조정을 위해서 자주 사용하는 속성이다.
- `margin`은 포함하지 않으니 주의.


---
## 📕 참고 자료  
#1) https://codingbroker.tistory.com/116

#2) https://developer.mozilla.org/ko/docs/Web/CSS/box-sizing

#3) https://velog.io/@nalsae/%EB%82%B4%EB%B3%B4%EC%A0%95CSS-%EB%AA%A8%EB%A5%B4%EB%A9%B4-%EA%B3%A4%EB%9E%80%ED%95%9C-box-sizing
