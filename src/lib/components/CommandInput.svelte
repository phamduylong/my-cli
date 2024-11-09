<script lang="ts">
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let command = "";
  let lastCommand = "";
</script>

<div class="space-x-2 flex !flex-row">
  <label for="command" class="!text-[forestgreen] font-bold"
    >visitor@longph.com:~$</label
  ><input
    class="bg-[#151515] border-none text-[#73abad] font-bold outline-none overflow-scroll"
    autofocus={true}
    name="command"
    autocomplete="off"
    type="text"
    bind:value={command}
    on:keydown={(e) => {
      if (e.key === "Enter") {
        lastCommand = command;
        dispatch("command", command);
        command = "";
      }
      if (e.key === "ArrowUp") {
        console.log("ArrowUp, ", lastCommand);
        e.preventDefault();
        command = lastCommand;
        dispatch("command", command);
        lastCommand = command;
      }
    }}
  />
</div>
