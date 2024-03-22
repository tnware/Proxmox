<script>
	export let app;

	// Function to copy the script URL to clipboard
	function copyToClipboard(text) {
		navigator.clipboard.writeText(text).then(
			() => {
				console.log('Copying to clipboard was successful!');
			},
			(err) => {
				console.error('Could not copy text: ', err);
			}
		);
	}

	function formatDate(dateString) {
		const options = { year: 'numeric', month: 'long', day: 'numeric' };
		return new Date(dateString).toLocaleDateString(undefined, options);
	}
</script>

<div class="item mt-4 rounded-xl bg-neutral-700 p-6 shadow-lg">
	<p class="flex justify-center">
		<img src={app.image_url} alt={app.name} class="h-48" />
	</p>
	<h1 class="my-2 text-center text-3xl font-semibold">{app.name}</h1>
	<div class="text-center text-sm text-gray-500">
		Added: {formatDate(app.date_added)} | Last Updated: {formatDate(app.last_updated)}
	</div>
	<div class="my-2 text-lg">{@html app.description}</div>
	<p class="mt-4">Run the command below in the <strong>Proxmox VE Shell</strong>.</p>
	<div class="relative mt-2 rounded-lg bg-gray-800 p-4 text-white">
		<button
			class="absolute right-2 top-2 rounded bg-blue-500 px-2 py-1 font-bold text-white hover:bg-blue-700"
			on:click={() => copyToClipboard(`bash -c "$(wget -qLO - ${app.script_url})"`)}>Copy</button
		>
		<code class="block whitespace-pre-wrap">{`bash -c "$(wget -qLO - ${app.script_url})"`}</code>
	</div>
	<!-- <p class="mt-2">It is recommended to answer “yes” (y) to all options presented during the process.</p> -->
	{#if app.type == 'lxc'}<h3 align="center" id="heading">
			⚡ Default Settings: 1GB RAM - 4GB Storage - 2vCPU ⚡
		</h3>{/if}
	{#if app.variants && app.variants.length > 0}
		<h2 class="mt-4 text-xl font-semibold">Variants</h2>
		<ul class="space-y-2">
			{#each app.variants as variant}
				<li>
					<button
						on:click={() => (variant.showDetails = !variant.showDetails)}
						class="cursor-pointer text-lg font-bold hover:underline"
					>
						{variant.name}
					</button>
					{#if variant.showDetails}
						<div class="item mt-4">
							<div class="my-2">{@html variant.description}</div>
							<p class="mt-4">Run the command below in the <strong>Proxmox VE Shell</strong>.</p>
							<div class="relative mt-2 rounded-lg bg-gray-800 p-4 text-white">
								<button
									class="absolute right-2 top-2 rounded bg-blue-500 px-2 py-1 font-bold text-white hover:bg-blue-700"
									on:click={() => copyToClipboard(`bash -c "$(wget -qLO - ${variant.script_url})"`)}
									>Copy</button
								>
								<code class="block whitespace-pre-wrap"
									>{`bash -c "$(wget -qLO - ${variant.script_url})"`}</code
								>
							</div>
						</div>
					{/if}
				</li>
			{/each}
		</ul>
	{/if}
</div>
