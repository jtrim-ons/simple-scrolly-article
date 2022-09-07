<script>
	import { themes } from '../config.js';

	export let imgurl;
	export let theme = 'story_of_census';
	export let center = true;
	export let wide = false;
	export let short = false;
	export let alttext = "";
	export let title = "";
</script>

<style>
	section {
		padding: 0;
        margin-top: 36px;
	}
	.img-filler-div {
        padding: 0;
        display: flex;
        flex-wrap: wrap;
    }
	.img-filler-gradient-bar {
        height: .8em;
        padding: 0;
        background-image: linear-gradient(to right, #2e3d8b , #8c1e7f);
    }
	.img-filler-text {
        flex-grow: 1;
        padding-left: 0;
        padding-right: 0;
        padding-bottom: 18px;
    }
    .img-filler-img {
	    padding: 0;
	    flex-grow: 1.8;
    }
	.img-filler-img img {
	    width: 100%;
	    display: block;
	    margin: 0 auto;
    }
	.img-filler-img.narrow-img img {
	    width: 80%;
    }
    @media (min-width: 600px) {
        .img-filler-div {
            padding: 0;
            display: flex;
            flex-wrap: nowrap;
        }
        .img-filler-text {
            padding-right: 24px;
            flex: 40%;
        }
        .img-filler-img {
            padding: 12px;
            flex: 60%;
        }
        .img-filler-img img, .img-filler-img.narrow-img img {
            width: 100%;
            display: block;
            margin: 0;
        }
    }
	.img-filler-div :global(h2) {
        font-style: italic;
        color: #414042;
    }
	.img-filler-div :global(p) {
        color: #414042;
    }
	.short {
		/* min-height: 70vh; */
	}
</style>

<section class="img-filler-section" style="color: {themes[theme]['text']}; background-color: {themes[theme]['img-background']};">
	<div class="middle" class:center class:col-mediumwide={true} class:height-full={!short} class:short>
        <div class="img-filler-div">
            <div class="img-filler-text">
                <div class="img-filler-gradient-bar"></div>
                <slot></slot>
            </div>
            <div class="img-filler-img" class:narrow-img={!wide}>
                <img src="{imgurl}" alt="{alttext}" title="{title}"/>
            </div>
        </div>
	</div>
</section>
