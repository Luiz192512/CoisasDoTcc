<script>
    import CoffeeDetails from './CoffeeDetails.svelte';
    import OrderPage from './OrderPage.svelte';
    
    let currentPage = 'details';

    function goToOrder() {
        currentPage = 'order';
    }

    function goToDetails() {
        currentPage = 'details';
    }
</script>

<main class="p-4">
    {#if currentPage === 'details'}
        <CoffeeDetails />
        <button on:click={goToOrder} class="bg-orange-500 text-white py-2 px-4 mt-4 rounded-lg">Go to Order Page</button>
    {:else if currentPage === 'order'}
        <OrderPage />
        <button on:click={goToDetails} class="bg-orange-500 text-white py-2 px-4 mt-4 rounded-lg">Back to Coffee Details</button>
    {/if}
</main>


<svelte:head>
<link rel="stylesheet" href="https://unpkg.com/tailwindcss@2.2.19/dist/tailwind.min.css"/>
</svelte:head>
