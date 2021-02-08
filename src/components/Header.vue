<template>
    <header class="header">
        <div class="header__container">
            <div class="header__logo">
                <img src="./../assets/img/Frame.svg" class="logo" alt="Logo">
                <span class="header__title">Услуги и сервисы Пермского края</span>
            </div>
            <div class="header__interface">
                <img class="header__profile-icon" src="./../assets/img/User.svg"  alt="Profile Icon">
                <span class="header__name" href="#" >Константинопольский К.К</span>
                <span class="header__exit" href="#" >Выйти</span>
            </div>
        </div>
  </header>
</template>

<script>
export default {

}
</script>

<style lang="scss">
.header {
    color: $white;
    margin: 0 auto;
    background: $light-blue;
    max-width: 100%;
}
.header__container {
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
    max-width: $whole-content-width;
    @media(max-width: 576px) {
        max-width: $whole-content-width-mobile;
    }
    padding: .7rem 0 .7rem 0;
}
.header__logo {
    display: flex;
    justify-content: center;
    align-items: center;
}
.logo {
    max-width: 1.9rem;
}
.header__title {
    margin-left: 1.2rem;
    font-weight: bold;
}
.header__interface {
    display: flex;
    justify-content: center;
    align-items: center;
}
.header__profile-icon {
    margin-right: 0.5rem;
    max-width: 1.1rem;
}
.header__exit {
    margin-left: 1rem;
}
</style>