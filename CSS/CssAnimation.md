# CSSアニメーションメモ

## @keyframes内でdisplayプロパティは基本使えない（まだ）
世にあまり情報がないが、これは嘘で鵜呑みにしてはいけない。  
https://tnyk.jp/frontend/only-css-fadein/  

実際はChromeでしかサポートされていない（Chrome116から）
https://chromestatus.com/feature/5154958272364544

下記のようにアニメーションの終わりを待ってからdisplay:noneにするのが今のところは懸命
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CSS Animation</title>
  <style>
    @keyframes fadeOut {
      0% {
        opacity: 1;
      }

      100% {
        opacity: 0;
      }
    }

    .fade-out {
      animation: fadeOut 1s forwards;
    }
  </style>
</head>
<body>
  <div id="myElement" style="display: flex;">Hello, World!</div>
  <button onclick="fadeOutElement()">Fade Out</button>

  <script>
    function fadeOutElement() {
      const element = document.getElementById('myElement');
      element.classList.add('fade-out');
      
      element.addEventListener('animationend', () => {
        element.style.display = 'none';
      });
    }
  </script>
</body>
</html>
```

