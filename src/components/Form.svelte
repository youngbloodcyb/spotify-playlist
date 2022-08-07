<script>
    import InputField from '../components/InputField.svelte';
    import Select from 'svelte-select';

    export let active_step;
    let formData = {
      genre: '',
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

    const genres = [
        "acoustic",
        "afrobeat",
        "alt-rock",
        "alternative",
        "ambient",
        "anime",
        "black-metal",
        "bluegrass",
        "blues",
        "bossanova",
        "brazil",
        "breakbeat",
        "british",
        "cantopop",
        "chicago-house",
        "children",
        "chill",
        "classical",
        "club",
        "comedy",
        "country",
        "dance",
        "dancehall",
        "death-metal",
        "deep-house",
        "detroit-techno",
        "disco",
        "disney",
        "drum-and-bass",
        "dub",
        "dubstep",
        "edm",
        "electro",
        "electronic",
        "emo",
        "folk",
        "forro",
        "french",
        "funk",
        "garage",
        "german",
        "gospel",
        "goth",
        "grindcore",
        "groove",
        "grunge",
        "guitar",
        "happy",
        "hard-rock",
        "hardcore",
        "hardstyle",
        "heavy-metal",
        "hip-hop",
        "holidays",
        "honky-tonk",
        "house",
        "idm",
        "indian",
        "indie",
        "indie-pop",
        "industrial",
        "iranian",
        "j-dance",
        "j-idol",
        "j-pop",
        "j-rock",
        "jazz",
        "k-pop",
        "kids",
        "latin",
        "latino",
        "malay",
        "mandopop",
        "metal",
        "metal-misc",
        "metalcore",
        "minimal-techno",
        "movies",
        "mpb",
        "new-age",
        "new-release",
        "opera",
        "pagode",
        "party",
        "philippines-opm",
        "piano",
        "pop",
        "pop-film",
        "post-dubstep",
        "power-pop",
        "progressive-house",
        "psych-rock",
        "punk",
        "punk-rock",
        "r-n-b",
        "rainy-day",
        "reggae",
        "reggaeton",
        "road-trip",
        "rock",
        "rock-n-roll",
        "rockabilly",
        "romance",
        "sad",
        "salsa",
        "samba",
        "sertanejo",
        "show-tunes",
        "singer-songwriter",
        "ska",
        "sleep",
        "songwriter",
        "soul",
        "soundtracks",
        "spanish",
        "study",
        "summer",
        "swedish",
        "synth-pop",
        "tango",
        "techno",
        "trance",
        "trip-hop",
        "turkish",
        "work-out",
        "world-music"
    ]
</script>
  
<form class="form-container bg-white rounded-none py-12 px-5 text-center w-[350px] h-[400px] flex flex-col justify-center font-mono" on:submit={handleSubmit}>
{#if active_step == 'Info'}
    <label class="text-left" for="genre">Genre:</label>
    <Select items={genres} bind:value={formData.genre}></Select>
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

