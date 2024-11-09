<script lang="ts">
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let command = "";
  let commandHistory: string[] = JSON.parse(
    localStorage.getItem("commandHistory") ?? "[]"
  );
  let lastCommandIdx = commandHistory.length === 0 ? 0 : commandHistory.length;
</script>

<div class="space-x-2 flex !flex-row">
  <label for="command" class="!text-[forestgreen] font-bold"
    >visitor@longph.com:~$</label
  ><input
    class="bg-[#151515] border-none text-[#73abad] w-full font-bold outline-none overflow-scroll"
    autofocus={true}
    name="command"
    autocomplete="off"
    type="text"
    bind:value={command}
    on:keydown={(e) => {
      switch (e.key) {
        case "ArrowUp":
          e.preventDefault();
          if (lastCommandIdx > 0) {
            lastCommandIdx -= 1;
          }
          command = commandHistory[lastCommandIdx];
          break;
        case "ArrowDown":
          e.preventDefault();
          if (lastCommandIdx < commandHistory.length - 1) {
            lastCommandIdx += 1;
          }
          command = commandHistory[lastCommandIdx];
          break;
        case "Enter":
          commandHistory = [...commandHistory, command.trim()];
          localStorage.setItem(
            "commandHistory",
            JSON.stringify(commandHistory)
          );
          lastCommandIdx = commandHistory.length - 1;
          dispatch("command", command.trim());
          command = "";
          break;
        default:
          // FIXME: Any key will trigger this, we only want to do this when text changed. For some reason, on:change doesn't work for text deletion
          lastCommandIdx = commandHistory.length;
          break;
      }
    }}
  />
</div>
