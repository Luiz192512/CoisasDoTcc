<script>
    import { onMount } from 'svelte';
    import PixPayment from './PixPayment.svelte'; // Certifique-se de que o caminho do arquivo esteja correto

    let paymentMethod = 'Pix';
    let quantity = 1;
    let unitPrice = 4.53;
    let totalPrice = unitPrice * quantity;

    // Estado para controlar a página atual
    let currentPage = 'order'; // 'order' ou 'pix'

    onMount(() => {
        totalPrice = unitPrice * quantity;
    });

    function removeProduct() {
        quantity = 0;
    }

    function handlePayment() {
        if (paymentMethod === 'Pix') {
            currentPage = 'pix'; // Muda para a página de pagamento via Pix
        }
    }

    function goBack() {
        currentPage = 'order'; // Volta para a página do pedido
    }
</script>

{#if currentPage === 'order'}
    <div class="p-4">
        <div class="flex justify-between mb-4">
            <h1 class="text-xl font-semibold">Pedido</h1>
        </div>

        <!-- Opções de pagamento -->
        <div class="flex space-x-2 mb-4">
            <button
                class="w-full border py-2 rounded-lg"
                style:background-color={paymentMethod === 'Pix' ? '#C67C4E' : 'transparent'}
                class:text-white={paymentMethod === 'Pix'}
                on:click={() => paymentMethod = 'Pix'}
            >
                Pix
            </button>
            <button
                class="w-full border py-2 rounded-lg"
                style:background-color={paymentMethod === 'Dinheiro' ? '#C67C4E' : 'transparent'}
                class:text-white={paymentMethod === 'Dinheiro'}
                on:click={() => paymentMethod = 'Dinheiro'}
            >
                Dinheiro
            </button>
            <button
                class="w-full border py-2 rounded-lg"
                style:background-color={paymentMethod === 'Cartão' ? '#C67C4E' : 'transparent'}
                class:text-white={paymentMethod === 'Cartão'}
                on:click={() => paymentMethod = 'Cartão'}
            >
                Cartão
            </button>
        </div>

        <!-- Detalhes do produto -->
        {#if quantity > 0}
            <div class="flex items-center mb-4">
                <img src="https://via.placeholder.com/50" alt="Caffe Mocha" class="w-12 h-12 rounded-lg mr-4" />
                <div class="flex-1">
                    <h3 class="text-sm font-semibold">Caffe Mocha</h3>
                    <p class="text-xs text-gray-600">Deep Foam</p>
                </div>
                <div class="flex items-center space-x-2">
                    <button on:click={() => quantity = Math.max(1, quantity - 1)} class="border p-1 rounded">-</button>
                    <span>{quantity}</span>
                    <button on:click={() => quantity += 1} class="border p-1 rounded">+</button>
                </div>

                <!-- Mostrar ícone de lixeira quando a quantidade for 1 -->
                {#if quantity === 1}
                    <button on:click={removeProduct} class="text-red-500 ml-4">
                        =
                    </button>
                {/if}
            </div>
        {/if}

        <!-- Mensagem de retirada quando for Dinheiro -->
        {#if paymentMethod === 'Dinheiro'}
            <p class="text-gray-600">Você irá retirar no local.</p>
        {/if}

        <!-- Opções de pagamento adicionais quando for Cartão -->
        {#if paymentMethod === 'Cartão'}
            <div class="mt-4">
                <h2 class="font-semibold">Escolha o tipo de pagamento</h2>
                <button class="border rounded-lg py-1 px-4 mt-2" on:click={() => alert('Opção de Débito selecionada.')}>
                    DÉBITO
                </button>
                <button class="border rounded-lg py-1 px-4 mt-2" on:click={() => alert('Opção de Crédito selecionada.')}>
                    CRÉDITO
                </button>
                <button class="border rounded-lg py-1 px-4 mt-2 bg-orange-500 text-white" on:click={() => alert('Cadastrar cartão!')}>
                    Cadastrar Cartão
                </button>
            </div>
        {/if}

        <!-- Resumo do pagamento -->
        {#if quantity > 0}
            <div class="mb-4">
                <h2 class="font-semibold">1 Discount is Applied</h2>
            </div>

            <div class="mb-4">
                <h2 class="font-semibold">Payment Summary</h2>
                <div class="flex justify-between">
                    <p class="text-gray-600">Price</p>
                    <p>R$ {totalPrice.toFixed(2)}</p>
                </div>
            </div>

            <div class="mt-4">
                <button class="bg-orange-500 text-white w-full py-2 rounded-lg" on:click={handlePayment}>Order</button>
            </div>
        {/if}

        {#if quantity === 0}
            <p class="text-center text-gray-600 mt-4">Nenhum item no carrinho.</p>
        {/if}
    </div>
{:else if currentPage === 'pix'}
    <PixPayment on:back={goBack} />
{/if}

<style>
    /* Removendo o seletor não utilizado */
</style>
