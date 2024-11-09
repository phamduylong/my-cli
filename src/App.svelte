<script lang="ts">
  const commands = ["help", "whoami", "projects", "contact", "clear"] as const;
  import CommandInput from "./lib/components/CommandInput.svelte";
  let command = "";
  let output = "";

  function handleCommand(e: { detail: string }) {
    switch (e.detail.trim().toLowerCase()) {
      case "help":
        output = `<b>Available commands:</b><div><ul>${commands.map((command) => `<li>&nbsp;&nbsp;${command}</li>`).join("")}</ul></div>`;
        break;
      case "whoami":
        output = "I'm Long Pham, a software engineer based in Espoo, Finland.";
        break;
      case "projects":
        output = `You can find my projects&nbsp;<a class="underline" href="https://longph.com/projects">here</a>.`;
        break;
      case "contact":
        output = `You can contact me via email at <a class="underline" href="mailto:longphamduy2002@gmail.com">longphamduy2002@gmail.com</a> 
        or <a class="underline" href="https://longph.com/contact" target="_blank"> write to me.</a>`;
        break;
      case "clear":
        output = "";
        break;
      case "":
        break;
      default:
        output =
          "Command not found. Type 'help' for a list of available commands.";
        break;
    }
  }
</script>

<main>
  <div class="flex flex-col container p-4 !text-[#b89076] !overflow-hidden">
    <div class="font-bold">
      Welcome to my interactive web terminal.
    </div>
    <div class="font-bold">
      For a list of available commands, type 'help'.
    </div>
    <CommandInput on:command={handleCommand} bind:command />
    {#if output}
      <div class="space-x-1">&#8618;&nbsp;{@html output}</div>
    {/if}
  </div>
</main>
