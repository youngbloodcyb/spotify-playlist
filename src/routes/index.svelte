<script>
    import Test from "../components/test.svelte";
    import { token, tokenExpired, appUrl } from "./stores.js";
    import { onMount } from "svelte";
  
  const client_id = "1f0ffce7c26a4370aa7f0a8df8f6b62b"; // Your client id

  function generateRandomString(length) {
    let text = "";
    const possible =
      "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";

    for (let i = 0; i < length; i++) {
      text += possible.charAt(Math.floor(Math.random() * possible.length));
    }
    return text;
  }

  const url = new URL("https://accounts.spotify.com/authorize?");
  const scope = "user-read-private user-read-email user-top-read";
  const state = generateRandomString(16);
  let rememberMe = true;
  $: params = new URLSearchParams({
    response_type: "token",
    show_dialog: !rememberMe, // Will show up on first sign-on regardless
    client_id,
    scope,
    redirect_uri: $appUrl,
    state,
  });
  $: loginLink = url + params;

  let user;

  async function getUserData() {
      
    const accessToken = $token;
    console.log("getting user data " + accessToken);
    if (accessToken) {
        console.log("Trying");
      const res = await fetch("https://api.spotify.com/v1/me", {
        headers: {
          Authorization: "Bearer " + accessToken,
        },
      });
      if (res.ok) {
        const data = await res.json();
        user = data;
      } else {
        tokenExpired.set(true);
      }
    }
  }

  onMount(getUserData);


</script>

<div class="w-full h-screen flex flex-row justify-center align-middle">
    <div class="w-10/12 my-16">
        <div>
            <h1 class="font-playfair text-8xl my-6">create a playlist<br> or something</h1>
            <p class="font-mono text-2xl text-orange-600 my-6 font-bold">Create a cool playlist by selecting stuff.</p>
        </div>
        {#if !$token}
        <div id="login">
          <a href={loginLink} class="py-3 px-6 transition-all duration-300 ease-in-out font-mono border-black border-solid border-2 rounded-none  hover:shadow-[-6px_6px_#000] block md:inline-block my-4 hover:text-orange-600 hover:text-bold w-full sm:w-40 text-center">Get started</a>
          <br />
          <div id="checkbox-container">
            <label id="checkbox-text" for="remember-me">Remember me?</label>
            <input
              id="checkbox-box"
              name="remember-me"
              type="checkbox"
              bind:checked={rememberMe}
            />
          </div>
        </div>
      {/if}
      {#if $token}
        {#if user}
        <div class="success">
            <button class="welcome-btn" on:click={collapseExpand}>
                Welcome, {user.display_name.split(" ")[0]}!
            </button>
        </div>
        {:else}
        <div class="success">
            <p>none of success</p>
            <!-- <button class="welcome-btn" on:click={collapseExpand}>
                Welcome, {user.display_name.split(" ")[0]}!
            </button> -->
        </div>
        {/if}
      {/if}
      {#if $tokenExpired}
        <section class="expired-token">
          <p>Token expired! Please log out and log back in again.</p>
          <a href={$appUrl}>
            <button>Logout</button>
          </a>
        </section>
      {/if}
      
  
    </div>
</div>

<style>
    input {
      padding: 0;
      margin: 0;
    }
    .success{
        height: 40px;
        width: 200px;

    }
  
    #login {
      margin: 2.5rem auto;
    }
  
  
    #checkbox-container {
      display: inline-flex;
      cursor: pointer;
      position: relative;
      align-items: center;
    }
  
    #checkbox-text {
      margin: 0 0.5rem 0 0;
    }
  
    #checkbox-box {
      overflow: hidden;
      height: 1em;
      width: 1em;
      margin-top: 0.15rem;
      border: 1px solid var(--light-1);
      outline: none;
      background-color: var(--dark-2);
      color: black;
      cursor: pointer;
      -webkit-appearance: initial;
      appearance: initial;
      position: relative;
    }
  
    #checkbox-box:checked:after {
      content: "\2714";
      padding: none;
      color: var(--light-1);
      position: absolute;
      left: 50%;
      top: 40%;
      -webkit-transform: translate(-50%, -50%);
      -moz-transform: translate(-50%, -50%);
      -ms-transform: translate(-50%, -50%);
      transform: translate(-50%, -50%);
    }
  
    .expired-token {
      font-size: 1.25rem;
    }
  </style>