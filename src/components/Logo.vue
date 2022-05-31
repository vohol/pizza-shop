<template>
<a class="logo header__logo" href="#">
  <img class="logo__icon icon" src="../assets/images/logo1.svg" alt="">
</a>  
</template>

<script>
export default {
  name: "logo-comp"
}
</script>

<style lang="scss">

.logo {
  display: block;
  width: calc(112px * 0.6);
  height: calc(67px * 0.6);
  
  &__icon {
    width: 100%;
    height: 100%;
  }
}

@media screen and (min-width: 1000px){
.logo {
  width: 112px;
  height: 67px;
}
  
}
</style>