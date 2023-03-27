<script>
    export let text = "Tooltip text";
    let visible = false;

    function show(e) {
        // if e not question mark, return
        if (e.target.id !== "question-mark") return;

        visible = !visible;
    }
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<div
    id="question-mark"
    on:mouseover={show}
    on:mouseout={show}
    on:focus={show}
    on:blur={show}
    on:touchstart={show}
    on:touchend={show}
>
    ?
    {#if visible}
        <div id="tooltip">
            {text}
        </div>
    {/if}
</div>

<style>
    #question-mark {
        display: inline-block;
        position: relative;

        color: var(--white);

        font-size: 18px;
        font-weight: 700;
        font-weight: 400;

        vertical-align: top;

        text-align: center;
        text-decoration: underline;
        cursor: pointer;

        padding: 10px;
        margin: -10px;
    }
    #tooltip {
        position: absolute;
        top: calc(100%);
        left: 50%;
        transform: translateX(-50%);

        width: 300px;

        background-color: #fff;
        border: 4px solid var(--black);
        color: var(--black);

        font-size: 20px;
        font-weight: 400;

        text-align: center;
        text-decoration: none;

        padding: 10px 20px;

        border-radius: 5px;
        box-shadow: 0px 5px 15px 0px rgba(0, 0, 0, 0.2);

        animation: show-up 0.2s ease-in-out;
    }
</style>
