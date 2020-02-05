<script type="text/javascript">
	import Navbar from './Navbar.svelte'
	import Main from './Main.svelte'
	import Card from './Card.svelte'
	import Notification from './Notification.svelte'

	let cards = []
	let error = false

	const addperson = (e) => {
		if (e.detail.cardholder.length == 0 || e.detail.cardnumber.length == 0 || e.detail.cvv.length == 0 || e.detail.expiry.length == 0) {
			error = true
		}else{
		e.detail.expiry = e.detail.expiry.slice(0,2)+'/'+e.detail.expiry.slice(8,10)
		e.detail.cardnumber = e.detail.cardnumber.toString()
		e.detail.cardnumber = e.detail.cardnumber.replace(/(\d{4})/g, '$1 ').replace(/(^\s+|\s+$)/,'')
	    const newPerson = e.detail;
	    cards = [...cards, newPerson];

	    error = false
	}
  };
	
</script>

<Navbar />

<div class="container">
  <div class="bx--grid">
	  <div class="bx--row">
	    <div class="bx--col-lg-6">
	    	{#if error}
	    		<Notification />
	    	{/if}
			<Main on:addperson = {addperson} />

	    </div>
	    <div class="bx--col">
	      
	      	{#if cards.length === 0} <h3>No Cards available</h3>
				{:else}
					{#each cards as card}
					  <Card cardnumber = {card.cardnumber} cardholder = {card.cardholder} expiry = {card.expiry} cvv = {card.cvv}/>
					{/each}
			{/if}

	    </div>
	  </div>

  </div>
</div>

<style type="text/css">
  .container{
    padding-top: 5em;
  }
  h3{
    text-align: center;
  }
</style>