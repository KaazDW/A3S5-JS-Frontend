<script setup>
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'

import { ref } from 'vue'

const count = ref(0)
const incrementCounter = () => {
  count.value++
}
</script>

<template>
  <WelcomeItem>
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading>1. Incrementation</template>

    <div class="incr">
      <p>Counter: <span>{{ count }}</span> > </p>
      <button @click="incrementCounter"> +1</button>
    </div>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading>2. TodoList</template>
    <div class="todo">

    </div>
  </WelcomeItem>
</template>
<style scoped lang="scss">
// 1.Increment
  .incr{
    display: flex;
    margin-top: 15px;
    text-align: center;
    align-items: center;
  }
  .incr button{
    padding: 8px 15px;
    margin-left: 10px;
  }
  .incr span{
    border: 1px solid lightgrey;
    padding: 5px 10px;
    border-radius: 5px;
    margin: 0 5px;
  }
</style>
