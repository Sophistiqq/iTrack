<script lang="ts">
    import type { PageData } from "./$types";

    let { data }: { data: PageData } = $props();
</script>

<nav>
    <a href="/">Logout</a>
</nav>

<style>

    nav {
        display: flex;
        justify-content: flex-end;
        
    }
</style>