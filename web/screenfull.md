# HTML页面全屏和退出全屏

```markup
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>页面全屏/退出全屏</title>
</head>

<body>
    <a class="screen-full" id="full" href="javascript:;">全屏</a>
</body>

</html>
<script src="https://code.jquery.com/jquery-3.2.1.min.js"></script>
<script>
$('#full').click(function() {
    var ele = document.documentElement;
    var SCREEN_FULL_TEXT = "全屏";
    var SCREEN_REST_TEXT = "退出全屏";
    var SCREEN_FULL = 'screen-full';
    var SCREEN_REST = 'screen-restore';
    var iconElem = $(this);
    if (iconElem.hasClass(SCREEN_FULL)) {
        var reqFullScreen = ele.requestFullScreen || ele.webkitRequestFullScreen || ele.mozRequestFullScreen || ele.msRequestFullscreen;
        if (typeof reqFullScreen !== 'undefined' && reqFullScreen) {
            reqFullScreen.call(ele);
        };
        iconElem.addClass(SCREEN_REST).removeClass(SCREEN_FULL);
        iconElem.text(SCREEN_REST_TEXT);
    } else {
        if (document.exitFullscreen) {
            document.exitFullscreen();
        } else if (document.mozCancelFullScreen) {
            document.mozCancelFullScreen();
        } else if (document.webkitCancelFullScreen) {
            document.webkitCancelFullScreen();
        } else if (document.msExitFullscreen) {
            document.msExitFullscreen();
        }
        iconElem.addClass(SCREEN_FULL).removeClass(SCREEN_REST);
        iconElem.text(SCREEN_FULL_TEXT);
    }
});
</script>
```

