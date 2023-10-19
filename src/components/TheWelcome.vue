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

  const tasks = ref([
    { text: 'Exemple de tâche', completed: false }
  ]);
  const newTask = ref('');

  const addTask = () => {
    if (newTask.value !== '') {
      tasks.value.push({ text: newTask.value, completed: false });
      newTask.value = '';
    }
  };

  const removeTask = (index) => {
    tasks.value.splice(index, 1);
  };
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
      <ul>
        <li v-for="(task, index) in tasks" :key="index">
          <button @click="removeTask(index)">Supprimer</button>
          <input type="checkbox" v-model="task.completed" />
          {{ task.text }}
        </li>
      </ul>
      <input v-model="newTask" placeholder="Ajouter une nouvelle tâche" />
      <button @click="addTask">Ajouter</button>

    </div>
  </WelcomeItem>
</template>
<style scoped lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');
*{
  font-family: 'Poppins', sans-serif;
}
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

//  2.Todo
  .todo{
    ul{
      list-style: none;
      padding: 0;
      li{
        margin: 5px 0;
        button{
          padding: 3px 5px;
          margin-right: 10px;
        }
        input{
          margin: 0 2px;
        }
      }
    }
    input{
      padding: 5px;
      border-radius: 5px;
    }
    button{
      padding: 5px;
      margin: 0 5px;
    }
  }
</style>
