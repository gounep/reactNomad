```html
<!DOCTYPE html>
<html>
  <body> 
    <span>Total clicks: 0</span> <!-- step 1 / HTML만들고-->
    <button id="btn">Click me</button>
  </body>
  <script>
    let counter = 0;
    const button = document.getElementById("btn"); // step 2 / JS로 가져와서
    const span = document.querySelector("span"); // step 2
    function handleClick() {
      counter = counter + 1; // step 4 (데이터를 업데이트하고)
      span.innerText = `Total clicks: ${counter}`; // step 5 / HTML 수정하는 방식
    }
    button.addEventListener("click", handleClick); // step 3 / (이벤트를 감지하고)
  </script>
</html>
```

