<script lang="ts">
	import type { Snippet } from 'svelte';
	import type { Product } from './types';

	type Props = {
		product: Product;
		relatedProduct?: Product;
		productDisplay: Snippet<[Product]>;
		children: Snippet;
	};

	let { product, relatedProduct, productDisplay, children }: Props = $props();
</script>

<section class="flex flex-col gap-5">
	{@render children()}

	{@render productDisplay(product)}

	{#if relatedProduct}
		<aside>You might also be interested in:</aside>
		{@render productDisplay(relatedProduct)}
	{/if}
</section>
