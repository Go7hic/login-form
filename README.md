# login_form

忘记在哪里看到的这个效果，当时就被这个体验给吸引了，卖的一手好萌啊。如果你也想让你的网站用户体验下可以试试哦。

DEMO：
[http://jsfiddle.net/gothic/m2wrdptL/2/](http://jsfiddle.net/gothic/m2wrdptL/2/)


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>login form</title>
    <style>
        .mod {
            position: relative;
            padding: 50px;
        }
        .login-form {
            position: relative;
            width: 300px;
            padding-top: 25px;
            margin: 100px auto;
        }
        .login-form input {
            width: 300px;
            height: 40px;
            margin-bottom: 10px;
            border-radius: 4px;
            border: 1px solid #ccc;
            text-indent: 10px;

        }
        .avatar {
            width: 100%;
            /*background-color: #FFF;*/
            position: absolute;
            top: -100px;
            -webkit-user-select: none;  /* 1 */
            -moz-user-select: none;  /* 1 */
            -ms-user-select: none;  /* 1 */
            -o-user-select: none;  /* 1 */
            user-select: none;  /* 1 */
        }

        /* 头*/
        .cabeca {
            background-color: #E35C49;
            height: 100px;
            width: 130px;
            margin: 0 auto;
            border-radius: 50% 50% 0 0;
            position: relative;
        }

        .orelha, .olhos, .narinas, .dentes { position: absolute; }

        /* 耳朵 */
        .orelha {
            width: 35px;
            height: 35px;
            border-radius: 50%;
            background-color: #E25441;
            top: 0;
            /*  z-index: -1;*/
            transform: translateY(-25%);
        }

        .orelha-esq {
            left: 10px;
            box-shadow: inset 3px 5px 0 #E35C49;
        }

        .orelha-dir {
            right: 10px;
            box-shadow: inset -3px 5px 0 #E35C49;
        }

        /* 眼睛*/
        .olhos {
            width: 35px;
            height: 35px;
            background-color: #FFF;
            border-radius: 50%;
            top: 30px;
            overflow: hidden;

            box-shadow: inset 0 1px 2px rgba(0,0,0,0.8);

            transition: all 0.05s ease;
        }

        .olhos .palpebra {
            background-color: #E25441;
            position: absolute;
            width: 100%;
            z-index: 2;
            border-radius: 50%;

            -webkit-animation: piscar 1.5s linear infinite alternate;
            animation: piscar 1.5s linear infinite alternate;
        }

        /* 眨眼动画 */
        @-webkit-keyframes piscar {
            0% { height: 0; }
            95% { height: 0; }
            100% { height: 100%; }
        }

        @keyframes piscar {
            0% { height: 0; }
            95% { height: 0; }
            100% { height: 100%; }
        }

        /* 手臂动画 */
        .olhos.fechar .palpebra {
            -webkit-animation: paused;  /*1*/
            animation: paused;  /*1*/
        }

        .olho-esq { left: 25px; }
        .olho-dir { right: 25px; }

        .olhos::before,
        .olhos::after {
            content: " ";
            display: block;
            position: absolute;
            border-radius: 50%;
            z-index: 1;
        }

        .olhos::before {
            bottom: 1px;
            background-color: #000;
            width: 10px;
            height: 10px;
            left: 50%;

            transform: translateX(-50%);
        }

        .olhos::after {
            width: 5px;
            height: 5px;
            background-color: #FFF;
            bottom: 7px;
            left: 18px;
        }

        /* 鼻子 */
        .narinas {
            width: 10px;
            height: 10px;
            background-color: rgba(255,255,255,0.2);
            border-radius: 50%;
            box-shadow: inset 0 2px 2px rgba(0,0,0,0.3);
            top: 70px;
        }

        .narina-esq { left: 50px; }
        .narina-dir { right: 50px; }

        /* 牙齿 */
        .dentes {
            width: 25px;
            height: 20px;
            background-color: #EAEAEA;
            border-radius: 0 0 3px 3px;
            bottom: -20px;
        }

        .dente-esq { left: 30px; }
        .dente-dir { right: 30px; }

        /* 手臂 */
        .bracos {
            position: absolute;
            right: 0;
            bottom: 0;
            left: 0;
        }

        .bracos .mao {
            width: 50px;
            height: 40px;
            border-radius: 50%;
            background-color: #E25441;
            position: absolute;
            bottom: 0;
            overflow: hidden;
            z-index: 5;

            box-shadow: 0 2px 0 rgba(0,0,0,0.2), inset 0 2px 0 rgba(0,0,0,0.1);

            transform: translateY(50%);

            transition: all 0.3s ease-out;
        }

        .bracos .mao-esq { left: 30px; }
        .bracos .mao-dir { right: 30px; }

        .mao .unha {
            background-color: rgba(255,255,255,0.2);
            width: 10px;
            height: 10px;
            border-radius: 50% 50% 0 0;
            position: absolute;
            bottom: 0;
            left: 10px;

            box-shadow: 20px 0 0 rgba(255,255,255,0.2);
        }

        /* 遮眼 */
        .esconder .mao {
            height: 75px;
            bottom: 30px;
            box-shadow: 0 0 0 rgba(0,0,0,0), inset 0 2px 0 rgba(0,0,0,0.1);
        }

        .esconder .mao-esq {
            left: 90px;
            transform: translateY(50%) rotate(-125deg);
        }

        .esconder .mao-dir {
            right: 90px;
            transform: translateY(50%) rotate(125deg);
        }

    </style>
</head>
<body>
    <div class="mod">
        <form action="" id="login_form" class="login-form">
         <input type="email" placeholder="邮箱" >
         <input type="password" id="password" placeholder="密码">
     </form>
 </div>
 <script>
    var template = [
        '<div class="avatar">',
        '   <div class="cabeca">',
        '       <div class="orelha-esq orelha"></div>',
        '       <div class="orelha-dir orelha"></div>',
        '       <div class="olho-esq olhos">',
        '           <div class="palpebra"></div>',
        '       </div>',
        '       <div class="olho-dir olhos">',
        '           <div class="palpebra"></div>',
        '       </div>',
        '       <div class="narina-esq narinas"></div>',
        '       <div class="narina-dir narinas"></div>',
        '       <div class="dente-esq dentes"></div>',
        '       <div class="dente-dir dentes"></div>',
        '   </div>',
        '   <div class="bracos" id="bracos">',
        '       <div class="mao-esq mao">',
        '           <div class="unha"></div>',
        '       </div>',
        '       <div class="mao-dir mao">',
        '           <div class="unha"></div>',
        '       </div>',
        '   </div>',
        '</div>'
    ].join("");
    var isIE9_ = document.all && !window.atob; //判断 IE9- 浏览器
    if (!isIE9_) {
       $("#login_form").prepend(template);
        $("#password").on({
            "focus": function() {
                $("#bracos").addClass("esconder");
                $(".olhos").addClass("fechar");
            },
            "focusout": function() {
                $("#bracos").removeClass("esconder");
                $(".olhos").removeClass("fechar");
            }
        })
    }
</script>
</body>
</html>

```
