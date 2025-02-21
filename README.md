<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Luxus Hub - Лудшчий сайт для Geode модов</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            width: 100%;
            height: 100vh;
            background-color: rgb(255, 255, 255); /* Белый фон */
            font-family: Arial, sans-serif;
            color: rgb(10, 12, 102); /* Черный текст */
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            align-items: center;
            position: relative; /* Позиционирование для шариков */
            overflow: hidden; /* Скрытие шариков вне экрана */
        }

        .intro-text {
            font-size: 4em;
            text-align: center;
            opacity: 0; /* Изначально текст невидим */
            animation: fadeInUp 2s forwards; /* Анимация появления текста */
            margin-top: 50px; /* Отступ сверху для центрирования текста */
            position: relative; /* Позиционирование для стрелок */
        }

        .arrow-left,
        .arrow-right {
            position: absolute;
            top: 50%;
            font-size: 3em;
            color: green; /* Зеленый цвет стрелок */
            opacity: 0; /* Изначально стрелки невидимы */
            animation: fadeInUp 2s 1s forwards; /* Анимация появления стрелок с задержкой */
        }

        .arrow-left {
            left: -60px; /* Положение слева от текста */
            transform: rotate(180deg); /* Поворот стрелки влево */
        }

        .arrow-right {
            right: -60px; /* Положение справа от текста */
        }

        .buttons {
            display: flex;
            justify-content: center;
            gap: 20px; /* Расстояние между кнопками */
            opacity: 0; /* Изначально кнопки невидимы */
            animation: fadeInUp 2s 1s forwards; /* Анимация появления кнопок с задержкой */
        }

        button {
            padding: 10px 20px;
            background-color: #008000; /* Зеленый цвет кнопок */
            color: white; /* Белый текст на кнопках */
            border: none;
            cursor: pointer;
            border-radius: 10px; /* Плавные углы */
            transition: background-color 0.3s ease; /* Переход цвета при наведении */
        }

        button:hover {
            background-color: #7bff7b; /* Светло-зеленый цвет при наведении */
        }

        .waves-container {
            position: relative;
            width: 100%;
            height: 250px; /* Высота контейнера волн */
            overflow: hidden;
        }

        .wave {
            position: absolute;
            bottom: 0;
            width: 100%;
            height: 120px; /* Высота волны */
            background-size: 1000px 120px; /* Размер фона */
            background-repeat: repeat-x;
            background-position: 0 0;
            animation-duration: 7s;
            animation-timing-function: linear;
            animation-iteration-count: infinite;
        }

        .wave.wave1 {
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 500 60'%3E%3Cpath fill='%231a2135' d='M0,26.11 C111.73,22.78 223.47,19.44 335.21,16.09 L500,34.59 L500,60 L0,60 Z' /%3E%3C/svg%3E");
            animation-name: move-wave1;
            z-index: 3; /* Верхний слой */
            opacity: 0.9; /* Немного прозрачный для эффекта размытости */
        }

        .wave.wave2 {
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 500 60'%3E%3Cpath fill='%232c304b' d='M0,29.55 C111.73,27.07 223.47,24.58 335.21,22.1 L500,31.17 L500,60 L0,60 Z' /%3E%3C/svg%3E");
            animation-name: move-wave2;
            z-index: 2; /* Средний слой */
            opacity: 0.8; /* Прозрачность для размытости */
        }

        .wave.wave3 {
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 500 60'%3E%3Cpath fill='%23383d62' d='M0,33 C111.73,31.37 223.47,29.74 335.21,28.11 L500,27.76 L500,60 L0,60 Z' /%3E%3C/svg%3E");
            animation-name: move-wave3;
            z-index: 1; /* Нижний слой */
            opacity: 0.7; /* Прозрачность для размытости */
        }

        /* Шарик */
        .bubble {
            position: absolute;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background-color: rgba(46, 19, 107, 0.3); /* Темно-Синий цвет */
            animation: fall 5s linear infinite; /* Анимация падения */
            z-index: -1; /* За всеми объектами */
        }

        /* Генерация случайных шариков */
        .bubble:nth-child(1) {
            left: 10%;
            animation-delay: 0s;
        }

        .bubble:nth-child(2) {
            left: 20%;
            animation-delay: 1s;
        }

        .bubble:nth-child(3) {
            left: 30%;
            animation-delay: 2s;
        }

        .bubble:nth-child(4) {
            left: 40%;
            animation-delay: 3s;
        }

        .bubble:nth-child(5) {
            left: 50%;
            animation-delay: 4s;
        }

        .bubble:nth-child(6) {
            left: 60%;
            animation-delay: 5s;
        }

        .bubble:nth-child(7) {
            left: 70%;
            animation-delay: 6s;
        }

        .bubble:nth-child(8) {
            left: 80%;
            animation-delay: 7s;
        }

        .bubble:nth-child(9) {
            left: 90%;
            animation-delay: 8s;
        }

        @keyframes fall {
            0% {
                top: -20px; /* Начинают падение сверху */
            }
            100% {
                top: 100vh; /* Заканчивают падение внизу */
            }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(50px); /* Начальная позиция выше центра */
            }
            to {
                opacity: 1;
                transform: translateY(0); /* Конечная позиция */
            }
        }

        @keyframes move-wave1 {
            from {background-position: 0 0;}
            to {background-position: 1000px 0;}
        }

        @keyframes move-wave2 {
            from {background-position: 0 0;}
            to {background-position: -1000px 0;}
        }

        @keyframes move-wave3 {
            from {background-position: 0 0;}
            to {background-position: 600px 0;}
        }
    </style>
</head>
<body>
    <h1 class="intro-text">Luxus Hub</h1>
    <i class="arrow-left"> </i><!-- Стрелка слева -->
    <i class="arrow-right"> </i><!-- Стрелка справа -->
    <div class="buttons">
        <button onclick="window.location.href = 'https://example.com/page1';">Кнопка 1</button>
        <button onclick="window.location.href = 'https://example.com/page2';">Кнопка 2</button>
    </div>
    <div class="waves-container">
        <div class="wave wave1"></div> <!-- Верхний слой -->
        <div class="wave wave2"></div> <!-- Средний слой -->
        <div class="wave wave3"></div> <!-- Нижний слой -->
    </div>
    
    <!-- Шарики -->
    <span class="bubble"></span>
    <span class="bubble"></span>
    <span class="bubble"></span>
    <span
