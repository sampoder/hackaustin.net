<link rel="stylesheet" href="https://cdn.simplecss.org/simple.min.css">

<script>
	import Iodine from '@kingshott/iodine';
	
	const instance = new Iodine();
	
	let email;
	let emailClass;
	
	$: emailValid = instance.assertEmail(email);
	
	$: if(emailValid != true) {
		emailClass = "error"
	} else {
		emailClass = ""
	}
	
	function submitHandler(e) {
		
		if(emailClass == "error") {
			e.preventDefault()
			alert("Your contact email isn't valid")
		}
		
	}
	
</script>

<svelte:head>
  <!-- HTML Meta Tags -->
  <title>Hack Austin! - Registration Form</title>
  <meta name="description" content="Hack Austin is a nonprofit hackathon for Austin high-schoolers to learn to code and build projects they're proud of. The venue is TBD, and will be held on October 14th from 10AM-8PM. Register today!">

  <!-- Google / Search Engine Tags -->
  <meta itemprop="name" content="Hack Austin! - Registration Form">
  <meta itemprop="description" content="Hack Austin is a nonprofit hackathon for Austin high-schoolers to learn to code and build projects they're proud of. The venue is TBD, and will be held on October 14th from 10AM-8PM. Register today!">
  <meta itemprop="image" content="/meta.png">

  <!-- Facebook Meta Tags -->
  <meta property="og:url" content="https://hackaustin.net">
  <meta property="og:type" content="website">
  <meta property="og:title" content="Hack Austin! - Registration Form">
  <meta property="og:description" content="Hack Austin is a nonprofit hackathon for Austin high-schoolers to learn to code and build projects they're proud of. The venue is TBD, and will be held on October 14th from 10AM-8PM. Register today!">
  <meta property="og:image" content="/meta.png">

  <!-- Twitter Meta Tags -->
  <meta name="twitter:card" content="summary_large_image">
  <meta name="twitter:title" content="Hack Austin! - Registration Form">
  <meta name="twitter:description" content="Hack Austin is a nonprofit hackathon for Austin high-schoolers to learn to code and build projects they're proud of. The venue is TBD, and will be held on October 14th from 10AM-8PM. Register today!">
  <meta name="twitter:image" content="/meta.png">
</svelte:head>


<div>
	<h1>
		Hack Austin Registration!
	</h1>
</div>

<form action="https://formspree.io/f/moqbqbab" method="POST" on:submit={submitHandler} id="form">
			<label for="name">Name:</label>
			<input name="Name" id="name" type="text">
			
			<label for="pronouns">Your Pronouns:</label>
			<input name="Your Pronouns" id="pronouns" type="text">
			
			<label for="email" style="margin-bottom: 0.025">Contact Email <b>(very important)</b>:</label>
			<input class={emailClass} bind:value={email} name="Contact Email" id="email" type="email">
			
			<label for="birthday" style="margin-bottom: 0.025">Birthday (upper middle &amp; high-school only):</label>
			<input name="Birthday" id="birthday" type="date">
			
			<label for="tshirt">T-Shirt Size:</label>
			<select name="T-Shirt Size" id="tshirt">
				<option value="axs">AXS</option>
				<option value="as">AS</option>
				<option value="am">AM</option>
				<option value="al">AL</option>
				<option value="axl">AXL</option>
			</select>
			
			<label for="vaccine">I am vaccinated! (you will be required to present proof):</label>
			<input type="checkbox" id="vaccine" name="Vaccination Status">
			
			<label for="techincal">How technical are you? (Beginners are totally welcome! :D)</label>
			<select name="Technical Skill" id="technical">
				<option value="beginner">Beginner - No coding experience or just started learning</option>
				<option value="intermediate">Intermediate - I've taken some CS class or have worked on small projects</option>
				<option value="advanced">Advanced - I can work on projects with little guidance</option>
			</select>
			
			<label for="workshops">Would you like to host a workshop?</label>
			<input type="checkbox" id="workshops" name="Hosting a Workshop">
	
			<label for="dietary">Dietary Restrictions</label>
			<textarea id="dietary" name="Dietary Restrictions" form="form"></textarea>
	
			
			<input type="submit" value="Register!">	
			
		</form>

<style>
	:root {
		--accent: #37F17A !important;
	}
	
	input[type=submit] {
		color: black;
		font-weight: bold;
	}
	
	@media (prefers-color-scheme: dark) {
		div > h1 {
			color: #212121 !important
		}
	}
	
	div {
		background-color: var(--accent);
		width: 100%;
		padding: 0.25rem;
		margin: 1rem 0;
		border-radius: 12px;
	}
	
	div > h1 {
		text-align: center;
	}
	
	input:not([type=checkbox]) {
		width: 100%;
	}
	
	input.error {
		border-color: #ff6961;
	}
</style>
