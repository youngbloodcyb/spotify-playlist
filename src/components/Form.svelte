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
  
<form class="form-container bg-white rounded-none py-12 px-5 text-center w-[350px] h-[400px] flex flex-col justify-center" on:submit={handleSubmit}>
{#if active_step == 'Info'}
    <InputField label={'Name'} bind:value={formData.name}/>
    <InputField label={'Surname'} bind:value={formData.surname}/>
    <InputField label={'Email'} bind:value={formData.email}/>
    <InputField type={'password'} label={'Password'} bind:value={formData.password}/>
{:else if active_step == 'Address'}
    <InputField label={'Address'} bind:value={formData.address}/>
    <InputField label={'City'} bind:value={formData.city}/>
    <InputField label={'Country'} bind:value={formData.country}/>
    <InputField label={'Postcode'} bind:value={formData.postcode}/>
{:else if active_step == 'Payment'}
    <InputField label={'Account Name'} bind:value={formData.account_name}/>
    <InputField label={'Card No'} bind:value={formData.card_no}/>
{:else if active_step == 'Confirmation'}
    <div class="text-center">
    <h2>Thank you for choosing us</h2>
    <button class="py-3 px-6 transition-all duration-300 ease-in-out font-mono border-black border-solid border-2 rounded-none  hover:shadow-[-6px_6px_#000] block md:inline-block my-4 hover:text-orange-600 hover:text-bold w-full sm:w-40 text-center">Finish </button>
    </div>
{/if}
</form>