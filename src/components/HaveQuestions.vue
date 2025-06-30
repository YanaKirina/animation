<template>
    <section class="gradient-section">
        <div class="questions">
            <h3>Есть вопросы?</h3>
            <p>Закажите обратный звонок от экспертов ГЭНДАЛЬФ – мы поможем найти оптимальное решение.</p>
            <div class="rounded-button-background">
                <button>Заказать обратный звонок</button>
            </div>
        </div>
    </section>
</template>

<script>

</script>

<style scoped>
.gradient-section {
    position: relative;
    width: 100%;
    height: 738px;
    background-image: url('@/assets/questions-back.png');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    overflow: hidden;
    display: flex;
    align-items: center;
}

.gradient-section::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 30%;
    background: linear-gradient(0.00deg, rgba(0, 114, 140, 0), rgba(0, 114, 140, 0.3) 29.555%, rgba(0, 114, 140, 0.8) 59.775%, rgb(0, 114, 140) 94.023%)
}

.questions {
    box-shadow: 0px 0px 20.4px -2px rgba(255, 255, 255, 0.72);
    background: linear-gradient(150.95deg, rgba(239, 247, 255, 0.9) 30.481%, rgba(29, 181, 218, 0.9) 86.976%
86.976%
);
    border-radius: 5px;
    padding: 56px;
    width: 45%;
}

h3{
    color: #021B44;
}

p{
    font-size: 20px;
    color: #021B44;
    padding: 15px 0;
}

button{
    font-weight: 700;
    padding: 16px 24px;
    background: linear-gradient(137.41deg, #0F6FD4 0.5%, #011438 59.79%), linear-gradient(322.4deg, #4C0091 11.93%, #00FFE1 95.31%);
    box-shadow: 24.799px 28.528px 75.6px rgba(20, 24, 42, 0.233);
    border-radius: 5px;
    color: #FFFFFF;
}


.rounded-button-background{
    box-sizing: border-box;
    background: linear-gradient(137.41deg, rgba(255, 255, 255, 0.56) 0.5%, rgba(177, 220, 255, 0.56) 59.79%);
    border: 1px solid rgba(255, 255, 255, 0.92);
    box-shadow: 0px 0px 24px 10px #C0DEFF;
    border-radius: 15px;
    padding: 9 px;
    width: fit-content
}

</style>
