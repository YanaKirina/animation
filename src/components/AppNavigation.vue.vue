<template>
    <section>
        <p>Почему именно ERP</p>
        <p>Программы</p>
        <p>Проектное внедрение</p>
        <p>Кейсы</p>
        <p>Ваша выгода</p>
        <p>Вопросы</p>
        <p>Статусы</p>
        <div class="menu-item" @click="toggleDropdown">
            <p :class="{ active: isDropdownOpen }">Услуги</p>
            <div class="dropdown" v-show="isDropdownOpen">
                <a href="#">Переход с «1С:УПП» на современные системы «1С»</a>
                <a href="#">Переход со сторонних систем</a>
                <a href="#">Внедрение систем класса ERP</a>
                <a href="#">Внедрение отраслевых решений ERP</a>
                <a href="#">Постпроектное сопровождение</a>
                <a href="#">Создание системной архитектуры</a>
                <a href="#">Анализ производительности</a>
            </div>
        </div>
        <button>Попробовать бесплатно</button>
    </section>
</template>

<script>
export default {
    data() {
        return {
            isDropdownOpen: false
        };
    },
    methods: {
        toggleDropdown() {
            this.isDropdownOpen = !this.isDropdownOpen;
        }
    }
};
</script>

<style scoped>
section {
    background: linear-gradient(137.41deg, #EFF7FF 0.5%, #6ED5EE 59.79%), linear-gradient(322.4deg, #4C0091 11.93%, #00FFE1 95.31%);
    box-shadow: 24.799px 28.528px 75.6px rgba(20, 24, 42, 0.233);
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 16px 15vw;
    position: relative;
}

button {
    background: linear-gradient(137.41deg, #0F6FD4 0.5%, #011438 59.79%), linear-gradient(0deg, #011438, #011438), linear-gradient(137.41deg, #EFF7FF 0.5%, #6ED5EE 59.79%), linear-gradient(137.41deg, #EFF7FF 0.5%, #81C6FF 59.79%), linear-gradient(322.4deg, #4C0091 11.93%, #00FFE1 95.31%);
    box-shadow: 24.799px 28.528px 75.6px rgba(20, 24, 42, 0.233);
    border-radius: 5px;
    padding: 12px;
    color: #FFFFFF;
    font-size: 16px;
    font-weight: 700;
}

p {
    border-bottom: 2px solid rgba(255, 255, 255, 0.64);
    font-size: 18px;
    color: #021B44;
    cursor: pointer;
}

p:hover {
    background: rgba(255, 255, 255, 0.64);
    box-shadow: 0px 0px 4.8px #FFFFFF;
    border-radius: 2px;
}

p.active {
    background: rgba(255, 255, 255, 0.64);
    box-shadow: 0px 0px 4.8px #FFFFFF;
    border-radius: 2px;
}

.menu-item {
    cursor: pointer;
}

.dropdown {
    position: absolute;
    top: 100%;
    left: 60%;
    background: linear-gradient(-2.77deg, rgba(239, 247, 255, 0.56) 22.69%, rgba(136, 216, 243, 0.56) 97.73%), #D9D9D9;
    border-radius: 0px 0px 5px 5px;
    padding: 16px 76px;
    z-index: 10;
}

.dropdown a {
    display: block;
    color: #021B44;
    padding: 6px 0;
}

.dropdown a:hover {
    text-decoration: underline;
}
</style>