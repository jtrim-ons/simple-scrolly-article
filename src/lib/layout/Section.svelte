<script>
	import { themes } from '../config.js';

	export let theme = 'story_of_census';
</script>

<section class="theme-{theme}" style="color: {themes[theme]['text']}; background-color: {themes[theme]['background']}">
	<div class="col-medium text-column">
		<slot></slot>
	</div>
</section>
