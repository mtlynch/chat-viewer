<template>
  <div class="log-viewer">
    <div v-if="conversations.length > 0">
      <select class="select-option" required v-model="selectedConversation">
        <option class="option" v-for="conversation in conversations" v-bind:value="conversation" v-bind:key="conversation.key">
          {{ conversation.remoteUsername }} - {{ conversation.messages.length }} messages
        </option>
      </select>

      <div v-if="selectedConversation">
        <div v-for="m of selectedConversation.messages" v-bind:key="m">
          <p>
            <span class="timestamp">{{ m.timestamp }}</span>
            <span class="sender">
              {{ m.sender }}:
            </span>
            <span class="contents" v-html="m.contents"></span>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'LogViewer',
  data() {
    return {
      conversations: [],
      selectedConversation: null,
      backendError: null
    };
  },
  created() {
    this.$http
      .get('/logs.json')
      .then(result => {
        this.conversations = [];
        for (const[conversationIndex, c] of result.data.entries()) {
          const messages = [];
          for (const [i, m] of c.messages.entries()) {
            messages.push({
              key: i,
              timestamp: new Date(m.timestamp),
              sender: m.sender,
              contents: m.contents,
            });
          }
          messages.sort((a, b) => a.timestamp - b.timestamp);
          this.conversations.push({
            key: `${c.remoteUsername}-${conversationIndex}`,
            messages: messages,
            remoteUsername: c.remoteUsername,
            localUsername: c.localUsername,
          });
        }
      });
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
</style>
