<script>
    const eq = "⬄";
    const msPerDay = 86400000;
    const hrPerDay = 25;
    const milli = Math.floor(msPerDay / 60 / 60 / hrPerDay);
    let time = new Date();
    let hr24 = time.getHours();
    let min24 = time.getMinutes();
    let sec24 = time.getSeconds();
    let hr25 = 0;
    let min25 = 0;
    let sec25 = 0;

    const convert24To25 = () => {
        let milli24 = sec24*1000 + min24*60*1000 + hr24*60*60*1000;
        let milli25 = milli24 % milli;
        milli24 = Math.floor(milli24 / milli);
        sec25 = milli24 % 60;
        milli24 = Math.floor(milli24 / 60);
        min25 = milli24 % 60;
        milli24 = Math.floor(milli24 / 60);
        hr25 = milli24 % hrPerDay;
    }

    const convert25To24 = () => {
        let milli25 = sec25*milli + min25*60*milli + hr25*60*60*milli;
        let milli24 = milli25 % 1000;
        milli25 = Math.floor(milli25 / 1000);
        sec24 = milli25 % 60;
        milli25 = Math.floor(milli25 / 60);
        min24 = milli25 % 60;
        milli25 = Math.floor(milli25 / 60);
        hr24 = milli25 % 24;
    }
    convert24To25();  // run once to initiate converter
</script>

<h3>Convert 25 hour to and from 24 hour</h3>
<div class="converter-panel">
    <div>
        <h3>24 Hour</h3>
        <input type="number" bind:value={hr24} on:change={convert24To25} min="0" max="23" /> :
        <input type="number" bind:value={min24} on:change={convert24To25} min="0" max="59" /> :
        <input type="number" bind:value={sec24} on:change={convert24To25} min="0" max="59" />
    </div>
    <div>
        <h1>{eq}</h1>
    </div>
    <div>
        <h3>25 Hour</h3>
        <input type="number" bind:value={hr25} on:change={convert25To24} min="0" max="24" /> :
        <input type="number" bind:value={min25} on:change={convert25To24} min="0" max="59" /> :
        <input type="number" bind:value={sec25} on:change={convert25To24} min="0" max="59" />
    </div>
</div>

<style>
    .converter-panel {
        display: flex;
        justify-content: center;
        align-items: center;
        /* max-width: 500px; */
    }
    input {
        max-width: 30px;
    }
</style>