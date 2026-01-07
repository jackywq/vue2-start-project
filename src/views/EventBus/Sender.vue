<template>
  <div class="sender">
    <h3>Sender Component</h3>
    <div class="input-group">
      <a-input
        v-model="message"
        placeholder="Type a message"
        style="width: 200px; margin-right: 10px"
      />
      <a-button type="primary" @click="sendMessage">Send Message</a-button>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import { EventBus } from '@/utils/eventBus'

@Component
class Sender extends Vue {
  message = ''

  sendMessage() {
    if (this.message) {
      EventBus.$emit('message-sent', this.message)
      this.$message.success('Message sent via EventBus!')
      this.message = ''
    } else {
      this.$message.warning('Please type a message first.')
    }
  }
}
export default Sender
</script>

<style scoped lang="less">
.sender {
  border: 1px solid #ccc;
  padding: 20px;
  margin: 10px;
  border-radius: 4px;

  .input-group {
    display: flex;
    align-items: center;
    justify-content: center;
  }
}
</style>
