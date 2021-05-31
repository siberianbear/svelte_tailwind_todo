<script lang="ts">

  import LogoItem from './lib/Logo.svelte'

  let todoList = [];

  let todo_text = ''

  function addTodo() {
    if (todo_text) {
      todoList = [...todoList, {text: todo_text, status: false}];
      todo_text = ''
    }
  }

  function removeTodo(index) {
      todoList.splice(index, 1)
      todoList = todoList;
  }

</script>

<main class='m-0 px-2 py-2 relative z-10 h-screen'>

  <div class="flex justify-center items-center w-screen h-screen z-0 absolute bottom-0 left-0 opacity-30 pr-3">
    <LogoItem pic_logo="svelte_logo.png" />
    <span class="font-bold text-3xl mx-1">+</span>
    <LogoItem pic_logo="tw_logo.svg" />
  </div>

  <div class="main-layer relative z-20">
    <div class="w-full flex justify-between">
      <input type="text" bind:value={todo_text} autocomplete="off" placeholder="Add your task here" class='w-10/12 appearance-none bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500'/>
      <button on:click={addTodo} class="bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded">Add task</button>  
    </div>
  
    <hr class="my-3" />
  
    <div class="flex flex-col w-full px-1">
  
      {#each todoList as item, index}
          <div class="h-10 px-5 my-2 flex justify-between bg-black bg-opacity-70 rounded text-white">
            <div class="w-10/12 flex items-center text-left">
              <input bind:checked={item.status} type="checkbox">
              <span class:checked={item.status} class='truncate pl-1' > {item.text} </span>
            </div>
  
            
            <div class="w-1/12 flex items-center justify-end">
              <span class="cursor-pointer" on:click={() => removeTodo(index)}>⏏️</span>
            </div>
  
          </div>
  
      {/each} 
  </div>

</div>

  
</main>

<style global lang="postcss">

  /* only apply purgecss on utilities, per Tailwind docs */
  /* purgecss start ignore */
  @tailwind base;
  @tailwind components;
  /* purgecss end ignore */

  @tailwind utilities;


  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

</style>