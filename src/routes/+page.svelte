<div class="container">
    <div class="info">
        <div class="animate-background">
            <div class="container info-container">
                <div class="info-text">
                    <div class="text-wrapper">
                        <h1>
                            <p class="animate-text-1">Добро пожаловать,</p>
                            <p class="text-2">Меня зовут Данил, я начинающий Web-разработчик.</p>
                        </h1>
                    </div>
                </div>
                <h2 class="subtitle">
                    Lorem ipsum dolor sit amet consectetur, adipisicing elit. Accusamus consequuntur pariatur quisquam, laborum amet illo iusto nesciunt odit quibusdam quaerat, sapiente repudiandae ipsa nobis iure!
                </h2>
                <div style="color:black" class="scroll-button animate-scroll" tabindex="0">
                    <a href="/about">Больше обо мне &#10145;</a>
                </div>
            </div>
        </div>
    </div>
</div>

<div class="background-div"></div>

<style>
    .info {
        text-align: center;
        position: relative;
    }

    .info-container {
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        text-align: left;
        align-items: start;
    }

    .container {
        max-width: 1400px;
        margin: 190px 0 0 2.5rem;
    }

    .info h1 {
        font-size: 4rem;
        margin: 0;
    }

    .info h1 p {
        position: relative;
        font: inherit;
        margin: 0;
        text-align: left;
        line-height: 130%;
        width: fit-content;
        font-weight: 800;
        letter-spacing: -0.03em;
    }

    .info h2 {
        max-width: 65ch;
        font-weight: 200;
        margin-top: 0.50rem;
    }

    .background-div {
        background-color: #ecebe8;
        width: 100%;
        height: 56vh;
        margin: -235px auto;
    }

    .info .info-text {
        position: relative;
    }

    .text-2 {
        position: relative;
        z-index: 1;
        margin-top: -50px; /* Отрицательный отступ сверху для перемещения текста над .background-div */
    }
</style>
