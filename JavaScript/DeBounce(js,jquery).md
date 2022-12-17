### If you Click multiple at Time and send server request __accidentally__  then you can use This for Prevent multile __accidental Click__
__JS__
```javascript
  const btn = document.getElementById("button");
  function debounce(fn, delay) {
      let timeClear;
    return function () {
      if(timeClear){
          clearTimeout(timeClear);
      }
      timeClear = setTimeout(() => {
          return fn()
      }, delay);
    };
  }

  btn.addEventListener(
    "click",
    debounce(function () {
      console.log("Clicked");
    },250)
  );
```

__jQuery__
```javascript
  $(".my-btn").click($.debounce(250, function(e) {
      console.log("It works!");
  }));
```
