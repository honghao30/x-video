<template>
  <button
    :class="`base-button base-button--${props.type} ${
      props.isActive ? 'active' : ''
    }`"
    @click="toggle"
  >
    <slot></slot>
  </button>
</template>

<script setup>
import { ref, defineProps, defineEmits } from 'vue'
const props = defineProps(['type', 'isActive', 'disabled'])
const emit = defineEmits()

const toggle = () => {
  console.log('Button clicked')
  emit('toggle', !props.active)
  console.log('!props.active::', !props.active)
}
</script>

<style scoped>
.base-button {
  /* 기본 버튼 스타일 */
  padding: 16px;
  cursor: pointer;
  border: 0;
  width: 100%;
}

.base-button--like {
  /* 좋아요 버튼 */
  background: url(@/assets/icon/like-bf.svg) center / contain no-repeat;
  vertical-align: middle;
}

.base-button--like.active {
  /* 좋아요 버튼 활성 상태 */
  background: url(@/assets/icon/like-af.svg) center / contain no-repeat;
  vertical-align: middle;
}

.base-button--comments {
  /* 댓글 버튼 */
  background: url(@/assets/icon/comments.svg) center / contain no-repeat;
  vertical-align: middle;
}

.base-button--share {
  /* 공유 버튼 */
  background: url(@/assets/icon/share.svg) center / contain no-repeat;
  vertical-align: middle;
}

/* 네비게이션 */
.base-button--home:before {
  /* 홈 버튼 */
  display: block;
  content: '';
  clear: both;
  margin: 0 auto;
  width: 24px;
  height: 24px;
  background: url(@/assets/icon/home.svg) center / contain no-repeat;
  vertical-align: middle;
  /* padding: 14px; */
}
</style>
