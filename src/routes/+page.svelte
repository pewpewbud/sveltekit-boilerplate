<script>
	import Counter from './Counter.svelte';
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcome_fallback from '$lib/images/svelte-welcome.png';
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<h1>
		<span class="welcome">
			<picture>
				<source srcset={welcome} type="image/webp" />
				<img src={welcome_fallback} alt="Welcome" />
			</picture>
		</span>

		to your new<br />SvelteKit app
	</h1>

	<h2>
		try editing <strong>src/routes/+page.svelte</strong>
	</h2>

	<Counter />
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>

<template>
<button class="dupe">Duplicate Card</button>
<button class="color-change">Change Color</button>
<button class="title-change">Change Title</button>
<button class="delete-dupe">Delete card</button>

<div class="wrapper">
  <div class="card">
      <img src="https://destiny.wiki.gallery/images/thumb/2/27/CrotaEndArt.jpg/1200px-CrotaEndArt.jpg" alt="Image depicting a shadow of a guardian slashing down a shadow of Crota, son of Oryx, whilst standing in Crota's throne room." style="max-width: 400px">
      <div class="container">
        <h2>Crotas End</h2>
        <details>
          <p>Crota's soul may have been banished from our world, and his brood all but demolished, but Crota himself still remains. To end this threat once and for all, a new team of six Guardians needs to enter the deepest pit of the Hellmouth and infiltrate his realm, the Oversoul Throne.</p>
        </details>
      </div>
    </div>
  </div>
</div>
</template>

</style>
/* Style button on hover and focus */
.dupe:hover, .dupe:focus {
  background-color: green;
}

.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 2); /*shadows*/
  transition: 0.3s;
  width: 500px;
  border: solid green;
  display: inline-block;
  margin: 8px; /* spacing between the cards */
  vertical-align: top;
  box-sizing: border-box; /* Padding and borders in the width */
  background-color: white;
  text-align: center;
}

/* Preventing layout issues */
.wrapper::after {
  display: flex;
  clear: both;
}

/* Mouse-over shadow & color */
.card:hover {
  box-shadow: 0 16px 24px 0 rgba(0, 0, 0, 15);
  background-color: #ddedd3;
}

/* Padding inside the card container */
.container {
  padding: 8px 16px;
  border: 5px double lightgreen;
  margin: 1em;
}

/* Code for button: */
.btn-wrapper {
  margin: 24 px auto;
}
.btn-wrapper button {
  font-size: 24px;
  color: blue;
  background-color: white;
}
.btn-wrapper button:hover {
  color: white;
  background-color: blue;
}

/* scaling code */

@media screen and (max-width: 800px) {
  button {
    display: none;
  }
}
@media screen and (max-width: 500px) {
  div {
    transform: scale(0.9);
  }
  img {
    width: 70%;
  }
}

.colorChanged {
  background-color: green;
}
</style>

<script>
// create dupe
document.querySelector(".dupe").addEventListener("click", (e) => {
  // Clone the first card
  const firstCard = document.querySelector(".card");
  const clonedCard = firstCard.cloneNode(true);
  // Append the cloned card to the wrapper
  document.querySelector(".wrapper").appendChild(clonedCard);
  //delete dupe
  document.querySelector(".delete-dupe").addEventListener("click", (e) => {
    document.querySelector(".wrapper").removeChild(clonedCard);
  });
});
//change color
document.querySelector(".color-change").addEventListener("click", (e) => {
  document.querySelector(".card").classList.toggle("colorChanged");
});
//change title
document.querySelector(".title-change").addEventListener("click", (e) => {
  document.querySelector(".card h2").textContent = "Something Else";
});
</script>
