<script lang="ts">
	import type { Snippet } from 'svelte';
	import type { Product } from './types';

	type Props = {
		product: Product;
		relatedProduct?: Product;
		productDisplay?: Snippet<[Product]>;
		children?: Snippet;
	};

	let { product, relatedProduct, productDisplay, children }: Props = $props();

	let productDisplaySnippetToUse: Snippet<[Product]> = productDisplay ?? productDisplayFallback;
</script>

{#snippet productDisplayFallback(p: Product)}
	<div class="flex flex-row gap-3">
		<img class="max-w-[50px]" src={p.url} alt="product url" />
		<div class="flex flex-col">
			<h2 class="text-base font-bold">{p.name}</h2>
		</div>
	</div>
{/snippet}

<section class="flex flex-col gap-5">
	{#if children}
		{@render children()}
	{:else}
		<h1>Fallback content</h1>
	{/if}

	{@render productDisplaySnippetToUse(product)}

	{#if relatedProduct}
		<aside>You might also be interested in:</aside>
		{@render productDisplaySnippetToUse(relatedProduct)}
	{/if}
</section>
