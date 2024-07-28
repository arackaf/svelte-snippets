<script>
	import '../app.css';
</script>

<div class="flex flex-col gap-4 p-4">
	<div class="flex flex-row gap-3">
		<a href="/snippets-for-reuse">Basic snippets</a>
		<a href="/injected-snippets">Injected snippets</a>
		<a href="/injected-snippets-with-defaults">Injected snippets with defaults</a>
	</div>
	<slot></slot>
</div>
