<template>
  <div class="navigation-bar">
    <!-- nav popup type -->
    <!-- <div class="navigation-button">
      <base-button type="home" @click="handlehome"
        ><span>home</span></base-button
      >
    </div>
    <div class="navigation-button">
      <base-button type="shots" @click="handlePopupShots">
        <span>shots</span>
      </base-button>
    </div>
    <div class="navigation-button navigation-button--update">
      <base-button type="plus" @click="handlePopupUpload">
        <span class="a11y">upload</span></base-button
      >
    </div>
    <div class="navigation-button">
      <base-button type="subscriptions" @click="handleSubscriptions"
        ><span>subscriptions</span></base-button
      >
    </div>
    <div class="navigation-button">
      <base-button type="library" @click="handleLibrary"
        ><span>library</span></base-button
      >
    </div> -->
    <div class="navigation-button">
      <router-link to="/">
        <base-button type="home"> 
          <span>home</span>
        </base-button>
      </router-link>
    </div>
    <div class="navigation-button">
      <router-link to="/home">
        <base-button type="shots"> 
          <span>shots</span>
        </base-button>
      </router-link>
    </div>
    <div class="navigation-button navigation-button--update">
      <router-link to="/Update">
        <base-button type="plus"></base-button>
      </router-link>
    </div>
    <div class="navigation-button">
      <router-link to="/Subscriptions">
        <base-button type="subscriptions">
          <span>subscriptions</span>  
        </base-button>
      </router-link>
    </div>
    <div class="navigation-button">      
      <base-button type="library" @click="goLibrary">
        <span>library</span>  
      </base-button>      
    </div>
  </div>
  <!-- nav popup type -->
  <!-- <componentPopup
    type="full"
    v-if="popupupload"
    @closePopup="popupupload = false"
    >popupupload</componentPopup
  >
  <componentPopup
    type="bottomLayer"
    v-if="Subscriptions"
    @closePopup="Subscriptions = false"
    >test2</componentPopup
  >
  <componentPopup
    type="full"
    v-if="Library"
    @closePopup="Library = false"
  >
    <div class="profile">
      <div class="icon-user"></div>
      <div class="user">
        <p class="user-name">Username</p>
        <p class="user-id">@user</p>
        <p class="user-subscribers">12,345 subscribers</p>
      </div>
    </div>
    <div class="library">
      <p class="user-library">최근 시청한 목록</p>
      <div class="library-list">
        <libraryList
          v-for="video in VideoData"
          :key="video.id"
          :video="video"
        />
      </div>
    </div>
  </componentPopup> -->
</template>

<script setup>
import BaseButton from '@/layouts/components/BaseButton.vue'
import componentPopup from '@/layouts/components/componentPopup.vue'
import { ref, defineEmits } from 'vue'

// pinia 
import { storeToRefs } from 'pinia'
import { useUserStore } from "@/stores/user"
import { router } from '../../router'
const userStore = useUserStore()
const userName = ref(userStore.userName)

// nav popup type
// const home = ref(false)
// const popupShots = ref(false)
// const popupupload = ref(false)
// const Subscriptions = ref(false)
// const Library = ref(false)

// const handlehome = () => {
//   home.value = true
// }

// const handlePopupShots = () => {
//   popupShots.value = true
// }

// const handlePopupUpload = () => {
//   popupupload.value = true
// }

// const handleSubscriptions = () => {
//   Subscriptions.value = true
// }

// const handleLibrary = () => {
//   Library.value = true
// }
const goLibrary = () => {
  if(userStore.isLoggedIn) {
    router.push('/Library')
  } else {
    router.push('/Signup')
  } 
}
</script>

<style lang="scss">
.base-button--shots:before {
  /* 숏츠 버튼 */
  display: block;
  content: '';
  clear: both;
  margin: 0 auto;
  width: 30px;
  height: 26px;
  background: url(@/assets/icon/shots.svg) center / contain no-repeat;
  vertical-align: middle;
  /* padding: 14px; */
}
.base-button--plus:before {
  /* 더보기 버튼 */
  display: block;
  content: '';
  clear: both;
  margin: 0 auto;
  width: 42px;
  height: 42px;
  background: url(@/assets/icon/plus.svg) center / contain no-repeat;
  vertical-align: middle;
  /* padding: 29px; */
}
.base-button--subscriptions:before {
  /* 구독 버튼 */
  display: block;
  content: '';
  clear: both;
  margin: 0 auto;
  width: 28px;
  height: 28px;
  background: url(@/assets/icon/subscriptions.svg) center / contain no-repeat;
  vertical-align: middle;
}
.base-button--library:before {
  /* 라이브러리 버튼 */
  display: block;
  content: '';
  clear: both;
  margin: 0 auto;
  width: 28px;
  height: 28px;

  background: url(@/assets/icon/library.svg) center / contain no-repeat;
  vertical-align: middle;
}
</style>
