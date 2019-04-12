<template>
  <div class="conversation container">
    <div v-for="m of conversation.messages" v-bind:key="m.key">
        <p>
        <span class="timestamp">{{ m.timestamp }}</span>
        <span class="sender">
            {{ m.sender }}:
        </span>
        <span class="contents" v-html="m.contents"></span>
        </p>
    </div>

  </div>

</template>

<script>
export default {
  name: 'Conversation',
  props: {
      conversation: Object
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
