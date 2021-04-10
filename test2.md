#### # https://www.youtube.com/watch?v=tYBIdgZrUKM
#### # data
```html
    {{person.name}} /
    {{person.age}} 
```
```js
    <script>
        new Vue({
            el:"#app",
            data : {
                person : {
                    name : "ji hoon",
                    age: 46
                },
                type:"number",
                inputValue:"1234"
            },
        })
    </script>
```
#### # v-bind data bind
```html
<input style="border: 1px solid red" v-bind:type="type" v-bind:value="inputValue"/> 
<!-- is same -->
<input style="border: 1px solid red" :type="type" :value="inputValue"/> 
```

#### # v-on event bind
```html
<button v-on:click="plus">plus</button>
<button v-on:click="minus"  >minus</button>
<!-- is same -->
<button @click="plus">plus</button>
<button @click="minus">minus</button>
```
: 이벤트 수식어 : 
 - https://v3.ko.vuejs.org/guide/events.html#%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A6%E1%86%AB%E1%84%90%E1%85%B3-%E1%84%89%E1%85%AE%E1%84%89%E1%85%B5%E1%86%A8%E1%84%8B%E1%85%A5
   - .stop
   - .prevent
   - .capture
   - .self
   - .once
   - .passive
   - 
```html
<form v-on:submit.prevent="submit" action="http://naver.com">
    <input type="text"><br>
    <button type="submit">submit</button>
</form>

<a @click.stop="doThis"></a>

<!-- 제출 이벤트가 페이지를 다시 로드하지 않습니다. -->
<form @submit.prevent="onSubmit"></form>

<!-- 수정자는 체이닝이 가능합니다. -->
<a @click.stop.prevent="doThat"></a>

<!-- 단순히 수식어만 사용이 가능합니다. -->
<form @submit.prevent></form>

<!-- 캡처 모드를 사용할 때 이벤트 리스너를 사용 가능합니다.-->
<!--즉, 내부 엘리먼트를 대상으로 하는 이벤트가 해당 엘리먼트에서 처리되기 전에 여기서 처리합니다. -->
<div @click.capture="doThis">...</div>

<!-- event.target이 엘리먼트 자체인 경우에만 트리거를 처리합니다.-->
<!-- 자식 엘리먼트에서는 처리되지 않습니다.-->
<div @click.self="doThat">...</div>
```

#### # v-model
```html
<form v-on:submit.prevent="submit" action="http://naver.com">
    <input type="text" :value="text" @keyup="updateText"><br>
    <input type="text" :value="text"><br>
    <input type="text" v-model="text"><br>
    <button type="submit">submit</button>
</form>
```

### # computed 
 - getter, setter를 이용한 data변수이다.
 - method를 이용해도 동일한 결과를 만들지만,
 - computed는 캐싱된다.
 - https://v3.ko.vuejs.org/guide/computed.html#computed-속성
: html
```html
    <div id="app">
        <input type="text" v-model="msg">
        <button @click="changeMessage(msg)">click</button>
        {{reverseMessage}}
    </div>
```
: js
```js
    new Vue({
        el:"#app",
        data : {
            msg:"",
            helloMessage : "안녕하세요"
        },
        methods : {
            changeMessage(v){
                this.helloMessage = v?"직접:"+v:this.msg;
            }
        },
        computed :{
            reverseMessage() {
                return this.helloMessage.split("").reverse().join("");
            }
        }
    });
```
```js
computed: {
  fullName: {
    // getter
    get() {
      return this.firstName + ' ' + this.lastName
    },
    // setter
    set(newValue) {
      const names = newValue.split(' ')
      this.firstName = names[0]
      this.lastName = names[names.length - 1]
    }
  }
}
```
```js
    this.firstName = "지훈 김";
```

#### # watch
 - watch는 data이름과 동일한이름의 함수다.
 - data가 변경될때 실행되는 함수다.
 - newValue, oldValue를 인자로 갖는다.
 - computed는 data다.

: html
```html
    {{messageUpdated?"갱신됨":"갱신전"}}
```

: js
```js
    watch: {
        helloMessage(newValue, oldValue) {
            console.log(newValue,oldValue);
            this.messageUpdated = true;
        }
    }
```

#### # class
 - https://v3.ko.vuejs.org/guide/class-and-style.html#%E1%84%80%E1%85%A2%E1%86%A8%E1%84%8E%E1%85%A6-%E1%84%80%E1%85%AE%E1%84%86%E1%85%AE%E1%86%AB

: html
```html
<div id="app">
	<div :class="{red: isRed, bold: isBold}">Hello</div>
	<button @click="updateColor">Click</button>
</div>
```

: js
```js
<script>
    new Vue({
        el:"#app",
        data : {
			isRed:false,
			isBold:false,
        },
        methods : {
			updateColor(){
				this.isRed = !this.isRed;
				this.isBold = !this.isBold;
			},
        },
    });
</script>
```

#### # style
 - https://v3.ko.vuejs.org/guide/class-and-style.html#인라인-스타일-바인딩하기

: html
```html
<div id="app">
	<div :style="{color: red, fontSize: size}">Hello</div>
</div>
```
: js
```js
<script>
    new Vue({
        el:"#app",
        data : {
			red:"red",
			size:"30px",
        }
    });
</script>
```

#### # v-if
 - https://v3.ko.vuejs.org/guide/conditional.html#v-if
: html
```html
<div id="app">
	<template v-if="show">
		<div>t-if1</div>
		<div>t-if2</div>
		<div>t-if3</div>
		<div>t-if4</div>
	</template>
			<div v-if="show">if1</div>
			<div v-if="show">if2</div>
			<div v-if="show">if3</div>
			<div v-if="show">if4</div>
			<div v-else="show">else</div>
			<button @click="toggleShow">toggleShow</button>
		</div>
</div>
```
: js
```js
<script>
    new Vue({
        el:"#app",
        data : {
			show:true,
        },
        methods : {
			toggleShow() {
				this.show = !this.show;
			},
        },
    });
</script>
```

#### # v-show
 - https://v3.ko.vuejs.org/guide/conditional.html#v-if-%E1%84%83%E1%85%A2-v-show
 - v-show는 렌더링은 되고 display none임


---- https://www.youtube.com/watch?v=HAegTAEW1Y0