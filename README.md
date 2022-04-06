# svelte-flickity
A Svelte component wrapper for Flickity carousel

![npm](https://img.shields.io/npm/v/svelte-flickity)

## Usage

Install:
```
npm install -save svelte-flickity
```

Import the Flickity carousel and add to your template:
```
<script>
	import Carousel from "svelte-flickity";
</script>

<Carousel>
	<div>Slide 1</div>
	<div>Slide 2</div>
	<div>Slide 3</div>
</Carousel>
```

## With options (optional)
```
<script>
	import Carousel from "svelte-flickity";

	const options = {
		freeScroll: true,
		freeScrollFriction: 0.03,
		wrapAround: true,
		etc..
	};
</script>

<Carousel {options}>
	<div>Slide 1</div>
	<div>Slide 2</div>
	<div>Slide 3</div>
</Carousel>
```

All options on Flickity website:
[https://flickity.metafizzy.co/options.html](https://flickity.metafizzy.co/options.html)


## Disclaimer
I've had no involvement in the development of Flickity.

[Please buy a Flickity license](https://flickity.metafizzy.co/license.html) if you're deploying a commercial site

I love the library and discovered it was tricky to add to SvelteKit with SSR - so made this wrapper. You can easily grab my code and implement your own component without this npm package (I'm using the package to avoid an extra component in my codebase):

```
<script>
	import "../node_modules/flickity/css/flickity.css";

	export let options;

	let flickity;

	function init(el) {
		(import('flickity'))
			.then((lib) => lib.default)
			.then((carousel) => flickity = new carousel(el, options))
			.catch((x) => console.log(x));
	}
</script>

<div use:init class="carousel">
	<slot></slot>
</div>

<!-- can also import css like this: -->
<!-- <style global>
	import "../node_modules/flickity/css/flickity.css";
</style> -->
```

Apologies to the 60+ people that downloaded the broken pre 1.0 version of this - it should work now!

You can log issues here:
[https://github.com/danieluntiedt/svelte-flickity/issues](https://github.com/danieluntiedt/svelte-flickity/issues)