<script lang="ts">
    export let command = "";
</script>

<div id="command-input">
    <label>visitor@longph.com:~$</label><input type="text" bind:value={command}/>
</div>

<style>
    label {
        color: forestgreen;
        font-size: 15px;
        font-weight: bold;
    }

    input {
        font-family: Consolas, Consolas Bold, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, serif;
        background: transparent;
        border: none;
        color: #73ABAD;
        font-size: 15px;
        font-weight: bold;
        outline: none;
        width: 600px;
        margin: 0 10px 0 10px;
    }

    #command-input {
        position: relative;
        left: 10px;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: flex-start;
        width: 100%;
        height: 100%;
        padding: 0 10px;
    }
</style>