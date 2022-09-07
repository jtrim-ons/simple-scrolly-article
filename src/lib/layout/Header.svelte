<script>
  import { themes } from '../config.js';

  export let theme = 'story_of_census';
  export let bggradient = null;
  export let bgimage = null;
  export let bgcolor = null;
  export let bgfixed = false;
  export let center = true;
  export let short = false;

  let style = '';

  if (bggradient) {
    style += `background-image: ${bggradient};`;
  } else if (bgimage) {
    style += `background-image: url(${bgimage});`;
  } else {
    style += 'background-image: none;';
  }

  if (bgfixed) {
    style += ' background-attachment: fixed;';
  }
</script>

<style>
  /*
  .short {
    min-height: 85vh;
  }
  */
  .v-padded {
    box-sizing: border-box;
    padding: 12px 24px;;
  }
</style>

<header style="color: {themes[theme]['text']}; background-color: {bgcolor ? bgcolor : themes[theme]['background']}; {style}" class:short>
	<div class="v-padded col-medium middle" style="position: relative" class:short class:height-full={!short}>
		<div class:center>
            <slot></slot>
        </div>
	</div>
</header>
