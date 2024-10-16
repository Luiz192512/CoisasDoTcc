<script>
    let selectedSize = 'M';
</script>

<div class="p-4">
    <div class="text-center">
        <img src="https://media.istockphoto.com/id/186823058/pt/foto/x%C3%ADcara-de-caf%C3%A9-tra%C3%A7ado-de-recorte-inclu%C3%ADdo.jpg?s=2048x2048&w=is&k=20&c=eAT6Rhytf60p6Mi1gg73NayQAKxnuqqmTwNONwR6JiI=" alt="Café" class="rounded-lg mb-4 h-64 object-cover" />
    </div>
    <div class="flex justify-between items-center mb-2">
        <h1 class="text-xl font-semibold">Café</h1>
    </div>
    <div class="text-gray-600 text-sm mb-4">
        <p>Hot</p>
    </div>
    <div class="mb-4">
        <h2 class="font-semibold mb-2">Descrição</h2>
        <p class="text-sm text-gray-600">
            A cappuccino is an approximately 150 ml (5 oz) beverage, with 25 ml of espresso coffee and 85ml of fresh milk.
            <span class="text-orange-500 font-semibold cursor-pointer">Read More</span>
        </p>
    </div>
    <div class="mb-4">
        <h2 class="font-semibold mb-2">Size</h2>
        <div class="flex space-x-2">
            {#each ['S', 'M', 'L'] as size}
                <button
                    class="border rounded-lg py-1 px-4 text-sm"
                    style:background-color={size === selectedSize ? '#C67C4E' : 'transparent'}
                    class:text-white={size === selectedSize}
                    on:click={() => selectedSize = size}
                >
                    {size}
                </button>
            {/each}
        </div>
    </div>
    <div class="flex justify-between items-center mt-4">
        <div class="text-xl font-semibold">R$ 4.53</div>
        <button class="bg-orange-500 text-white py-2 px-6 rounded-lg">Buy Now</button>
    </div>
</div>
