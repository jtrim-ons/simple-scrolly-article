<script>
	import { themes } from '../config.js';

	export let fullWidth=false;
	export let imgurl;
	export let height40=false;
	export let alttext="";
	export let title="";
</script>

<style>
    .img-filler-img.notFullWidth {
        /*padding-left: 0;
        padding-right: 0;*/
        box-sizing: border-box;
        margin: 0 auto 0 auto;
        max-width: 1000px;
    }
    .img-filler-img.fullWidth {
        padding-left: 0;
        padding-right: 0;
        margin-left: auto;
        margin-right: auto;
        max-width: 1000px;
    }
    .height40 {
        height: 40px;
        padding-top: 21px;
        padding-bottom: 6px;
    }
    @media (min-width: 992px) {
        .img-filler-img.notFullWidth {
            margin: 0 auto 0 8px;
        }
    }
    @media (min-width: 1050px) {
        .img-filler-img.fullWidth {
            margin-left: 32px;
        }
    }
</style>

<div class="img-filler-img" class:fullWidth class:notFullWidth="{!fullWidth}">
    <img src="{imgurl}" alt="{alttext}" title="{title}" class:height40 />
</div>
