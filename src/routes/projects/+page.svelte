<script>
    import { onMount } from "svelte";

    let projects = [];

    onMount(async () => {
        const response = await fetch(`https://api.github.com/users/imsern/repos`);
        const repos = await response.json();

        // Transform GitHub repo data to match your project structure
        projects = repos.map((repo) => ({
            title: repo.name,
            description: repo.description || "No description provided",
            buttonText: "View on GitHub",
            buttonURL: repo.html_url
        }));
    });
</script>

<template>
    <div class="min-h-screen bg-black text-orange-500 py-10">
        <div class="container mx-auto px-4">
            <h1 class="text-3xl font-bold text-center mb-10">My Projects</h1>

            {#if projects.length > 0}
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                    {#each projects as project}
                        <div class="rounded-lg p-6 shadow-lg bg-gray-800 text-white flex flex-col justify-between h-full">
                            <!-- Card Content -->
                            <div>
                                <h2 class="text-xl font-semibold mb-2">{project.title}</h2>
                                <p class="mb-4">{project.description}</p>
                            </div>
                            <!-- Button aligned to bottom-right -->
                            <div class="flex justify-end mt-auto">
                                <a href="{project.buttonURL}" target="_blank">
                                    <button class="btn bg-orange-500 hover:bg-orange-600 border-none">
                                        {project.buttonText}
                                    </button>
                                </a>
                            </div>
                        </div>
                    {/each}
                </div>
            {:else}
                <div class="text-center">
                    <p>Loading projects...</p>
                </div>
            {/if}
        </div>
    </div>
</template>

<style></style>