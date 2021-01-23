---
title: "Vue.js 시작"
date: 2021-01-14T11:30:03+00:00
weight: 1
aliases: ["/vuejs"]
tags: ["Vue.js"]
categories: ["Vue.js"]
series: ["Vue.js"]
author: "Me"
showToc: true
TocOpen: false
draft: false
hidemeta: false
disableShare: false
comments: false
---
## Vue.js 
### 정의
[Vue.js](https://vuejs.org/)
Frontend를 쉽게 접근할 수 있게 하는 JS library

### MVVM Pattern
MVC와 비슷하지만 다른 MVVM 패턴

#### MVC VS. MVVM 
 ![MVVM Pattern on Android | WOXAPP](https://woxapp.com/uploads/images/5_MVC.png)
**MVC**:  Controller와 Model이 Backend, View가 Frontend 
**MVVM**: 모든 요소가 Front이며 Javascript &HTML 

### 설치 

#### Vue.js 사이트에서 설치 script 가져와 Head tag 전에 삽입 


```javascript
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```
 ### 중요 문법 
#### Vue Instance 와 Key Attribute 
```javascript
<div id="app">
	<input  tyv-model="name"></div>  
<script>
let model = { "name": "hugo"};
let vm = new Vue({
	el: "app", 
	data: model
}); 
</script>
```

### 중요 문법: v-show, v-if, v-if-else
[v-show와 v-if](https://pa-pico.tistory.com/22)

- v-show는 style = display:none; 을 설정해서 condition filtering을 통해 모든 결과중 필요한 결과를 보여주는것 
- v-if 는 스타일 태그에 관한 변화가 아니라 필터링 된 결과만 출력 
