## Git

깃은 버전관리 시스템 깃허브, 빅버켓은 깃을 업로드 할 수 있는 플랫폼.

## HTML5

meta tag는 검색엔진에서의 설명부분을 설정할 수 있다.
보이지 않는 정보(meta, title 등등)는 head에, 사용자 눈에 보이는 정보는 body에

Semantic Tag = 의미가 있는 태그 (title, article, section, h1, h2 등등)
Non Semantic Tag = 의미가 없는 태그 (div, span 등등)

span은 텍스트를 위한 컨테이너이다
id는 고유해야 하나 class는 중복 가능

## CSS

```css
h1 {
  color: red;
}
```

선택자만

```css
.styleclass {
  color: red;
}
#styleid {
  color: blue;
}
```

class(.)나 id(#)

```css
h1 .styleclass {
  color: purple;
}
h1 .styleid {
  color: green;
}
```

선택자+클래스 혹은 선택자+id

### css와 html을 연결하기

1. inline

   html 파일 내부에 `<style>` 태그를 이용하여 직접 정의

2. external

   css파일을 분리.
   `<link href="style.css" rel="stylesheet" />`
   을 `<head>`태그 안에 추가

## Box

많은 엘리먼트들은 4개의 박스를 가지고 있다.
Content < Padding < Border < Margin

### padding, margin

```css
padding-left: 30px;
margin-left: 30px;
```

이와 같이 left,right,top,bottom 을 지정하여 값을 줄 수 있다.

```css
padding: 30px; /* 상하좌우 30px */
padding: 20px 10px; /* 상하 20px 좌우 10px */
padding: 40px 30px 20px 10px; /* 상우하좌 40,30,20,10px(시계방향) */
```

위와 같은 사용방식은 margin에도 적용할 수 있다.

### border

```css
border-width: 5px;
border-color: red;
border-style: dashed;
border: 5px dashed red; /* 위 3줄을 한번에 나타낼 수 있다 */
```

## display 속성

박스는 block이나 inline-block의 속성을 가진다.

### block

element의 크기와 상관없이 옆에 다른 element가 위치하는 것을 허용하지 않는다.

### inline-block

옆에 다른 element가 위치하는 것을 허용

### inline

블록이 아닌 텍스트처럼 적용이 된다.
(width, height 값을 줘도 적용이 되지 않음)

## position 속성

### static

기본값

### fixed

엘리먼트가 해당 위치에서 화면에 고정된다(다른 엘리먼트와 오버랩됨).

```css
top: 300px;
left: 300px;
```

위와 같이 위치값을 줘 위치를 정할 수 있음.

### absolute

```css
.abs-box {
  width: 400px;
  height: 400px;
  background-color: yellow;
  position: relative;
}
.abs-child {
  width: 100px;
  height: 100px;
  background-color: green;
  position: absolute;
  right: 10px;
  top: 10px;
}
```

```html
<div class="abs-box">
  <div class="abs-child"></div>
</div>
```

absolute position 의 경우 relative position 을 가지고 있는 부모를 찾아서 그 부모를 기준으로 top, right 등의 위치속성을 적용시킬 수 있다.
relative positon 을 가진 부모가 없을 경우 body에 맞춰서 위치를 잡는다.

## display: flex

부모 박스에만 flex 속성을 주면 자식 박스 혹은 contents들을 flex 방식으로 다룰 수 있다.

```css
justify-content: center;
align-items: flex-start;
flex-direction: row;
flex-wrap: wrap;
```

flex에서는 위와 같은 속성을 사용할 수 있다.

justify-content 는 수평정렬을, align-items는 수직 정렬을 정한다.
flex-direction의 기본값은 row이며 column을 주면 수직, 수평이 바뀐다.
flex-wrap의 기본값은 nowrap이며 기본값일 경우 창 크기를 줄이면 박스들의 크기가 작아지는데,
wrap을 주면 박스들의 크기가 줄어들지 않고 화면을 나가는 박스들이 다음줄로 넘어간다.

## pseudo-selector

스타일을 지정할 때 class나 id 말고 특정 attribute를 선택자로 사용할 수 있다.

```css
input[name="id"] {
  background-color: powderblue;
}
```

name값이 id인 input의 배경색을 powderblue로 변경.

## 구조적 가상 클래스

```css
.box:nth-child(2n + 1) {
  background-color: yellow;
}
```

box 클래스의 2n+1 번쨰 child들의 배경색을 yellow로 변경

## 인접형제 선택자

```css
#uni + .box {
  background-color: red;
}
```

#uni 바로 뒤에 오는 .box를 선택

## 자손 선택자

```css
.box > .child {
  background-color: peru;
}
```

.box 의 **직계자손**인 .child를 선택

## 여러 선택자 조합

```css
.box#uni[name="cake"] {
  height: 200px;
}
```

여러 선택자를 조합하여 사용할 수 있음.

## CSS States

```css
.box {
  background-color: red;
  font-size: 40px;
}
.box:hover {
  background-color: pink;
}
.box:active {
  background-color: green;
}
.box:focus {
  background-color: powderblue;
}
```

hover : 위에 커서가 있을 때
active : 클릭되었을 때
focus : 포커스 되었을 때

## Transitions

속성의 변화에 특수효과를 줄 수 있다.
트랜지션은 hover, active, focus에서 효과적으로 적용이 된다.

```css
.box {
  background-color: green;
  color: white;
  transition: background-color 0.5s ease-in-out;
}
.box:hover {
  background-color: red;
}
```

The **transition** CSS property is a shorthand property for **transition-property**, **transition-duration**, **transition-timing-function**, and **transition-delay**.

**transition-property** 부분에는 특정 속성(color, background-color 등등)을 주거나 모든 속성에 적용하고 싶을 때는 **all** 을 준다.

### **transition-timing-function**의 속성값

|          값           | 설명                                                                                                  |
| :-------------------: | :---------------------------------------------------------------------------------------------------- |
|        linear         | 전환(transition) 효과가 처음부터 끝까지 일정한 속도로 진행됩니다.                                     |
|         ease          | 기본값으로, 전환(transition) 효과가 천천히 시작되어, 그다음에는 빨라지고, 마지막에는 다시 느려집니다. |
|        ease-in        | 전환(transition) 효과가 천천히 시작됩니다.                                                            |
|       ease-out        | 전환(transition) 효과가 천천히 끝납니다.                                                              |
|      ease-in-out      | 전환(transition) 효과가 천천히 시작되어, 천천히 끝납니다.                                             |
| cubic-bezier(n,n,n,n) | 전환(transition) 효과가 사용자가 정의한 cubic-bezier 함수에 따라 진행됩니다.                          |

<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/transition">MDN - Transition</a>

## Transform

transform 속성은 엘리먼트의 형태를 다양하게 변화시킬 수 있다.

```css
.box {
  background-color: red;
  width: 500px;
  height: 500px;
  transform: rotate(20deg);
}
```

위 스타일은 20도(20deg) 회전한 500px\*500px 크기의 상자를 나타낸다.

```css
.box {
  background-color: red;
  width: 500px;
  height: 500px;
  transition: transform 0.5s ease-in-out;
}
.box:hover {
  transform: rotate(1turn) scale(0.5, 0.5);
}
```

위와 같이 transition과 결합하면 서서히 변하게 할 수 있다.

<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/transform">MDN - Transform</a>

## Animation

```css
.box {
  background-color: red;
  width: 100px;
  height: 100px;
  animation: 1.5s scaleAndRotateSquare infinite ease-in-out;
}
@keyframes scaleAndRotateSquare {
  /* 스테이지가 2개인 경우 from-to 사용
  from {
    transform: none;
  }
  to {
    transform: rotate(1turn) scale(0.5, 0.5);
  }
  */
  /* 스테이지가 여러개인 경우 n%로 직접 지정 */
  0% {
    transform: none;
  }
  50% {
    transform: rotate(1turn) scale(0.5, 0.5);
  }
  100% {
    transform: none;
  }
}
```

1. `@keyframes 애니메이션명` 으로 키프레임을 정의해준다.
2. Stage가 2개인 경우 from-to를 사용하고 원하는 만큼 스테이지를 설정하고 싶을 때는 n%로 스테이지들을 나눈다.
3. 선택자에 animation 속성 를 통해 지정할 애니메이션 및 옵션을 정해준다.
