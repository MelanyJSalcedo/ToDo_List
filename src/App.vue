<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs

/*import { ref } from "vue";

// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
const message = ref("Hola mundo");*/
import { CheckCircleIcon }  from "@heroicons/vue/solid";
//import Tasks from './components/Tasks.vue';
import {ref} from "vue";

let id= ref(1);//variable reactiva

interface Todo {
  identifier: number,
  text: string,
  styles: {button:string; text:string
  };
}

const handleClick = ({ styles }: Todo): void => {
  styles.button = styles.button === "text-re-400" ? "text-green-400":"text-red-400";
  styles.text = styles.text === "" ? "line-through": "";

};
const todos = ref([
  {
  identifier: id.value++,
  text:"Task 1",
  stykes:{ button:"text-red-400", text: "" }
},
{
  identifier: id.value++,
  text:"Task 2",
  stykes:{ button:"text-red-400", text: "" }
},
{
  identifier: id.value++,
  text:"Task 3",
  stykes:{ button:"text-red-400", text: "" }
},
])
</script>

<template>
  <div class="flex h-screen items-center justify-center bg-slate-300 "> 
    <div class="flex h-fit w-fit flex-col rounded-lg bg-white py-14 px-14 font-poppins ">
      <div class="flex fex-row my-auto gap=32">
       <div class="flex flex-row gap-3">
          <h2 class="my-auto text-5xl font-bold">
             day
          </h2>
          <div class="flex flex-col">
            <h2 class="font-bold">
              month

            </h2>
            <h2 class="font-bold">
              year
            </h2>

          </div>
       </div>
      
       <h2 class="my-auto text-2xl font-bold">
         weekday
       </h2>
     </div >
     <div v-for="todo in todos " :key="todo.identifier">

     </div>

     <div class="relative mt-12 flex h-10 w-full flex-row">
       <h2 :class="'h-10 w-fit text-2xl' +' ' + Todo.styles.texto"> 
         {{Todo.text}}
       </h2>
       <button @click="handleClick(Todo)" class ="my-auto absolute right-0 h-10 w-10">
         
         <CheckCircleIcon :class=" 'h-10 text-2xl text-red-400' + ' ' + Todo.styles.button">
         </CheckCircleIcon>

       </button>
      </div>
    </div>
  </div>
</template>
