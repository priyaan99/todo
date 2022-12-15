<script> 
    let quantity = 0;

    function add_to_cart() {
        quantity += 1;

        inventory = [...inventory, quantity];
    }

    let inventory = [1, 2, 3];
    let price = 100;

    $: remaining = 10 - quantity;
    $: total_cost = price * quantity;
</script>

<p>Count {quantity}</p>
<button on:click={add_to_cart}>Add to Cart</button>

<p>In inventory {inventory}</p>
<p>Remaining: {remaining}</p>
<h3>Total cost: {total_cost}</h3>

<style>
    
</style>
