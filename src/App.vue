<script>
export default {
  data() {
    return {
      tasks: [],
      msg: "",
    };
  },

  methods: {
   
   addTask(task) {
      if (task === "") return;

      let _id = Math.random() * Date.now();

      this.tasks.push({ text: task, id: _id });

       this.msg = "";
    },

    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
  },
};
</script>

<template>
  <div class="w-full">
    <div
      class="w-[30%] mx-auto mt-28 bg-[#F3F1F5] rounded-md h-auto pb-6 flex flex-col gap-y-2"
    >
      <div class="w-[90%] mx-auto text-2xl h-10 mt-6">
        <h1 class="font-bold">TodoApp</h1>
      </div>

      <div class="w-[90%] mx-auto flex justify-between items-center h-14">
        <input
          @keypress.enter="addTask(msg)"
          v-model="msg"
          id="input"
          class="w-[80%] h-10 border-2 px-2 rounded- outline-0"
          type="text"
          placeholder="digite uma tarefa"
        />
        <div
          @click="addTask(msg)"
        
          id="addTask"
          class="w-12 h-10 bg-[#BFA2DB] cursor-pointer rounded-sm flex items-center justify-around"
        >
          <div class="w-10">
            <img class="w-full" src="./assets/add-outline.svg" alt="" />
          </div>
        </div>
      </div>

      <div
        id="container-task"
        class="w-[90%] mx-auto h-auto flex flex-col gap-y-2"
      >
        <div
          v-for="task in tasks"
          :key="task"
          class="w-full h-10 border-l-4 border-[#BFA2DB] rounded-sm px-2 bg-[#F0D9FF] flex justify-between items-center"
        >
          <p>{{ task.text }}</p>
          <img
            @click="deleteTask(task.id)"
            class="w-6 cursor-pointer transition-transform ease-out duration-150 hover:-translate-y-1"
            src="./assets/trash-outline.svg"
            alt=""
          />
        </div>

        <p class="pl-1">Total de tarefas : {{tasks.length}}</p>
      </div>
    </div>
  </div>
</template>
