<script>
export let showModal = false;


export let isPromo =  false
export let message  = 'sign up for offers!';

</script>

{#if showModal}
<div class = 'backdrop' class:promo={isPromo} on:click|self style='cursor:pointer'>
    <div class="modal" style='cursor:default'>
        <p>{message}</p>
    </div>
</div>
{/if}

<style>

.backdrop {
width: 100%;
height: 100%;
padding: 0;
position: fixed;
background: rgba(0,0,0,0.9);
}

.modal {
    padding: 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: 10% auto;
    text-align: center;
    background: #fff;
    }

.promo .modal{
    background: crimson;
    color: white;
    font-weight: 900;
    border: solid 2px #fff
}



</style>