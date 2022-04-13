<script>
	import "flickity/css/flickity.css";

	export let options;

	let flickity;

	function init(el) {
		(import("flickity"))
			.then((lib) => lib.default)
			.then((carousel) => flickity = new carousel(el, options))
			.catch((x) => console.log(x));
	}
</script>

<div use:init class="carousel">
	<slot></slot>
</div>
