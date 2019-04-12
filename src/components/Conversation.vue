<template>
  <div class="conversation container">
    <div v-for="m of conversation.messages" v-bind:key="m.key">
        <Message v-bind:message="m" />
    </div>

  </div>

</template>

<script>
import Message from "./Message.vue";
export default {
  name: 'Conversation',
  components: {
      Message,
  },
  props: {
      conversation: Object
  }
}
</script>

<style scoped>
p {
  font-size: 11pt;
}
</style>
