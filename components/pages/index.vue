<template>
  <meta name="viewport" content="width=device-width,initial-scale=1.0" />
  <div class="">
    <div :class="['tab', { active: isActive }]">
      <div class="menuToggle" @click="onClick()"><span>+</span></div>

      <div class="circuLarbg1"></div>
      <div class="circuLarbg2"></div>

      <div class="circuLar">
        <ul class="circle">
          <li v-for="item in itemsCircle">
            <a href="#"></a><ion-icon :name="item"></ion-icon>
          </li>
        </ul>
      </div>

      <ul class="menu">
        <li v-for="{ icon } in iconList">
          <a href="#"><ion-icon :name="icon"></ion-icon></a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup lang="ts">
import 'assets/scss/main.scss'

const isActive = ref<boolean>(false)

const iconList = [
  { icon: 'home' },
  { icon: 'person' },
  { icon: '' },
  { icon: 'chatbubble' },
  { icon: 'settings' }
]

const itemsCircle = ['camera-outline', 'qr-code-outline', 'videocam-outline']

function onClick() {
  isActive.value = !isActive.value
}
</script>

<style lang="scss">
.tab {
  position: relative;
  width: 400px;
  height: 80px;
  z-index: 1;
  user-select: none;
  .circuLar,
  .circuLarbg1,
  .circuLarbg2 {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    width: 160px;
    height: 80px;
    background: #fff;
    border-bottom-left-radius: 80px;
    border-bottom-right-radius: 80px;
    transform-origin: top center;
    transition: 1s ease-in-out;
  }
  .circuLarbg1 {
    background: #8bc34a;
    transition: 0.6s ease-in-out;
    transition-delay: 0.4s;
  }
  .circuLarbg2 {
    background: #ffeb3b;
    transition: 0.8s ease-in-out;
    transition-delay: 0.2s;
  }
  &.active {
    .circuLar,
    .circuLarbg1,
    .circuLarbg2 {
      transform: translateX(-50%) rotate(180deg);
    }
    .circuLarbg1,
    .circuLarbg2 {
      transition-delay: 0s;
    }
    .menuToggle {
      transform: translateX(-50%) rotate(225deg);
    }
  }
  .menuToggle {
    position: absolute;
    top: -30px;
    transform: translateX(-50%);
    left: 50%;
    width: 60px;
    height: 60px;
    background: #ff3b7e;
    z-index: 1;
    border-radius: 50%;
    cursor: pointer;
    color: #fff;
    font-size: 2.5em;
    font-weight: 600;
    transition: 1s ease-in-out;
    display: flex;
    justify-content: center;
    align-items: center;
    span {
      position: relative;
      top: -3px;
    }
  }
  ul {
    &.circle {
      position: absolute;
      display: flex;
      justify-content: center;
      align-items: center;
      inset: 0;
      li {
        list-style: none;
        display: flex;
        position: absolute;
        cursor: pointer;
        @each $i in 1, 2, 3 {
          &:nth-child(#{$i}) {
            @if $i == 1 {
              transform: translate(50px, -15px);
            } @else if $i == 2 {
              transform: translate(0px, 15px);
            } @else {
              transform: translate(-50px, -15px);
            }
          }
        }
        &:hover {
          ion-icon {
            color: #ff3b7e;
          }
        }
        ion-icon {
          transform: rotate(180deg);
          font-size: 1.25em;
          color: #bbb;
          pointer-events: none;
        }
      }
    }
    &.menu {
      position: absolute;
      inset: 0;
      background: #fff;
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 55px;
      box-shadow: 0 -15px 25px rgba(0, 0, 0, 0.1);
      li {
        list-style: none;
        &:hover {
          ion-icon {
            color: #2196f3;
          }
        }
        ion-icon {
          font-size: 1.5em;
          color: #bbb;
          pointer-events: none;
        }
      }
    }
  }
}
</style>
