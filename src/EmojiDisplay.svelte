<script>
    export let emoji;
    export let currentEmoji = emoji;
    let currentButton = 'button1';
</script>

<style>
    div {
        font-size: 3em;
        margin-bottom: 0.5em;
    }
</style>

<div>{currentEmoji}</div>
<button
class="btn" 
class:btn-primary={currentButton === 'button1'} 
on:click={() => currentButton = 'button1'
}>button 1</button>
<button
class="btn" 
class:btn-primary={currentButton === 'button2'} 
on:click={() => currentButton = 'button2'}
>button 2</button>
<button
class="btn" 
class:btn-primary={currentButton === 'button3'} 
on:click={() => currentButton = 'button3'}
>button 3</button>