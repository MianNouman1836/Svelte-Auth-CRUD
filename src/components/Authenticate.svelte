<script>
	let email = '';
	let password = '';
	let confirmPassword = '';
	let error = false;
	let register = false;

	function handleAuthenticate() {
		if (!email || !password || (register && !confirmPassword)) {
			error = true;
			return;
		}
	}
</script>

<div class="authContainer">
	<form>
		<h1>{register ? 'Register' : 'Login'}</h1>

		{#if error}
			<p class="error">The information you entered is not Correct</p>
		{/if}

		<label>
			<p class={email ? 'above' : 'center'}>Email</p>
			<input bind:value={email} type="email" placeholder="Email" />
		</label>

		<label>
			<p class={password ? 'above' : 'center'}>Password</p>
			<input bind:value={password} type="password" placeholder="Password" />
		</label>

		<label>
			<p class={confirmPassword ? 'above' : 'center'}>Confirm Password</p>
			<input bind:value={confirmPassword} type="password" placeholder="Confirm Password" />
		</label>

		<button type="button">Submit</button>
	</form>

	<div class="authOptions">
		<p>OR</p>

		{#if register}
			<div>
				<p>Already have an Account?</p>
				<p>Login</p>
			</div>
		{:else}
			<div>
				<p>Don't have an Account?</p>
				<p>Register</p>
			</div>
		{/if}
	</div>
</div>

<style>
	.authContainer {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		flex: 1;
		padding: 24px;
	}

	h1 {
		text-align: center;
		font-size: 3rem;
	}

	form {
		display: flex;
		flex-direction: column;
		gap: 14px;
		width: 400px;
		max-width: 100%;
		margin: 0 auto;
	}

	form label {
		position: relative;
		border: 1px solid navy;
		border-radius: 5px;
	}

	form input {
		width: 100%;
		border: none;
		background: transparent;
		color: white;
		padding: 14px;
	}

	form input:focus {
		border: none;
		outline: none;
	}

	form button {
		background: navy;
		color: white;
		padding: 14px;
		border: none;
		border-radius: 5px;
		cursor: pointer;
		font-size: 1rem;
	}

	form button:hover {
		background: blue;
	}

	.above,
	.center {
		position: absolute;
		transform: translateY(-50%);
		pointer-events: none;
		color: white;
		border-radius: 4px;
		padding: 0 6px;
		font-size: 0.8 rem;
	}

	.above {
		top: 0;
		left: 24px;
		background: navy;
		border: 1px solid blue;
		font-size: 0.7 rem;
	}

	.center {
		top: 50%;
		left: 6px;
		border: 1px solid transparent;
		opacity: 0;
	}

	.error {
		color: coral;
		font-size: 0.9rem;
	}

	.authOptions {
		padding: 14px 0;
	}

	.authOptions > p {
		position: relative;
	}

	.authOptions > p::after,
	.authOptions > p::before {
		position: absolute;
		top: 50%;
		left: 0;
		transform: translateY(-50%);
		width: 100%;
		height: 1.5px;
		background: white;
	}

	.authOptions > p::after {
		right: 100%;
	}
</style>
