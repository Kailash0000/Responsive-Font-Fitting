<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>reactive text </title>
</head>
<body>
    <div id="box">
        <div id="text" contenteditable="true">Type here...</div>
      </div>
      
      <style>
        #box {
          width: 300px;
          height: 100px;
          border: 1px solid black;
          overflow: hidden;
          display: flex;
          align-items: center;
          justify-content: center;
          padding: 10px;
          resize: both;
        }
      
        #text {
          white-space: nowrap;
          outline: none;
          text-align: center;
          display: inline-block;
        }
      </style>
      
      <script>
        const box = document.getElementById("box");
        const text = document.getElementById("text");
      
        function adjustFontSize() {
          let fontSize = 35;// max font size
          text.style.fontSize = fontSize + "px";
      
          while (
            (text.scrollWidth > box.clientWidth || text.scrollHeight > box.clientHeight)
            && fontSize > 20//min font size 
          ) {
            fontSize--;
            text.style.fontSize = fontSize + "px";
          }
        }
      
        // Resize observer for box resizing
        new ResizeObserver(adjustFontSize).observe(box);
      
        // On user typing
        text.addEventListener("input", adjustFontSize);
      
        // Initial adjust
        adjustFontSize();
      </script>
      
</body>
</html>
