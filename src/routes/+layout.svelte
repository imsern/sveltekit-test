<script>
    let navItems = [
        { name: "Home", href: "/" },
        { name: "About", href: "/about" },
        { name: "Projects", href: "/projects" },
        { name: "Contact", href: "/contact" },
    ];
</script>

<nav class="bg-gray-950 text-white p-4">
    <ul class="flex space-x-4">
        {#each navItems as item}
            <li>
<a href={item.href} class="text-lg hover:text-orange-500">{item.name}</a>
            </li>
        {/each}
    </ul>
</nav>

<div>
    <slot></slot>
</div>