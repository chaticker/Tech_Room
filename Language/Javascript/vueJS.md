### Vue.js란?

* 컴포넌트 기반의 SPA(Single Page Application)를 구축할 수 있게 해주는 프레임워크
  - 컴포넌트란
    * 웹을 구성하는 로고, 메뉴바, 버튼, 모달창 등 웹 페이지 내의 다양한 UI 요소
    * 재사용 가능하도록 구조화한 것
   
* 기초 실습
```vue
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>뷰 기초 익히기</title>
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
</head>
<body>
    <!--뷰 인스턴스 생성-->
    <div id="app">
        {{ nextYear('안녕') }}
        <input v-bind:type="type" :value="inputData"> <!--데이터 바인딩: v-bind / :만있어도 가능 -->
        <a :href="getChatickerLink(chaticker)">차티커 홈페이지</a><br><br>
        <!--이벤트 넣기-->

        {{ year }} <br>
        <button v-on:click="plus">더하기</button>
        <button v-on:click="minus">빼기</button>

        <form v-on:submit = "submit">
            <input type="text"><br>
            <button type="submit">Submit</button>
        </form>
    </div>
    <script>
        /*변수 생성*/
        new Vue({
            el: '#app',
            data:{
                /*한 사람의 정보로 묶어서 생성*/
                person:{
                    name: '차티커',
                    age: 26
                },
                inputData: 'hello',
                type: 'number',
                link: 'https://itnext.io/the-css-preprocessor-dilemma-node-sass-or-dart-sass-32a0a096572',
                year: 2021
            },
            /*메소드 생성 -> 함수가 들어갈 수 있음*/
            methods:{
                getChatickerLink(channel){
                    return this.link + channel;
                },
                nextYear(greeting){
                    return greeting + '! ' + this.person.name + '는 내년에 ' + (this.person.age + 1) + '살 입니다.';
                },
                alert(){
                    alert('hello');
                },
                plus(){
                    this.year++;
                },
                minus(){
                    this.year--;
                },
                submit(){
                    alert('submitted');
                }
            }
        })
    </script>
</body>
</html>
```

* 데이터 양방향 바인딩 실습
```vue
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>뷰 기초 익히기</title>
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
</head>
<body>
    <div id="app">
        <form v-on:submit = "submit">
            <input type="text" v-model="text"><br> <!--양방향 바인딩이 필요할 땐 v-model씀-->>
            {{ text }}<br>
            <button type="submit">Submit</button>
        </form>
    </div>
    <script>
        new Vue({
            el: '#app',
            data:{
                text: 'text'
            },
            methods:{
                submit(){
                    alert('submitted');
                },
                // updateText(event){
                //     this.text = event.target.value;
                // }
            }
        })
    </script>
</body>
</html>
```
* console창에서의 키보드 이벤트 변화
![dfasdf](https://user-images.githubusercontent.com/23302973/103435826-a2ac5200-4c57-11eb-906e-9f762e3cfd60.PNG)

* target 내부의 value 값의 변화를 가지고 함수를 작성
```vue
updateText(event){
    console.log(event);
    this.text = event.target.value;
```
![캡처](https://user-images.githubusercontent.com/23302973/103435861-32520080-4c58-11eb-92ab-382137a9d7a0.PNG)
