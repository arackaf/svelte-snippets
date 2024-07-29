<script lang="ts">
	let val1 = $state(0);
	let val2 = $state(0);
</script>

{#snippet helloWorld()}
	<span>Hello World</span>
{/snippet}

{@render helloWorld()}
{@render helloWorld()}
