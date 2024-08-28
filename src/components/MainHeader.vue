<template>
    <header class="header">
        <div class="header-logo">
            <img src="../assets/logo.png" alt="" />
        </div>

        <ul class="header-list">
            <li class="header-list-item">
                <router-link class="link" to="/">Форма</router-link>
            </li>
            <li class="header-list-item">
                <router-link class="link" to="/preview">Превью</router-link>
            </li>
        </ul>
    </header>
</template>

<script setup></script>

<style scoped>
li {
    list-style: none;
}

.header {
    display: flex;
    gap: 670px;

    /* BottomLine */
    border-bottom: 1px;
    box-shadow: 0px 1px 0px 0px rgba(17, 17, 17, 0.1);
}

.header-logo {
    padding-top: 24px;
    padding-bottom: 24px;
    padding-left: 92px;
}

.header-list {
    display: flex;
    gap: 24px;

    color: rgba(17, 17, 17, 0.48);

    font-size: 14px;
    font-weight: 400;
    line-height: 24px;
    letter-spacing: 0px;
    cursor: pointer;
}

.link {
    text-decoration: none;
}
</style>
