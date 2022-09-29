<template>
  <q-page padding>
    <div class="row q-mb-lg">
      <q-input class="col" v-model="text" placeholder="Add New Task" @keyup.enter="addTask"></q-input>
      <q-btn color="primary" size="sm" label="Add" @click="addTask"></q-btn>
    </div>
    <div class="row q-mb-lg">
      <q-list highlight bordered class="col" padding>
        <q-item-label header>Tasks</q-item-label>
        <q-item clickable v-ripple v-for="(task, index) in tasks" :key="task">
          <q-item-section>{{task}}</q-item-section>
          <q-item-section avatar><q-icon color="green" text-color="white" name="check" @click="doneTask(index)"/></q-item-section>
        </q-item>
      </q-list>
    </div>
    <div class="row">
      <q-list highlight bordered class="col" padding>
        <q-item-label header>Done</q-item-label>
        <q-item clickable v-ripple v-for="task in done" :key="task">
          <q-item-section>{{task}}</q-item-section>
        </q-item>
      </q-list>
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'IndexPage',
  data(){
    return{
      text:'',
      tasks:[],
      done:[]
    }
  },
  methods:{
    addTask(){
      this.tasks.push(this.text);
      this.text= '';
    },
    doneTask(id){
      this.done.push(this.tasks[id])
      this.tasks.splice(id, 1)
    }
  }
})
</script>
