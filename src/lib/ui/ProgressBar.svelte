<script>
	export let index;
	export let count = 1;

	let progressCircles = [{position: 20}];
	$: {
	    progressCircles = [];
	    for (let i=0; i<count; i++)
	        progressCircles.push({index: i, position: i * 25 + 20});
    }

    function growCircle(node, { duration }) {
		return {
			duration,
			tick: t => {node.setAttribute('r', t*6)}
		};
	}

    function circlePosition(index) {
        if (!progressCircles[index]) return 20;
        if (!index) return 20;
        if (index >= progressCircles.length) {
            return progressCircles[progressCircles.length - 1].position;
        }
        return progressCircles[index].position;
    }
</script>

<style>
    svg {
        max-height: 100vh;
        display: block;
        margin: 0 auto;
    }
</style>

<div class="progress-bar">
    <svg viewBox="0 0 50 615">
        <line x1="25" x2="25" y1="20" y2="{circlePosition(progressCircles.length - 1)}" stroke="#7C7EB2" stroke-width="1.5"/>
        <line x1="25" x2="25" y1="20" y2="{circlePosition(index)}" stroke="white" stroke-width="1.5"/>
        {#each progressCircles as c}
            <circle cx="25" cy="{c.position}" r="10" fill="#2e3d8b" stroke="{c.index <= index ? 'white' : '#7C7EB2'}" stroke-width="1.5"/>
            {#if c.index == index || (c.index == progressCircles.length - 1 && index == progressCircles.length)}
                <circle cx="25" cy="{c.position}" fill="white" stroke="none" transition:growCircle="{{duration: 200}}"/>
            {/if}
        {/each}
    </svg>
</div>

