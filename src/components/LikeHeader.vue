<template>
  <div>
    <slot></slot>
  </div>
</template>

<script>

export default {
  data() {
    return {
      user: {
        firstName: 'ドナルド',
        lastName: 'トランプ',
      }
    }
  },
}
</script>
