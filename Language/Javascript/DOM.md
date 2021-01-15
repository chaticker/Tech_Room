# DOM (Document Object Model)
텍스트 파일로 만들어져 있는 웹 문서를 브라우저에 렌더링하려면 웹 문서를 브라우저가 이해할 수 있는 구조로 메모리에 올려야 한다. 

브라우저의 렌더링 엔진은 웹 문서를 로드한 후, 파싱하여 웹 문서를 브라우저가 이해할 수 있는 구조로 구성하여 메모리에 적재하는데 이를 DOM이라 한다. 

즉 모든 요소와 요소의 어트리뷰트, 텍스트를 각각의 객체로 만들고 이들 객체를 부자 관계를 표현할 수 있는 트리 구조로 구성한 것이 DOM이다. 이 DOM은 자바스크립트를 통해 동적으로 변경할 수 있으며 변경된 DOM은 렌더링에 반영된다.

![image](https://user-images.githubusercontent.com/23302973/104024971-48873000-5207-11eb-882f-1145864f2199.png)

### 브라우저 동작 원리

브라우저는 웹 문서(HTML, XML, SVG)를 로드한 후, 파싱하여 DOM(문서 객체 모델: Document Object Model)을 생성한다.

이러한 웹 문서의 동적 변경을 위해 DOM은 프로그래밍 언어가 자신에 접근하고 수정할 수 있는 방법을 제공하는데 일반적으로 프로퍼티와 메소드를 갖는 자바스크립트 객체로 제공된다. 이를 DOM API(Application Programming Interface)라고 부른다. 달리 말하면 정적인 웹페이지에 접근하여 동적으로 웹페이지를 변경하기 위한 유일한 방법은 메모리 상에 존재하는 DOM을 변경하는 것이고, 이때 필요한 것이 DOM에 접근하고 변경하는 프로퍼티와 메소드의 집합인 DOM API이다.

DOM은 HTML, ECMAScript에서 정의한 표준이 아닌 별개의 W3C의 공식 표준이며 플랫폼/프로그래밍 언어 중립적이다. DOM은 다음 두 가지 기능을 담당한다.

1. HTML 문서에 대한 모델 구성
브라우저는 HTML 문서를 로드한 후 해당 문서에 대한 모델을 메모리에 생성한다. 이때 모델은 객체의 트리로 구성되는데 이것을 DOM tree라 한다.

2. HTML 문서 내의 각 요소에 접근 / 수정
DOM은 모델 내의 각 객체에 접근하고 수정할 수 있는 프로퍼티와 메소드를 제공한다. DOM이 수정되면 브라우저를 통해 사용자가 보게 될 내용 또한 변경된다.

# DOM tree
DOM tree는 브라우저가 HTML 문서를 로드한 후 파싱하여 생성하는 모델을 의미한다. 객체의 트리로 구조화되어 있기 때문에 DOM tree라 부른다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .red  { color: #ff0000; }
      .blue { color: #0000ff; }
    </style>
  </head>
  <body>
    <div>
      <h1>Cities</h1>
      <ul>
        <li id="one" class="red">Seoul</li>
        <li id="two" class="red">London</li>
        <li id="three" class="red">Newyork</li>
        <li id="four">Tokyo</li>
      </ul>
    </div>
  </body>
</html>
```

![image](https://user-images.githubusercontent.com/23302973/104024980-4e7d1100-5207-11eb-84a7-f36db9da7c91.png)

DOM tree

## DOM tree

DOM에서 모든 요소, 어트리뷰트, 텍스트는 하나의 객체이며 Document 객체의 자식이다. 요소의 중첩관계는 객체의 트리로 구조화하여 부자관계를 표현한다. DOM tree의 진입점(Entry point)는 document 객체이며 최종점은 요소의 텍스트를 나타내는 객체이다.

## DOM tree는 네 종류의 노드로 구성된다.

1. 문서 노드(Document Node)
트리의 최상위에 존재하며 각각 요소, 어트리뷰트, 텍스트 노드에 접근하려면 문서 노드를 통해야 한다. 즉, DOM tree에 접근하기 위한 시작점(entry point)이다.
2. 요소 노드(Element Node)
요소 노드는 HTML 요소를 표현한다. HTML 요소는 중첩에 의해 부자 관계를 가지며 이 부자 관계를 통해 정보를 구조화한다. 따라서 요소 노드는 문서의 구조를 서술한다고 말 할 수 있다. 어트리뷰트, 텍스트 노드에 접근하려면 먼저 요소 노드를 찾아 접근해야 한다. 모든 요소 노드는 요소별 특성을 표현하기 위해 HTMLElement 객체를 상속한 객체로 구성된다. (그림: DOM tree의 객체 구성 참고)
3. 어트리뷰트 노드(Attribute Node)
어트리뷰트 노드는 HTML 요소의 어트리뷰트를 표현한다. 어트리뷰트 노드는 해당 어트리뷰트가 지정된 요소의 자식이 아니라 해당 요소의 일부로 표현된다. 따라서 해당 요소 노드를 찾아 접근하면 어트리뷰트를 참조, 수정할 수 있다.
4. 텍스트 노드(Text Node)
텍스트 노드는 HTML 요소의 텍스트를 표현한다. 텍스트 노드는 요소 노드의 자식이며 자신의 자식 노드를 가질 수 없다. 즉, 텍스트 노드는 DOM tree의 최종단이다.

![image](https://user-images.githubusercontent.com/23302973/104024993-52109800-5207-11eb-937e-6e992ae94366.png)

DOM tree의 객체 구성

# DOM Query
1. 하나의 요소 노드 선택

![image](https://user-images.githubusercontent.com/23302973/104737861-27cf5500-5788-11eb-857d-149e2f014e4d.png)

* document.getElementById(id)
  - id 어트리뷰트 값으로 요소 노드를 한 개 선택한다. 복수개가 선택된 경우, 첫번째 요소만 반환한다.
  - Return: HTMLElement를 상속받은 객체
  - 모든 브라우저에서 동작

```javascript
// id로 하나의 요소를 선택한다.
const elem = document.getElementById('one');
// 클래스 어트리뷰트의 값을 변경한다.
elem.className = 'blue';

// 그림: DOM tree의 객체 구성 참고
console.log(elem); // <li id="one" class="blue">Seoul</li>
console.log(elem.__proto__);           // HTMLLIElement
console.log(elem.__proto__.__proto__); // HTMLElement
console.log(elem.__proto__.__proto__.__proto__);           // Element
console.log(elem.__proto__.__proto__.__proto__.__proto__); // Node
```

* document.querySelector(cssSelector)
  - CSS 셀렉터를 사용하여 요소 노드를 한 개 선택한다. 복수개가 선택된 경우, 첫번째 요소만 반환한다.
  - Return: HTMLElement를 상속받은 객체
  - IE8 이상의 브라우저에서 동작

```javascript
// CSS 셀렉터를 이용해 요소를 선택한다
const elem = document.querySelector('li.red');
// 클래스 어트리뷰트의 값을 변경한다.
elem.className = 'blue';
```

1. 여러개의 요소 노드 선택

![image](https://user-images.githubusercontent.com/23302973/104738153-7da3fd00-5788-11eb-960b-27cdd9ad2071.png)

* document.getElementsByClassName(class)
  - class 어트리뷰트 값으로 요소 노드를 모두 선택한다. 공백으로 구분하여 여러 개의 class를 지정할 수 있다.
  - Return: HTMLCollection (live)
  - IE9 이상의 브라우저에서 동작
  
```javascript
// HTMLCollection을 반환한다. HTMLCollection은 live하다.
const elems = document.getElementsByClassName('red');

for (let i = 0; i < elems.length; i++) {
  // 클래스 어트리뷰트의 값을 변경한다.
  elems[i].className = 'blue';
}
```
->이 코드 실행시키면 두 번째 요소만 변경이 안됨

->getElementsByClassName 메소드의 반환값은 HTMLCollection인데, 얘는 반환 값이 복수인 경우 배열과 비슷한 사용법을 가진 **'유사배열'** 임 또한 HTMLCollection은 실시간으로 Node의 상태 변경을 반영함 

->그렇담 왜 예상대로 동작이 안될까?

->이유: elems.length는 3이므로 3번의 loop가 실행

  1. i가 0일때, elems의 첫 요소(li#one.red)의 class 어트리뷰트의 값이 className 프로퍼티에 의해 red에서 blue로 변경된다. 이때 elems는 실시간으로 Node의 상태 변경을 반영하는 HTMLCollection 객체이다. elems의 첫 요소는 li#one.red에서 li#one.blue로 변경되었으므로 getElementsByClassName 메소드의 인자로 지정한 선택 조건(‘red’)과 더이상 부합하지 않게 되어 반환값에서 실시간으로 제거된다.

2. i가 1일때, elems에서 첫째 요소는 제거되었으므로 elems[1]은 3번째 요소(li#three.red)가 된다. li#three.red의 class 어트리뷰트 값이 blue로 변경되고 마찬가지로 HTMLCollection에서 제외된다.

3. i가 2일때, HTMLCollection의 1,3번째 요소가 실시간으로 제거되었으므로 2번째 요소(li#two.red)만 남았다. 이때 elems.length는 1이므로 for 문의 조건식 i < elems.length가 false로 평가되어 반복을 종료한다. 따라서 elems에 남아 있는 2번째 li 요소(li#two.red)의 class 값은 변경되지 않는다.

->해결법1:반복문을 역방향으로 돌림
```javascript
const elems = document.getElementsByClassName('red');

for (let i = elems.length - 1; i >= 0; i--) {
  elems[i].className = 'blue';
}
```

->해결법2:while 반복문을 사용. 이때 elems에 요소가 남아 있지 않을 때까지 무한반복하기 위해 index는 0으로 고정
```javascript
const elems = document.getElementsByClassName('red');

let i = 0;
while (elems.length > i) { // elems에 요소가 남아 있지 않을 때까지 무한반복
  elems[i].className = 'blue';
  // i++;
}
```

->해결법3:HTMLCollection을 배열로 변경한다. 이 방법을 권장
```javascript
const elems = document.getElementsByClassName('red');

// 유사 배열 객체인 HTMLCollection을 배열로 변환한다.
// 배열로 변환된 HTMLCollection은 더 이상 live하지 않다.
console.log([...elems]); // [li#one.red, li#two.red, li#three.red]

[...elems].forEach(elem => elem.className = 'blue');
```

->해결법4:querySelectorAll 메소드를 사용하여 HTMLCollection(live)이 아닌 NodeList(non-live)를 반환하게 한다.
```javascript
// querySelectorAll는 Nodelist(non-live)를 반환한다. IE8+
const elems = document.querySelectorAll('.red');

[...elems].forEach(elem => elem.className = 'blue');
```

* document.getElementsByTagName(tagName)
  - 태그명으로 요소 노드를 모두 선택한다.
  - Return: HTMLCollection (live)
  - 모든 브라우저에서 동작
```javascript
// HTMLCollection을 반환한다.
const elems = document.getElementsByTagName('li');

[...elems].forEach(elem => elem.className = 'blue');
```

* document.querySelectorAll(selector)
  - 지정된 CSS 선택자를 사용하여 요소 노드를 모두 선택한다.
  - Return: NodeList (non-live)
  - IE8 이상의 브라우저에서 동작
```javascript
// Nodelist를 반환한다.
const elems = document.querySelectorAll('li.red');

[...elems].forEach(elem => elem.className = 'blue');
```
