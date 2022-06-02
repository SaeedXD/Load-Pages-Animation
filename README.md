# Load-Pages-Animation
💡Navigate the pages of your site with Blur animation

## How to do ?
📌Add these codes to all pages of your website.
> HTML
```
<body>
  <div id="page_move_in" style="position: fixed;width: 100vw;height: 101vh;pointer-events: none;cursor: default;backdrop-filter: blur(50px);z-index: 999;transition: 0.3s;-webkit-transition: 0.3s;-moz-transition: 0.3s;-ms-transition: 0.3s;-o-transition: 0.3s;"></div>
  <div id="page_move_out" style="position: fixed;width: 100vw;height: 101vh;pointer-events: none;cursor: default;backdrop-filter: blur(0px);z-index: 999;transition: 0.3s;-webkit-transition: 0.3s;-moz-transition: 0.3s;-ms-transition: 0.3s;-o-transition: 0.3s;"></div>

  <!-- your codes ... -->
  ...
  ...
  ...
```

> JavaScript
```
  ...
  ...
  ...
	
	
  <script>
    window.addEventListener("load", function () {
    var page_move = document.querySelector("#page_move_in");
      page_move.style.backdropFilter = "blur(0px)";
      page_move.style.pointerEvents = "none";

      document.querySelectorAll('a').forEach((element) => {
        element.addEventListener('click', function (event) {
          let Url = this.getAttribute("href");
          let go;
          if (CTRL) {
            event.preventDefault();
            window.open(Url);
            CTRL = false;
            return;
          }
          if (Url.match(/https?:\/\/(www\.)?[-a-zA-Z0-9@:%._\+~#=]{1,256}\.[a-zA-Z0-9()]{1,6}\b([-a-zA-Z0-9()@:%_\+.~#?&\/\/=]*)/gi)) {
            go = true;
          } else {
            if (Url.match(/^#.*/ig)) {
              go = false;
            } else {
              go = true;
            }
          }
          if (go) {
            event.preventDefault();
            var page_move = document.querySelector('#age_move_out');
            page_move.style.backdropFilter = "blur(40px)";
            page_move.style.pointerEvents = "all";
            location.href = Url; 
          }
        });
      });
    });

    CTRL = false;
    window.addEventListener("keydown", function (e) {
      if (e.key == "Control") {
        CTRL = true;
      }
    });
    window.addEventListener("keyup", function (e) {
      if (e.key == "Control") {
        CTRL = false;
      }
    });
  </script>
</body>
```
