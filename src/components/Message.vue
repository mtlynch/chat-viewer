<template>
  <div class="message">
    <p>
        <span class="timestamp">{{ message.timestamp }}</span>
        <span class="sender">
            {{ message.sender }}:
        </span>
        <span class="contents" v-html="message.contents"></span>
    </p>

  </div>

</template>

<script>
export default {
  name: 'Message',
  props: {
      message: Object
  }
}
</script>

<style scoped>
p {
  font-size: 11pt;
}

.timestamp {
  width: 50px;
}

.sender {
  font-weight: bold;
}
</style>
