<template>
  <div id="app">
    <ChatScreen />
    <ChatInput />
  </div>
</template>

<script>
import ChatScreen from './components/ChatScreen.vue';
import ChatInput from './components/ChatInput.vue';

export default {
  name: 'App',
  components: {
    ChatScreen,
    ChatInput
  }
}
</script>
