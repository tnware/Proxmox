<script>
	import * as Accordion from '$lib/components/ui/accordion';
	import AppDetails from './AppDetails.svelte';
	import ProjectBadges from './ProjectBadges.svelte';
	import * as Dialog from '$lib/components/ui/dialog';
	let selectedApp = {};
	let dialogOpen = false;
	let appsData = {
		apps: [
			{
				name: 'Proxmox Backup Tool',
				description:
					'This script provides options for managing Proxmox VE repositories, including disabling the Enterprise Repo, adding or correcting PVE sources, enabling the No-Subscription Repo, adding the test Repo, disabling the subscription nag, updating Proxmox VE, and rebooting the system.',
				category: 'Proxmox VE Tools',
				type: 'script',
				script_url: 'https://example.com/proxmox-backup-tool',
				image_url: '/img/logo/proxmox.png',
				date_added: '2023-03-01',
				last_updated: '2023-03-15'
			},
			{
				name: 'NGINX Reverse Proxy LXC Container',
				description:
					'A <strong>reverse proxy</strong> server that can be used to route traffic to different services within your <em>Proxmox VE</em> environment.',
				category: 'Servers',
				type: 'lxc',
				script_url: 'https://example.com/nginx-reverse-proxy-lxc',
				image_url: '/img/logo/nginx.png',
				date_added: '2023-03-01',
				last_updated: '2023-03-15',
				variants: [
					{
						name: 'NGINX Reverse Proxy LXC Container (Debian)',
						description:
							'A default <strong>NGINX reverse proxy</strong> server with basic configuration settings.',
						script_url: 'https://example.com/nginx-reverse-proxy-lxc-default'
					},
					{
						name: 'NGINX Reverse Proxy LXC Container (Alpine)',
						description:
							'An advanced <strong>NGINX reverse proxy</strong> server with additional configuration settings.',
						script_url: 'https://example.com/nginx-reverse-proxy-lxc-advanced'
					}
				]
			}
		]
	};

	function getCategories(apps) {
		const categories = apps.map((app) => app.category);
		return [...new Set(categories)]; // Return unique categories
	}

	function selectApp(app) {
		selectedApp = app;
		dialogOpen = true;
	}

	let categories = getCategories(appsData.apps);
</script>

<header class="bg-neutral-800 py-6 text-white">
	<div class="container mx-auto flex flex-col items-center">
		<a
			id="a-title"
			href="/Proxmox/"
			class="flex items-center text-3xl font-bold transition duration-300 ease-in-out hover:text-neutral-300"
		>
			<img src="https://via.placeholder.com/32" alt="Proxmox Logo" class="mr-2 h-8 w-8" />
			Proxmox VE Helper-Scripts
		</a>

		<h2 class="mt-2 text-xl text-neutral-400">
			Scripts for Streamlining Your Homelab with Proxmox VE
		</h2>
		<section id="downloads" class="mt-4">
			<a
				href="https://github.com/tnware/Proxmox"
				class="inline-block rounded bg-blue-600 px-4 py-2 font-semibold text-white shadow-lg transition-shadow duration-300 hover:bg-blue-700 hover:shadow"
			>
				<svg
					class="-mt-1 mr-2 inline h-5 w-5"
					fill="currentColor"
					viewBox="0 0 24 24"
					xmlns="http://www.w3.org/2000/svg"
					><path
						d="M12 0C5.373 0 0 5.373 0 12c0 5.302 3.438 9.8 8.207 11.387.6.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.108-.775.418-1.305.762-1.604-2.665-.305-5.467-1.332-5.467-5.93 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.3 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.046.138 3.003.404 2.29-1.552 3.297-1.23 3.297-1.23.653 1.652.242 2.873.118 3.176.768.84 1.235 1.91 1.235 3.221 0 4.61-2.807 5.623-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.8.576C20.565 21.795 24 17.3 24 12c0-6.627-5.373-12-12-12z"
					/></svg
				>
				View on GitHub
			</a>
		</section>
	</div>
</header>

<div class="container mx-auto mt-4 space-y-4 px-4">
	<div class="container mx-auto mt-4 space-y-4 px-4">
		<div class="flex flex-col items-center space-y-4">
			<div class="flex items-center space-x-2 rounded-lg bg-neutral-800 p-4 shadow-lg">
				<input
					type="text"
					value=""
					placeholder="Search..."
					class="focus:shadow-outline rounded border px-4 py-2 leading-tight text-gray-700 focus:outline-none"
				/>
				<button class="rounded bg-blue-500 px-4 py-2 font-bold text-white hover:bg-blue-700"
					>Clear Search</button
				>
			</div>
			<ProjectBadges></ProjectBadges>
		</div>
	</div>
	<h1>Grid View</h1>
	<div class="container mx-auto mt-4 px-4">
		<div class="-m-2 flex flex-wrap">
			{#each appsData.apps as app}
				<div class="w-1/2 p-2 sm:w-1/3 md:w-1/4" on:click={selectApp(app)}>
					<!-- Set a minimum and maximum height to ensure consistency across grid items -->
					<div
						class="flex max-h-[200px] min-h-[200px] flex-col items-center space-y-2 rounded-lg bg-neutral-800 p-4 shadow-lg hover:bg-neutral-700"
					>
						<!-- Image already constrained to w-24 h-24, ensuring uniform size -->
						<img src={app.image_url} alt={app.name} class="h-24 w-24 rounded-sm object-cover" />
						<h3 class="text-lg font-semibold text-white">{app.name}</h3>
					</div>
				</div>
			{/each}
		</div>
	</div>

	<h1>Accordion View</h1>
	<Accordion.Root>
		{#each categories as category}
			<Accordion.Item value={category} class="my-2 rounded-lg bg-neutral-800 shadow-lg">
				<Accordion.Trigger
					class="flex cursor-pointer items-center justify-between rounded-t-lg p-4 text-lg font-semibold text-neutral-300 transition duration-300 ease-in-out hover:bg-neutral-700"
				>
					{category}
				</Accordion.Trigger>
				<Accordion.Content class="rounded-b-lg bg-neutral-800 p-6">
					<ul class="space-y-2">
						{#each appsData.apps.filter((app) => app.category === category) as app}
							<li>
								<button
									on:click={() => (app.showDetails = !app.showDetails)}
									class="cursor-pointer text-lg font-bold hover:underline"
								>
									{app.name}
								</button>
								{#if app.showDetails}
									<AppDetails {app}></AppDetails>
								{/if}
							</li>
						{/each}
					</ul>
				</Accordion.Content>
			</Accordion.Item>
		{/each}
	</Accordion.Root>
</div>

<Dialog.Root bind:open={dialogOpen}>
	<Dialog.Content class="min-w-[900px]">
		<AppDetails bind:app={selectedApp} />
	</Dialog.Content>
</Dialog.Root>
