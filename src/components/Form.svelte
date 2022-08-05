<script>
    import InputField from '../components/InputField.svelte';

    export let active_step;
    let formData = {
      name: '',
      surname: '',
      email: '',
      password: '',
      address: '',
      city: '',
      country: '',
      postcode: '',
      account_name: '',
      card_no: ''
    }
  
    const handleSubmit = () => {
      console.log("Your form data => ",formData)
    }
</script>
  
<form class="form-container bg-white rounded-none py-12 px-5 text-center w-[350px] h-[400px] flex flex-col justify-center font-mono" on:submit={handleSubmit}>
{#if active_step == 'Info'}
    <div class="typewriter">
        <p>
        This is a test.
        </p>
    </div>
    <InputField label={'Name'} bind:value={formData.name}/>
    <InputField label={'Surname'} bind:value={formData.surname}/>
    <InputField label={'Email'} bind:value={formData.email}/>
    <InputField type={'password'} label={'Password'} bind:value={formData.password}/>
{:else if active_step == 'Address'}
    <div class="typewriter">
        <p>
        This is a test.
        </p>
    </div>
    <InputField label={'Address'} bind:value={formData.address}/>
    <InputField label={'City'} bind:value={formData.city}/>
    <InputField label={'Country'} bind:value={formData.country}/>
    <InputField label={'Postcode'} bind:value={formData.postcode}/>
{:else if active_step == 'Payment'}
    <div class="typewriter">
        <p>
        This is a test.
        </p>
    </div>
    <InputField label={'Account Name'} bind:value={formData.account_name}/>
    <InputField label={'Card No'} bind:value={formData.card_no}/>
{:else if active_step == 'Confirmation'}
    <div class="typewriter">
        <p>
        This is a test.
        </p>
    </div>
    <div class="text-center">
    <h2>Thank you for choosing us</h2>
    <button class="py-3 px-6 transition-all duration-300 ease-in-out font-mono border-black border-solid border-2 rounded-none  hover:shadow-[-6px_6px_#000] block md:inline-block my-4 hover:text-orange-600 hover:text-bold w-full sm:w-40 text-center">Finish </button>
    </div>
{/if}
</form>

<style>
    .typewriter p {
        overflow: hidden; /* Ensures the content is not revealed until the animation */
        border-right: .15em solid rgb(234 88 12); /* The typwriter cursor */
        white-space: nowrap; /* Keeps the content on a single line */
        margin: 0; /* Gives that scrolling effect as the typing happens */
        letter-spacing: .15em; /* Adjust as needed */
        width: max-content;
        animation: 
            typing 3.5s steps(40, end),
            blink-caret .75s step-end infinite;
    }

    /* The typing effect */
    @keyframes typing {
        from { width: 0 }
        to { width: 100% }
    }

    /* The typewriter cursor effect */
    @keyframes blink-caret {
        from, to { border-color: transparent }
        50% { border-color: rgb(234 88 12); }
    }
</style>