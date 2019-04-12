<template>
  <div class="message">
    <p>
        <span class="timestamp">{{ timestamp | dateFormat('MM/D/YY h:mm:ss a') }}</span>
        <span class="sender">
            {{ sender }}:
        </span>
        <span class="contents" v-html="contents"></span>
    </p>
  </div>

</template>

<script>
import Vue from "vue";
import VueFilterDateFormat from "vue-filter-date-format";
Vue.use(VueFilterDateFormat);

export default {
  name: 'Message',
  props: {
      message: Object
  },
  data() {
      return {
          timestamp: null,
          sender: null,
          contents: null,
      }
  },
  created() {
      this.timestamp = this.message.timestamp;
      this.sender = this.message.sender;
      this.contents = this.message.contents;
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
