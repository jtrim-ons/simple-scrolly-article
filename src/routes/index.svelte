<script>
    //export let gtag;

	// CORE IMPORTS
	import { setContext, onMount } from "svelte";
	import { themes } from "$lib/config.js";
	import ONSHeader from "$lib/layout/ONSHeader.svelte";
	import ONSFooter from "$lib/layout/ONSFooter.svelte";
	import Header from "$lib/layout/Header.svelte";
	import CustomisableSection from "$lib/layout/CustomisableSection.svelte";
	import Section from "$lib/layout/Section.svelte";
	import Scroller from "$lib/layout/Scroller.svelte";
	import Img from "$lib/layout/Img.svelte";
	import PlainImg from "$lib/layout/PlainImg.svelte";
	import PlainVideo from "$lib/layout/PlainVideo.svelte";
	import ProgressBar from "$lib/ui/ProgressBar.svelte";

	// CORE CONFIG (COLOUR THEMES)
	// Set theme globally (options are 'light', 'dark' or 'lightblue')
	let theme = "story_of_census";

	// CONFIG FOR SCROLLER COMPONENTS
	// Config
	const threshold = 1;
	// State
	let index;   // index of current section
	let count;   // number of sections
</script>

<ONSHeader {theme} filled={true} center={false} census={true}/>

<div style="position: relative">
    <Scroller {threshold} bind:index bind:count>
        <div class="foreground" slot="foreground">
            <Header theme="dark" bgcolor="#206095" bgfixed={true} bggradient={"linear-gradient(to right, #2e3d8b , #8c1e7f)"}  center={false} short={true}>
                <h1>Title of the Article</h1>
                <p class="article-date" style="margin-top: 5px">
                    20 June 2022
                </p>
                <p class="text-big" style="margin-top: 5px">
                    ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... .....
                </p>
                <p class="text-big" style="margin-top: 5px">
                    ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... .....
                </p>
            </Header>

            <Section {theme}>
                <h2>Section Title</h2>
                <p>
                    ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... .....
                </p>
                <p>
                    ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... .....
                </p>
            </Section>

            <Img {theme} imgurl="img/mountain.jpg" short={true} center={false}
                    alttext="Alt text"
                    title="Title">
                <h2>.....</h2>
                <p>
                    .....
                </p>
                <p>
                    .....
                </p>
                <p>
                    .....
                </p>
            </Img>

            <Section theme={"dark"}>
                <h2>Section Title</h2>
                <p>
                    .....
                </p>
                <p>
                    .....
                </p>
                <p>
                    .....
                </p>
                <p>
                    .....
                </p>
            </Section>

            <CustomisableSection {theme}>
                <div class="col-medium text-column less-padding-after">
                    <h2>Section Title</h2>
                    <p>
                        .....
                    </p>
                    <p>
                        .....
                    </p>
                </div>
                <PlainImg
                    fullWidth={true}
                    imgurl="img/waterfall.jpg"
                    alttext="Alt text"
                    title="Title"
                ></PlainImg>
                <div class="col-medium text-column less-padding-before">
                    <p>
                        .....
                    </p>
                    <p>
                        .....
                    </p>
                    <p>
                        .....
                    </p>
                </div>
            </CustomisableSection>
        </div>
    </Scroller>
</div>

<ONSFooter {theme}/>

<style>
	/* Styles specific to elements within the demo */
	:global(svelte-scroller-foreground) {
		pointer-events: none !important;
	}
	:global(svelte-scroller-foreground section div) {
		pointer-events: all !important;
	}
</style>
