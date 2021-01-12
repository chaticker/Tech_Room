### Vue.js란?

* 컴포넌트 기반의 SPA(Single Page Application)를 구축할 수 있게 해주는 프레임워크
  - 컴포넌트란
    * 웹을 구성하는 로고, 메뉴바, 버튼, 모달창 등 웹 페이지 내의 다양한 UI 요소
    * 재사용 가능하도록 구조화한 것
- - -

### 기초 실습
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
- - -

### 데이터 양방향 바인딩 실습
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

- - -
### computed 속성
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
        <button @click="changeMessage">Click</button>
        {{ reversedMessage }}
        {{ reversedMessage }}
        {{ reversedMessage }}
    </div>
    <script>
        new Vue({
            el: '#app',
            data:{
                message: '안녕하세요'
            },
            methods:{
                changeMessage(){
                    this.message = '차티커'; /*버튼 클릭 후 데이터가 바뀜*/
                }
            },
            computed:{ /*중복 속성을 관리할 수 있음 -> 괄호 없이 함수 사용 가능*/
                reversedMessage(){
                    return this.message.split('').reverse().join('')
                }
            }
        })
        /*methods와 computed의 차이점: computed는 캐싱을 함 -> 
        처음 한 번만 계산하고, 값이 저장이 되어 있어서 함수를 반복적으로 사용할 수 있음*/
    </script>
</body>
</html>
```

### 클래스 & 스타일 바인딩
```vue
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>뷰 기초 익히기</title>
    <style>
        .red{
            color: red;
        }
        .font-bold{
            font-weight: bold;
        }
    </style>
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
</head>
<body>
    <div id="app">
        <!--font-bold 같은 경우 ''안에 넣어줘야 함-->
        <div :style="{ color: red, fontSize: size}">Hello</div>
        <button @click="update">Click</button>
    </div>
    <script>
        new Vue({
            el: '#app',
            data:{
                red: 'red', /*false일 경우에는 class에 안들어감*/
                size: '30px'

            },
            methods:{
                update(){
                    this.isRed = !this.isRed;
                    this.isBold = !this.isBold;
                }
            }
        })
    </script>
</body>
</html>
```

### v-if와 v-show
```vue
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>뷰 기초 익히기</title>
    <style>
        .red{
            color: red;
        }
        .font-bold{
            font-weight: bold;
        }
    </style>
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
</head>
<body>
    <div id="app">
        <!--한번에 보여주기-->
        <!-- <template v-if='number === 1'>
            <div>1</div>
            <div>2</div>
            <div>3</div>
        </template>
        <div v-else-if="number === 2">hi</div>
        <div v-else>no</div> -->

        <!--v-if와 v-show의 차이점: if는 조건이 부적합이면 아예 렌더링 안하지만, show는 렌더링은 하되, 스타일로써 안보이게 함-->

        <div v-show="show">yes</div>
        <button @click="toggle">toggle</button>
    </div>
    <script>
        new Vue({
            el: '#app',
            data:{
                number: 1,
                show: false
            },
            methods:{
                increaseNumber(){
                    this.number++;
                },
                toggle(){
                    this.show = !this.show
                }
            }
        })
    </script>
</body>
</html>
```

### v-for 리스트 렌더링
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
        <div>
            {{ people[0].name }} {{people[0].age }}
        </div>
        <div>
            {{ people[1].name }} {{people[1].age }}
        </div>
        <div>
            {{ people[2].name }} {{people[2].age }}
        </div>

        <hr>

        <!--* key는 반드시 필요한 속성인데, 만일 중복이 있다면 전체를 '-'을 사용해 모두 입력
            * index를 따로 지정해서 key로 사용하는 것은 좋지 않은 방법 -> 왜? 중간에 값이 빠지면 인덱스 순서가 애매해지기 때문
            * 그래서 id값을 사용하는 것이 좋음 -> {id:3 , name: 'c', age: 23 }-->
        <div v-for="(person, index) in people" :key="person.name + '-'+ person.age"> <!--in 대신에 of를 써도 됨-->
            {{ person.name }} {{person.age }} {{ index }}
        </div>
    </div>
    <script>
        new Vue({
            el: '#app',
            data:{
               people: [
                   { name: 'a', age: 20 },
                   { name: 'b', age: 21 },
                   { name: 'c', age: 22 },
                   { name: 'c', age: 23 },
                ]
            },
            methods:{
                modal(){

                }
            },
        })
    </script>
</body>
</html>
```

### 여러개의 뷰 인스턴스 사용하기
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
        {{ name }}<br>
        <button @click="changeText">Click</button>
    </div>

    <div id="app-1">
        {{ name }}<br>
        <button @click="changeText">Click</button>
    </div>
    <script>
        /*다른 인스턴스에서 변경하고 싶을 때 -> 변수에 담아서 사용*/
        const app = new Vue({
            el: '#app',
            data:{
               name: 'cha'
            },
            methods:{
                changeText(){
                    app1.name = 'chaticker updated';
                }
            },
        })

        const app1 = new Vue({
            el: '#app-1',
            data:{
                name: 'cha'
            },
            methods:{
                changeText(){
                    app.name = 'chaticker updated1';
                }
            },
        })
    </script>
</body>
</html>
```

### 뷰 컴포넌트
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
        <!-- {{ name }}<br>
        <button @click="changeText">Click</button>

        <hr> -->

        <cha-button></cha-button> <!--컴포넌트를 이용한 코드-->
    </div>
    <hr><hr>
    <div id="app-1">
        <!-- {{ name }}<br>
        <button @click="changeText">Click</button>

        <hr> -->

        <cha-button></cha-button>
    </div>

    <script>
        /*컴포넌트 내부에서 다른 컴포넌트 사용하기*/
        Vue.component('hello-world', {
            template: '<div>Hello World</div>'
        })
        /*인스턴스의 중복을 제거하기 위해 사용하는 것이 컴포넌트 -> 만들어 놓으면 아무데나 사용 가능*/
        /*컴포넌트의 전역 등록*/
        Vue.component('cha-button', {
            /*템플릿 내에서는 하나의 태그 안에 코드가 존재 해야함*/
            template: ` 
            <div>
                {{ name }}<br>
                <hello-world></hello-world> 
                <button @click="changeText">Click</button>
            </div>    
            `
            ,
            /*컴포넌트에서 데이터는 함수 형태로 만들어서 리턴해야 함*/
            data() {
                return {
                    name: 'cha'
                }
            },
            methods:{
                changeText(){
                    this.name = 'chaticker updated';
                }
            },
        })
        
        const helloWorld = {
            template: '<div>Hello World</div>'
        };

        /*컴포넌트의 지역 등록*/
        const chaButton = {
            components: {
                'hello-world': helloWorld
            },
            template: ` 
            <div>
                {{ name }}<br>
                <hello-world></hello-world> 
                <button @click="changeText">Click</button>
            </div>    
            `
            ,
            data() {
                return {
                    name: 'cha'
                }
            },
            methods:{
                changeText(){
                    this.name = 'chaticker updated';
                }
            },
        };
        
        const app = new Vue({
            el: '#app',
            components:{
                'cha-button': chaButton
            }
            // data:{
            //    name: 'cha'
            // },
            // methods:{
            //     changeText(){
            //         this.name = 'chaticker updated';
            //     }
            // },
        })

        const app1 = new Vue({
            el: '#app-1',
            components:{
                'cha-button': chaButton
            }
            // data:{
            //     name: 'cha'
            // },
            // methods:{
            //     changeText(){
            //         this.name = 'chaticker updated';
            //     }
            // },
        })
    </script>
</body>
</html>
```

### 싱글 파일 컴포넌트
[노션](https://www.notion.so/Single-File-Component-66bdd89ad6a64c15b7026764d251b0a5)

### 자식 컴포넌트에 데이터 보내기 (props)
[노션](https://www.notion.so/Props-66729172ce2d42f1aaea130c9799a04b)

## 부모 컴포넌트로 데이터 보내기 (Emit)
[노션](https://www.notion.so/Emit-4da2d4bfa601475e8baacb6d928525bc)
