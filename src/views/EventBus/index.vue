<template>
  <div class="event-bus-demo">
    <h2>EventBus Communication Demo</h2>
    <p class="description">
      This example demonstrates communication between two sibling components
      using a global EventBus.
    </p>
    <div class="components-container">
      <Sender />
      <Receiver />
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import Sender from './Sender.vue'
import Receiver from './Receiver.vue'

@Component({
  components: {
    Sender,
    Receiver,
  },
})
class EventBusDemo extends Vue {}
export default EventBusDemo
</script>

<style scoped lang="less">
.event-bus-demo {
  padding: 20px;
  text-align: center;

  .description {
    margin-bottom: 20px;
    color: #666;
  }

  .components-container {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 20px;
  }
}
</style>
