<!DOCTYPE html>
<html>

<head>

    <title>Тестовое задание</title>
    <meta charset="UTF-8">
    <link href="css/main.css" rel="stylesheet" type="text/css">
    <link href="css/media.css" rel="stylesheet" type="text/css">

</head>

<body>

<div class="wrapper">

    <div class="middle">

        <div class="content">

                <div class="block1">

                    <div class="block_tochka1">

                        <div class="text_tochka1">

                            <div class="header_tochka1">Тестовое задание</div>

                            <div class="keep_tochka1">

                                На экранах до 1024px показывать CSS-анимацию.
                                При клике на кнопку плавный scroll до следующего блока.

                            </div>

                            <div class="bt">

                                <div class="button_tochka1">

                                    <a class="button" href="#nav">Подробнее</a>

                                </div>

                            </div>

                        </div>

                    </div>

                    <div class="block_tochka2">

                        <div class="img_tochka2">

                            <img src="file/img/images/splash.png" class="animation">
                            <img src="file/img/images/shadow.png" class="animation an-2">
                            <img src="file/img/images/wallet.png" class="an-1 animation">

                        </div>

                    </div>

                </div>

            </div>

        <div class="bx">

            <div class="content2">

            <div class="block2">

                <div class="block2_tochka1">

                    <div class="header_tochka3" id="nav">Колонки с иконками</div>

                    <div class="block_icons">

                        <ul>

                            <li><a href="#"><img src="file/img/icon3.png" alt=""> Банковские карты</a></li>
                            <li><a href="#"><img src="file/img/icon2.png" alt=""> Мессенджер</a></li>
                            <li><a href="#"><img src="file/img/icon4.png" alt=""> Интернет-банк</a></li>
                            <li><a href="#"><img src="file/img/icon1.png" alt=""> Электронный кошелёк</a></li>
                            <li><a href="#"><img src="file/img/icon5.png" alt=""> Баланс телефона</a></li>

                        </ul>

                    </div>

                </div>



            </div>

        </div>

        </div>

    </div>

</div>

<script>
    var linkNav = document.querySelectorAll('[href^="#nav"]'),
        V = 1.5;  // скорость, может иметь дробное значение через точку
    for (var i = 0; i < linkNav.length; i++) {
        linkNav[i].addEventListener('click', function(e) {
            e.preventDefault();
            var w = window.pageYOffset,  // прокрутка
                hash = this.href.replace(/[^#]*(.*)/, '$1');  // id элемента, к которому нужно перейти
            t = document.querySelector(hash).getBoundingClientRect().top,  // отступ от окна браузера до id
                start = null;
            requestAnimationFrame(step);  // подробнее про функцию анимации [developer.mozilla.org]
            function step(time) {
                if (start === null) start = time;
                var progress = time - start,
                    r = (t < 0 ? Math.max(w - progress/V, w + t) : Math.min(w + progress/V, w + t));
                window.scrollTo(0,r);
                if (r != w + t) {
                    requestAnimationFrame(step)
                } else {
                    location.hash = hash  // URL с хэшем
                }
            }
        }, false);
    }
</script>

</body>

</html>
