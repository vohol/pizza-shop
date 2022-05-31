<template>
  <nav class="nav nav__header">
    <ul
    :class="{'nav__list--mobile': mobile}"
    class="nav__list">
      <li v-for="item in menu" :key="item.id" class="nav__item">
        <a class="nav__link" :href="item.link">{{item.name}}</a>
      </li>
    </ul>
    <div 
    @click="toggleMobileMenu()"
    class="material-symbols-outlined nav__menu">
    menu
    </div>
  </nav>
</template>

<script>
export default {
  name: "navList",
  data() {
    return {
     menu : [
        {
     link: '#',
       id: 1,
     name: 'payment'
   },
   {
     link: '#',
       id: 2,
     name: 'about us'
   },
   {
     link: '#',
       id: 3,
     name: 'contacts'
   }
  ],
  mobile: false,
  } 
 },
 methods: {
   toggleMobileMenu() {
     this.mobile = !this.mobile;
   }
 }
}
</script>

<style lang="scss">
.nav {

  &__menu {
    cursor: pointer;
    padding: 10px;
  }

  &__list {
    display: flex;
    flex-direction: column;
    align-items: center;
    position: fixed;
    top: 74px;
    left: 0;
    right: 0;
    transform: scaleY(0);
    transform-origin: top;
    transition: transform 0.2s ease-in;
    border-bottom: 1px solid rgba(#000000, .6);
    
    &--mobile {
      transform: scaleY(1);
    }
  }

  &__item {
    display: flex;
    border-top: 1px solid rgba(#000000, .6);
    width: 100%;
  }

  &__link {
    font-weight: 400;
    font-size: 18px;
    line-height: 1.25;
    color: #000000;
    text-transform: capitalize;
    padding: 10px;
    display: block;
    width: 100%;
    text-align: center;
    transition: all 0.3s ease;
  }

  &__item:hover &__link {
    text-shadow: 0 0 .01px black, 0 0 .01px black, 0 0 .01px black;
  }
}

@media screen and (min-width: 1000px) {
  .nav {
    display: flex;
    align-items: center;
    
    &__menu {
      display: none;
  }

  &__list {
    transform: scaleY(1);
    position: static;
    flex-direction: row;
    align-items: center;
    gap: 40px;
    border-bottom: unset;
  }

  &__item {
    border-top: unset;
    width: auto;
  }

  &__link {
    font-size: 16px;
    line-height: 1.25px;
  }
}

  
}
</style>