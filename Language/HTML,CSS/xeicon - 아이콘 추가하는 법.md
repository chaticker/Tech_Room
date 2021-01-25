### CDN 설치
* XEICON의 CDN 주소를 적용하고자 하는 웹사이트의 <hrad>태그 영역에 styleseet를 불러오는 것 처럼 링크를 걸어주면 됨
* 아래 코드를 <head> 태그 안에 삽입
```html
 <link rel="stylesheet" href="//cdn.jsdelivr.net/gh/xpressengine/xeicon@2.3.1/xeicon.min.css">
```

### 사용법
* 기본 적용
  - <i>태그에 class명으로 아이콘의 종류를 선택
 
  ```html
    <i class="xi-xpressengine"> xpressengine </i>
  ```
  
* 아이콘 크기 변경  
  ```html
    <i class="xi-face xi-x"></i>
    <i class="xi-face xi-2x"></i> 
    <i class="xi-face xi-3x"></i> 
    <i class="xi-face xi-4x"></i> 
    <i class="xi-face xi-5x"></i>
  ```
  
[그 외 사용법](https://junistory.blogspot.com/2017/08/xeicon.html)
