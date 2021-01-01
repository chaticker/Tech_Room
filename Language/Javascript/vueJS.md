### Vue.js란?

* 컴포넌트 기반의 SPA(Single Page Application)를 구축할 수 있게 해주는 프레임워크
  - 컴포넌트란
    * 웹을 구성하는 로고, 메뉴바, 버튼, 모달창 등 웹 페이지 내의 다양한 UI 요소
    * 재사용 가능하도록 구조화한 것
   
*    
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
