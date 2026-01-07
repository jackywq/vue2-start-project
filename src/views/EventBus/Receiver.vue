<template>
  <div class="receiver">
    <h3>Receiver Component</h3>
    <div class="content">
      <p v-if="receivedMessage" class="message">
        Received:
        <span class="highlight">{{ receivedMessage }}</span>
      </p>
      <p v-else class="waiting">Waiting for message...</p>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import { EventBus } from '@/utils/eventBus'

@Component
class Receiver extends Vue {
  receivedMessage = ''

  mounted() {
    EventBus.$on('message-sent', this.handleMessage)
  }

  beforeDestroy() {
    EventBus.$off('message-sent', this.handleMessage)
  }

  private handleMessage(msg: string) {
    this.receivedMessage = msg
  }
}
export default Receiver
</script>

<style scoped lang="less">
.receiver {
  border: 1px solid #ccc;
  padding: 20px;
  margin: 10px;
  border-radius: 4px;

  .content {
    margin-top: 10px;
  }

  .message {
    font-size: 16px;
    font-weight: bold;
  }

  .highlight {
    color: #1890ff;
  }

  .waiting {
    color: #999;
    font-style: italic;
  }
}
</style>
