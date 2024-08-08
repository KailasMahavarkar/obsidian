basic code 
```cpp

<a
	class="_3n8fnaug _3n8fnamv _3n8fnaf9 _3n8fna1 _3n8fna7n _1i2djtb9 _9nihix1c"
	href="/big-bachat-dhamaal-sale-store"
	style="
		align-items: stretch;
		border-width: 0px;
		box-sizing: border-box;
		display: flex;
		flex-basis: auto;
		flex-direction: column;
		flex-shrink: 0;
		min-height: 0px;
		min-width: 0px;
		position: relative;
		z-index: 0;
	"
>
	<div
		class="zlQd20"
		style="
			--aspect-ratio: 211/35;
			--aspect-ratio-m: 211/35;
			--aspect-ratio-l: 211/35;
			flex: 1 1 0%;
		"
	>
		<picture>
            <source
				srcset="
					https://rukminim2.flixcart.com/fk-p-flap/1600/270/image/e72a333d048f834c.jpg?q=80 1x,
					https://rukminim2.flixcart.com/fk-p-flap/3200/540/image/e72a333d048f834c.jpg?q=60 2x
				"
				media="(min-width: 1192px)"
			/>
			<source
				srcset="
					https://rukminim2.flixcart.com/fk-p-flap/1000/170/image/e72a333d048f834c.jpg?q=80 1x,
					https://rukminim2.flixcart.com/fk-p-flap/2000/340/image/e72a333d048f834c.jpg?q=60 2x
				"
				media="(min-width: 768px) and (max-width: 1191px)"
			/>
			<img
				loading="auto"
				alt="Image"
				srcset="
					https://rukminim2.flixcart.com/fk-p-flap/480/80/image/e72a333d048f834c.jpg?q=80  1x,
					https://rukminim2.flixcart.com/fk-p-flap/960/160/image/e72a333d048f834c.jpg?q=60 2x
				"
				style="
					width: 100%;
					margin: auto;
					display: block;
					object-fit: cover;
					opacity: 1;
					aspect-ratio: 211 / 35;
				"
				src="https://rukminim2.flixcart.com/fk-p-flap/480/80/image/e72a333d048f834c.jpg?q=90"
			/>
		</picture>
		<img
			src="https://rukminim2.flixcart.com/fk-p-flap/480/80/image/e72a333d048f834c.jpg?q=20"
			loading="auto"
			alt="Image"
			style="
				width: 100%;
				margin: auto;
				display: block;
				position: absolute;
				inset: 0px;
				padding: inherit;
				object-fit: cover;
				opacity: 0;
				aspect-ratio: 211 / 35;
			"
		/>
	</div>
</a>


```



ffmpeg -i flower_2_high.jpg -vf scale=20:-1 flower_2_lowest.jpg
ffmpeg -i flower_3_high.jpg -vf scale=20:-1 flower_3_lowest.jpg
ffmpeg -i flower_4_high.jpg -vf scale=20:-1 flower_4_lowest.jpg

-----


# Part 1: Images on web

```html
<img
    style="width: 100%; border-radius: 1rem"
    src="https://placehold.co/3200x800/png"
    srcset="
        https://placehold.co/800x200/png   800w,
        https://placehold.co/1600x400/png 1600w,
        https://placehold.co/3200x800/png 3200w
    "
/>

/* or */

<img
    style="width: 100%; border-radius: 1rem"
    src="https://placehold.co/3200x800/png"
    srcset="
        https://placehold.co/800x200/png  1x,
        https://placehold.co/1600x400/png 2x,
        https://placehold.co/3200x800/png 3x
    "
/>

```


## deep dive of `srcset` and `src`

Initially in our image tag we used `src` tag to define image url, this is all good but few years back browsers started supporting `srcset` tag which takes it step further

img `srcset`:
A list of one of more strings separated by commas indicating a set of possible image sources for the user agent to use


Understanding Image srcset attribute:


