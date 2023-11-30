<script lang="ts">
  const commands = ["help", "whoami", "projects", "contact", "clear"] as const;
  import CommandInput from "./lib/components/CommandInput.svelte";
  let command = "";
  const handleCommand = (e) => {
    switch(e.detail) {
      case "help":
        console.log("Available commands: ", commands);
        break;
      case "whoami":
        console.log("I'm Long Pham, a software engineer based in Espoo, Finland.");
        break;
      case "projects":
        console.log(`You can find my projects <a href="https://github.com/phamduylong">here</a>`);
      default:
        console.log("Command not found. Type 'help' for a list of available commands.");
        break;
    }
  }
</script>

<main>
<p><br/>Welcome to my interactive web terminal.</p>
<p><br/>For a list of available commands, type 'help'.</p>
  <CommandInput on:command={handleCommand} bind:command={command} />
</main>

<style>
  p {
    position: relative;
    left: 10px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-start;
    width: 100%;
    height: 100%;
    padding: 0 10px;
    color: #B89076;
  }
</style>
