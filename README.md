<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xml:lang="en" xmlns="http://www.w3.org/1999/xhtml"><head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
		<title>HBD love </title>	    
        <link type="text/css" rel="stylesheet" href="./file/default.css">
		<script type="text/javascript" src="./file/jquery.min.js"></script>
		<script type="text/javascript" src="./file/jscex.min.js"></script>
		<script type="text/javascript" src="./file/jscex-parser.js"></script>
		<script type="text/javascript" src="./file/jscex-jit.js"></script>
		<script type="text/javascript" src="./file/jscex-builderbase.min.js"></script>
		<script type="text/javascript" src="./file/jscex-async.min.js"></script>
		<script type="text/javascript" src="./file/jscex-async-powerpack.min.js"></script>
		<script type="text/javascript" src="./file/functions.js" charset="utf-8"></script>
		<script type="text/javascript" src="./file/love.js" charset="utf-8"></script>
        <script>
            function playAudio() {
                var audio = document.getElementById("myAudio");
                audio.play();
            }
        </script>
	    <style type="text/css">
        </style>
</head>
    <body>
        <div id="main">
            <div id="error">，<a href="http://www.google.cn/chrome/intl/zh-CN/landing_chrome.html?hl=zh-CN&brand=CHMI">Chrome</a>(<a href="http://firefox.com.cn/download/">Firefox</a>)</div>
            <audio autoplay="autoplay" height="100" width="100" id = "myAudio">
                    <source src="aud.mp3" type="audio/mp3" />
                    <embed height="100" width="100" src="aud.mp3" />
            </audio>
            <div id="wrap">
                <div id="text">
                    <div id="code">
                      <span class="say"> Happy Birthday  </span><br>
                      <span class="say">My gorgeous 🪷 </span><br>             
                      <span class="say">✨💐My sweet hearted madam ji 💐✨</span><br>             
                      <span class="say">Happiest birthday to you </span><br>
                      <span class="say">🌸 Radhika madam ji 🌸</span><br>
                      <span class="say">🫶 Miss 18🫰🥰 </span><br>
                      <span class="say">🥳🥳🥳Many many returns of the day🎊🎊🎊🎉🎉🎉 </span><br>
                      <span class="say"> God bless you 😇🤞</span><br>
                      <span class="say">you entered a new phase of your life, you will create some best memories i hope god always bless you and take care of your health, and also i want to say thanks to you for everything that you do for me i hope your all dreams will complete and you will achieve what you want in your life...😊 Once again happiest birthday radhi....🤗.  </span><br>
                      <span class="say">Always stay happy and keep smiling 😁😉<span class="space"></span></span> </font>
                          <br />
                          <br />
                      </p>
                    </div>
                  </div>

                  <div id = "message-box"></div>
                <div id="clock-box">
                    <span class="STYLE1"></span><font color="#33CC00"></font>
<span class="STYLE1"></span>
                  <div id="clock"></div>
              </div>
                <canvas id="canvas" width="1100" height="680"></canvas>
            </div>

        </div>

    <script>
    </script>

    <script>
    (function(){
        var canvas = $('#canvas');

        if (!canvas[0].getContext) {
            $("#error").show();
            return false;        }

        var width = canvas.width();
        var height = canvas.height();        
        canvas.attr("width", width);
        canvas.attr("height", height);
        var opts = {
            seed: {
                x: width / 2 - 20,
                color: "rgb(190, 26, 37)",
                scale: 2
            },
            branch: [
                [535, 680, 570, 250, 500, 200, 30, 100, [
                    [540, 500, 455, 417, 340, 400, 13, 100, [
                        [450, 435, 434, 430, 394, 395, 2, 40]
                    ]],
                    [550, 445, 600, 356, 680, 345, 12, 100, [
                        [578, 400, 648, 409, 661, 426, 3, 80]
                    ]],
                    [539, 281, 537, 248, 534, 217, 3, 40],
                    [546, 397, 413, 247, 328, 244, 9, 80, [
                        [427, 286, 383, 253, 371, 205, 2, 40],
                        [498, 345, 435, 315, 395, 330, 4, 60]
                    ]],
                    [546, 357, 608, 252, 678, 221, 6, 100, [
                        [590, 293, 646, 277, 648, 271, 2, 80]
                    ]]
                ]] 
            ],
            bloom: {
                num: 700,
                width: 1080,
                height: 650,
            },
            footer: {
                width: 1200,
                height: 5,
                speed: 10,
            }
        }

        var tree = new Tree(canvas[0], width, height, opts);
        var seed = tree.seed;
        var foot = tree.footer;
        var hold = 1;

        canvas.click(function(e) {
            playAudio();
            console.log("Helloworld!");
            var offset = canvas.offset(), x, y;
            x = e.pageX - offset.left;
            y = e.pageY - offset.top;
            if (seed.hover(x, y)) {
                hold = 0; 
                canvas.unbind("click");
                canvas.unbind("mousemove");
                canvas.removeClass('hand');
            }
        }).mousemove(function(e){
            var offset = canvas.offset(), x, y;
            x = e.pageX - offset.left;
            y = e.pageY - offset.top;
            canvas.toggleClass('hand', seed.hover(x, y));
        });



        var seedAnimate = eval(Jscex.compile("async", function () {
            seed.draw();
            while (hold) {
                $await(Jscex.Async.sleep(10));
            }
            while (seed.canScale()) {
                seed.scale(0.95);
                $await(Jscex.Async.sleep(10));
            }
            while (seed.canMove()) {
                seed.move(0, 2);
                foot.draw();
                $await(Jscex.Async.sleep(10));
            }
        }));

        var growAnimate = eval(Jscex.compile("async", function () {
            do {
    	        tree.grow();
                $await(Jscex.Async.sleep(10));
            } while (tree.canGrow());
        }));

        var flowAnimate = eval(Jscex.compile("async", function () {
            do {
    	        tree.flower(2);
                $await(Jscex.Async.sleep(10));
            } while (tree.canFlower());
        }));

        var moveAnimate = eval(Jscex.compile("async", function () {
            tree.snapshot("p1", 240, 0, 610, 680);
            while (tree.move("p1", 500, 0)) {
                foot.draw();
                $await(Jscex.Async.sleep(10));
            }
            foot.draw();
            tree.snapshot("p2", 500, 0, 610, 680);

            canvas.parent().css("background", "url(" + tree.toDataURL('image/png') + ")");
            canvas.css("background", "#ffe");
            $await(Jscex.Async.sleep(300));
            canvas.css("background", "none");
        }));

        var jumpAnimate = eval(Jscex.compile("async", function () {
            var ctx = tree.ctx;
            while (true) {
                tree.ctx.clearRect(0, 0, width, height);
                tree.jump();
                foot.draw();
                $await(Jscex.Async.sleep(25));
            }
        }));

        var textAnimate = eval(Jscex.compile("async", function () {
		    var together = new Date();
		    together.setFullYear(2005, 25, 12); 			
		    together.setFullYear(2002, 20, 09); 			
		    together.setHours(20);						
		    together.setMinutes(0);					
		    together.setSeconds(0);					
		    together.setMilliseconds(2);				

		    $("#code").show().typewriter();
            $("#clock-box").fadeIn(500);
            while (true) {
                timeElapse(together);
                $await(Jscex.Async.sleep(1000));
            }
        }));

        var runAsync = eval(Jscex.compile("async", function () {
            $await(seedAnimate());
            $await(growAnimate());
            $await(flowAnimate());
            $await(moveAnimate());

            textAnimate().start();

            $await(jumpAnimate());
        }));

        runAsync().start();
    })();
    </script></body></html>
