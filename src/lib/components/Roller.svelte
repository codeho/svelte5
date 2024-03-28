
<script>
    /** @type {number} */
    let dice = $state(0);
    /** @type {Array.<number>} */
    let rolls = $state([]);

    function draw() {
        dice = Math.floor(Math.random() * Math.floor(5)) + 1;
        rolls[rolls.length] = dice;
    }
    function reset() {
        dice = 0;
        rolls = [];
    }
</script>
<svelte:head>
    <link href="https://unpkg.com/nes.css@latest/css/nes.min.css" rel="stylesheet" />
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap" rel="stylesheet">

</svelte:head>
<section style="padding-top: 50px;">
    <button on:click={draw}> Let's draw </button>
    <button on:click={reset}> Let's restart </button>
</section>
<section>
    <div class="grid place-content-center pb-7">
    <h2 style="text-align: center">
        <span class="nes-text is-primary">{dice == 0 ? "Let's start rolling" : dice}</span>
    </h2>

    {#each rolls as t, index}
        <p style="text-align: center">
            <span class="nes-text is-success">Rolling number {index + 1}, the dice says {t}</span>
        </p>
    {/each}
    </div>
</section>
