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

v                  <div class="item mt-4 bg-neutral-700 rounded-xl shadow-lg p-6">
    <p class="flex justify-center">
      <img src={app.image_url} alt={app.name} class="h-48"/>
    </p>
    <h1 class="text-3xl font-semibold text-center my-2">{app.name}</h1>
    <div class="text-sm text-center text-gray-500">
        Added: {formatDate(app.date_added)} | Last Updated: {formatDate(app.last_updated)}
      </div>
    <div class="my-2 text-lg">{@html app.description}</div>
    <p class="mt-4">Run the command below in the <strong>Proxmox VE Shell</strong>.</p>
    <div class="bg-gray-800 text-white p-4 rounded-lg mt-2 relative">
      <button class="absolute top-2 right-2 bg-blue-500 hover:bg-blue-700 text-white font-bold py-1 px-2 rounded"
              on:click={() => copyToClipboard(`bash -c "$(wget -qLO - ${app.script_url})"`)}>Copy</button>
      <code class="block whitespace-pre-wrap">{`bash -c "$(wget -qLO - ${app.script_url})"`}</code>
    </div>
    <!-- <p class="mt-2">It is recommended to answer “yes” (y) to all options presented during the process.</p> -->
    {#if app.type == 'lxc'}<h3 align="center" id="heading">⚡ Default Settings:  1GB RAM - 4GB Storage - 2vCPU ⚡</h3>{/if}
    {#if app.variants && app.variants.length > 0}
      <h2 class="text-xl font-semibold mt-4">Variants</h2>
      <ul class="space-y-2">
        {#each app.variants as variant}
          <li>
            <button on:click={() => (variant.showDetails = !variant.showDetails)} 
                    class="text-lg font-bold cursor-pointer hover:underline">
              {variant.name}
            </button>
            {#if variant.showDetails}
              <div class="item mt-4">
                <div class="my-2">{@html variant.description}</div>
                <p class="mt-4">Run the command below in the <strong>Proxmox VE Shell</strong>.</p>
                <div class="bg-gray-800 text-white p-4 rounded-lg mt-2 relative">
                  <button class="absolute top-2 right-2 bg-blue-500 hover:bg-blue-700 text-white font-bold py-1 px-2 rounded"
                          on:click={() => copyToClipboard(`bash -c "$(wget -qLO - ${variant.script_url})"`)}>Copy</button>
                  <code class="block whitespace-pre-wrap">{`bash -c "$(wget -qLO - ${variant.script_url})"`}</code>
                </div>
              </div>
            {/if}
          </li>
        {/each}
      </ul>
    {/if}
</div>