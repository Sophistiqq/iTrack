<script lang="ts">
	import { goto } from "$app/navigation";
	import { json } from "@sveltejs/kit";
	import { isAuthenticated } from "../stores/authStore";
	import {
		AppleSolid,
		FacebookSolid,
		GoogleSolid,
	} from "flowbite-svelte-icons";
	import type { SignpostBig } from "lucide-svelte";
	import { onMount } from "svelte";
	import { writable } from "svelte/store";

	onMount(() => {
		fetchData();
	});

	async function fetchData() {
		const res = await fetch("http://192.168.1.31:3000/", {
			method: "POST",
		});
		const data = await res.json();
		console.log(data.message);
	}

	let email: string = $state("");
	let password: string = $state("");

	async function sendLogin(e: Event) {
		e.preventDefault();
		try {
			const res = await fetch("http://192.168.1.31:3000/login", {
				headers: {
					"Content-Type": "application/json",
				},
				method: "POST",
				body: JSON.stringify({ email, password }),
			});
			const data = await res.json();
			if (data.success == true) {
				goto("/logout");
			}
		} catch (e) {
			console.error(e);
		}
	}

	function handleLogin() {
		if (email === "email" && password === "password") {
			isAuthenticated.set(true);
			goto("/");
		} else {
			alert("Invalid Credentials");
		}
		goto("/logout");
	}
</script>

<div class="container">
	<div class="left">
		<div class="title">
			<h1>iTrack</h1>
		</div>
		<div class="hi">
			<h1>Hi There!</h1>
		</div>
		<div id="temp">
			<h2>Enter your email and password.</h2>
		</div>

		<form onsubmit={sendLogin}>
			<input
				bind:value={email}
				type="email"
				placeholder="Enter your email"
				required
				id="email"
				autocomplete="email"
			/>
			<input
				type="password"
				placeholder="Enter your password"
				required
				id="passwords"
				bind:value={password}
			/>
			<div class="rememberme">
				<p>
					<input type="checkbox" name="" id="rememberme" /> Remember me
				</p>
			</div>

			<!-- <button id="continue"><a href="/logout">Continue</a></button> -->
			<button id="continue" onclick={sendLogin}>Continue</button>
		</form>

		<p id="or">or</p>
		<div class="buttons">
			<!-- <button>
				<GoogleSolid />
			</button>
			<button>
				<AppleSolid />
			</button>
			<button>
				<FacebookSolid />
			</button> -->
		</div>
		<p id="needanaccount">
			Create an account?
			<a href="/register">Sign up</a>
		</p>
	</div>

	<div class="right">
		<img src="3615781.jpg" alt="" />
	</div>
</div>

<style>
	.container {
		display: flex;
		justify-content: center;
		/* border: 1px solid green; */
		align-items: center;
		min-width: 100vw;
		height: 100vh;
		font-family: proxima-nova, sans-serif;
		font-style: normal;
	}

	.container .left {
		width: 75%;
		height: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		padding-inline: 15%;
		gap: 0.5rem;
		/* border: 1px solid red; */
		background: rgb(0, 128, 0);
		background: linear-gradient(
			0deg,
			rgba(0, 128, 0, 1) 0%,
			rgba(255, 158, 42, 1) 80%
		);
	}

	.container .right {
		/* border: 1px solid blue; */
		width: 100%;
		img {
			max-width: 85%;
		}
	}

	.title h1 {
		/* border: 1px solid rgb(87, 87, 87); */
		color: #ffffff;
		font-weight: bold;
		font-size: 5rem;
		gap: 5rem;
	}

	.hi {
		/* border: 1px solid red; */
		font-size: 2rem;
		font-weight: bold;
		color: #ffffff;
		/* padding: 0.5rem 0; */
	}

	#temp {
		/* border: 1px solid black; */
		color: #ffffff;
		font-size: 1rem;
	}

	#email {
		border-radius: 0.5rem;
		background-color: #ffffff;
	}

	#email:hover {
		border: 1px solid #008000;
	}

	#passwords {
		border-radius: 0.5rem;
		background-color: #ffffff;
	}

	#passwords:hover {
		border: 1px solid #008000;
	}

	.rememberme {
		p {
			/* border: 1px solid black; */
			color: #ffffff;
		}
	}

	#rememberme {
		border-radius: 0.3rem;
		background-color: #ffffff;
	}

	#continue {
		background-color: #008000;
		padding: 0.5rem 1rem;
		border-radius: 0.5rem;
		font-weight: bold;
		color: white;
		&:active {
			transform: scale(0.9);
		}
	}

	#or {
		display: flex;
		justify-content: center;
		color: #ffffff;
	}

	form {
		/* border: 1px solid red; */
		display: flex;
		flex-direction: column;
		gap: 0.5rem;
	}

	/* .buttons {
		display: flex;
		justify-content: space-between;
		gap: 1rem;
		color: #008000;
		button {
			border: 1px solid gray;
			width: 100%;
			display: flex;
			padding: 0.3rem 0.75rem;
			justify-content: center;
			border-radius: 0.5rem;
			background-color: #ffffff;
		}
	} */

	#needanaccount {
		color: #ffffff;
		a {
			font-weight: bold;
		}
		a:hover {
			text-decoration: underline;
		}
	}
</style>
