## Next JS란?
리액트 프레임 워크

## UI렌더링
- 방문자가 웹페이지를 방문하면 브라우져는 HTML코드를 읽고 DOM을 설계함  
- DOM이란 HTML을 대표하는 object
- DOM 과 Js를 이용하여 DOM을 조작가능 =>  element를 선택하고 스타일과 내용 변경 가능
- imperative programming(절차형) : DOM vs Declartive(선언형) programming : HTML
```html
<!-- index.html -->
<html>
  <body>
    <!-- div - id : app -->
    <div id="app"></div>
    <!-- js를 통한 편집 가능 -->
    <script type="text/javascript">
      // DOM STYLE
      // app(id : app) elment 선택 
      const app = document.getElementById('app');
      // h1 header element 생성
      const header = document.createElement('h1');
      // textnode 생성 : headerContent
      const headerContent = document.createTextNode(
        'Develop. Preview. Ship. 🚀',
      );
      // h1 header의 자식 headerContent
      header.appendChild(headerContent);
      // div app의 자식 h1 header
      app.appendChild(header);
    </script>
  </body>
</html>
```
<!-- index.html -->
<html>
  <body>
    <!-- div - id : app -->
    <div id="app">
      <!-- HTML STYLE -->
      <h1>Develop. Preview. Ship. 🚀</h1>
    </div>
  </body>
</html>
```