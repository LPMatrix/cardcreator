<script>
  import Card from './Card.svelte'
  import { createEventDispatcher } from 'svelte';
  const dispatcher = createEventDispatcher();

  let person = {
      cardnumber : "",
      cardholder : "",
      expiry : "",
      cvv : ""
    }

  const submit = (e) => {
      e.preventDefault();
      dispatcher("addperson", person);
      person = {
        cardnumber : "",
        cardholder : "",
        expiry : "",
        cvv : ""
      }
    }

  const remove = (e) => {
    cards = cards.filter(person => person.name !== e.detail);
  };
  
</script>

    <form on:submit = {submit}>
      <div class="bx--form-item">
        <div data-numberinput class="bx--number bx--number--helpertext full">
          <label for="number-input3" class="bx--label">Card Number</label>
          <div class="bx--form__helper-text">
            Enter 16 digit Card Number
          </div>
          <div class="bx--number__input-wrapper">
            <input id="number-input" type="number" min="0" bind:value={person.cardnumber}>
            <div class="bx--number__controls">
              <button aria-label="increase number input" class="bx--number__control-btn up-icon" type="button"
                aria-live="polite" aria-atomic="true">
                <svg focusable="false" preserveAspectRatio="xMidYMid meet" style="will-change: transform;" xmlns="http://www.w3.org/2000/svg" width="8" height="4" viewBox="0 0 8 4" aria-hidden="true"><path d="M0 4L4 0 8 4z"></path></svg>
              </button>
              <button aria-label="decrease number input" class="bx--number__control-btn down-icon" type="button"
                aria-live="polite" aria-atomic="true">
                <svg focusable="false" preserveAspectRatio="xMidYMid meet" style="will-change: transform;" xmlns="http://www.w3.org/2000/svg" width="8" height="4" viewBox="0 0 8 4" aria-hidden="true"><path d="M8 0L4 4 0 0z"></path></svg>
              </button>
            </div>
          </div>
        </div>

      </div>

      <div class="bx--form-item">
        <label for="text-input-3" class="bx--label">Card Holder</label>
        <div class="bx--form__helper-text">
          Enter Card Holder Name
        </div>
        <input id="text-input-3" type="text"
          class="bx--text-input"
          placeholder="Sanusi Mubaraq" bind:value={person.cardholder}>
      </div>

      <div class="bx--form-item">
        <div data-numberinput class="bx--number bx--number--helpertext full">
        <label for="text-input-3" class="bx--label">Expiry Date</label>
        <div class="bx--form__helper-text">
          Enter Card Expiry Date
        </div>
        <div data-date-picker data-date-picker-type="single"
          class="bx--date-picker bx--date-picker--single bx--date-picker--nolabel">
          <div class="bx--date-picker-container">
            <div class="bx--date-picker-input__wrapper">
              <input type="text" id="date-picker-3" class="bx--date-picker__input"
                 placeholder="mm/dd/yyyy" data-date-picker-input bind:value={person.expiry} />
              <svg focusable="false" preserveAspectRatio="xMidYMid meet" style="will-change: transform;" xmlns="http://www.w3.org/2000/svg" data-date-picker-icon="true" class="bx--date-picker__icon" width="16" height="16" viewBox="0 0 16 16" aria-hidden="true"><path d="M13,2h-2V1h-1v1H6V1H5v1H3C2.4,2,2,2.4,2,3v10c0,0.6,0.4,1,1,1h10c0.6,0,1-0.4,1-1V3C14,2.4,13.6,2,13,2z M13,13H3V6h10V13z M13,5H3V3h2v1h1V3h4v1h1V3h2V5z"></path></svg>
            </div>
          </div>
        </div>
      </div>
      </div>
      <div class="bx--form-item">
        <div data-numberinput class="bx--number bx--number--helpertext full">
          <label for="number-input3" class="bx--label">CVV</label>
          <div class="bx--form__helper-text">
            Enter 3 digit CVV
          </div>
          <div class="bx--number__input-wrapper">
            <input id="number-input3" type="number" min="0" bind:value={person.cvv}>
            <div class="bx--number__controls">
              <button aria-label="increase number input" class="bx--number__control-btn up-icon" type="button"
                aria-live="polite" aria-atomic="true">
                <svg focusable="false" preserveAspectRatio="xMidYMid meet" style="will-change: transform;" xmlns="http://www.w3.org/2000/svg" width="8" height="4" viewBox="0 0 8 4" aria-hidden="true"><path d="M0 4L4 0 8 4z"></path></svg>
              </button>
              <button aria-label="decrease number input" class="bx--number__control-btn down-icon" type="button"
                aria-live="polite" aria-atomic="true">
                <svg focusable="false" preserveAspectRatio="xMidYMid meet" style="will-change: transform;" xmlns="http://www.w3.org/2000/svg" width="8" height="4" viewBox="0 0 8 4" aria-hidden="true"><path d="M8 0L4 4 0 0z"></path></svg>
              </button>
            </div>
          </div>
        </div>

      </div>

      <div class="bx--form-item">
        <button class="bx--btn bx--btn--primary" type="submit">Create</button>
      </div>

  </form>


<style>
  .tile{
    margin-top: 1em;
    text-align: center;
  }
  .bx--btn{
    margin-top: 1em;
  }
  .full{
    width: 100% !important;
  }
</style>