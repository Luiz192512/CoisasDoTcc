<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher(); // Adicionado para despachar eventos

    let cpf = '';

    function generateQRCode() {
        alert(`QR Code gerado para o CPF: ${cpf}`);
        // Aqui você pode integrar com uma API que gera QR Codes
    }
</script>

<div class="p-4">
    <h1 class="text-xl font-semibold mb-4">Pagamento via Pix</h1>
    
    <div class="mb-4">
        <label for="cpf" class="block text-sm font-medium text-gray-700">Digite seu CPF:</label>
        <input
            type="text"
            id="cpf"
            bind:value={cpf}
            class="mt-1 block w-full border border-gray-300 rounded-md shadow-sm p-2"
            placeholder="000.000.000-00"
        />
    </div>

    <button
        class="bg-orange-500 text-white py-2 px-4 rounded-lg"
        on:click={generateQRCode}
    >
        Gerar QR Code
    </button>

    <!-- Exibir o QR Code -->
    <div class="mt-4">
        {#if cpf}
            <h2 class="font-semibold mt-4">QR Code para pagamento:</h2>
            <img src="https://via.placeholder.com/200" alt="QR Code" class="mt-2" />
        {/if}
    </div>

    <!-- Botão para voltar -->
    <button class="mt-4 text-blue-500" on:click={() => dispatch('back')}>
        Voltar
    </button>
</div>
