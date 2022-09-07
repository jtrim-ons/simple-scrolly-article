<script>
  import { themes } from '../config.js';
	import ONSLogo from "./ONSLogo.svelte";
	import CensusLogo from "./CensusLogo.svelte";
	
	export let theme = 'story_of_census';
	export let filled = true;
	export let center = false;
	export let census = false;

	let primary = theme == "dark" ? "white" : filled ? "#003c57" : "#222222";
	let secondary = theme == "dark" || filled ? "#a8bd3a" : "#222222";
	let census_color = theme == "dark" ? "white" : "#902082";
</script>

<nav style="border-bottom-color: {themes[theme]['muted']}; {filled ? 'background-color: ' +  themes[theme]['img-background'] + ';' : ''}">
  <div class="col-wide middle" class:center>
		<div class="logo-block">
			<a href="https://www.ons.gov.uk/" class="logo" style:width="270px">
				<ONSLogo {primary} {secondary}/>
			</a>
			{#if census}
			<a href="https://www.ons.gov.uk/census/" class="logo" style:width="160px">
				<CensusLogo color={census_color}/>
			</a>
			{/if}
		</div>
  </div>
</nav>

<style>
	nav {
		-webkit-box-sizing: border-box;
		box-sizing: border-box;
		position: relative;
		height: 46px;
		z-index: 1;
	}
	.col-wide {
		width: calc(100% - 24px) !important;
	}
	.logo-block {
		position: relative;
		display: flex;
		flex-direction: row;
		align-items: center;
		max-width: 100%;
	}
	.logo {
		box-sizing: border-box;
		cursor: pointer;
		padding: 4px;
		margin: 0;
		line-height: 1;
	}
    @media (min-width: 992px) {
        .logo {
            margin-left: 8px;
        }
    }
</style>
