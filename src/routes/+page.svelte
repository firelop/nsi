<script>
	import {browser} from "$app/environment";
	import {onMount} from "svelte";

	let activeMenuLink = 1;
	onMount(() => {
		if (browser) {
			let lastObserbles = Array.from(document.querySelectorAll(".lastObservable"));
			let observer = new IntersectionObserver(entries => {
				let disapearEntries = entries.filter(entry => entry.intersectionRatio == 0 && entry.boundingClientRect.top < 0);
				if (disapearEntries.length > 0) {
					disapearEntries = disapearEntries.sort((a, b) => a.intersectionRatio - b.intersectionRatio);
					console.log(lastObserbles.indexOf(disapearEntries[0].target));
					activeMenuLink = lastObserbles.indexOf(disapearEntries[0].target) + 2;
					console.log(activeMenuLink);
				}
				// Appear entries need to be at least 50% visible
				let appearEntries = entries.filter(entry => entry.intersectionRatio > 0.5);
				if (appearEntries.length > 0) {
					appearEntries = appearEntries.sort((a, b) => a.intersectionRatio - b.intersectionRatio);
					console.log(lastObserbles.indexOf(appearEntries[0].target));
					activeMenuLink = lastObserbles.indexOf(appearEntries[0].target) + 1;
					console.log(activeMenuLink);
				}
			}, {threshold: [0, 0.5]});
			for (let observables of lastObserbles) {
				observer.observe(observables);
			}
		}
	});
</script>


<svelte:head>
    <title>L'histoire de ECMAScript</title>
	<meta name="description" content="L'histoire de l'ECMAScript" />
	<link rel="stylesheet" href="style.css">
</svelte:head>


	<main>
		<div class="grid-30-70 marginbottom">
			<div class="left-col">
				<div class="sticky">
					<h2 class="x-pad20">Qui suis-je ?</h2>
					<div class="lateral-menu">
						<a class="menu-item {activeMenuLink == 1 ? 'active' : ''}" href="#presentation">Présentation</a>
						<a class="menu-item {activeMenuLink == 2 ? 'active' : ''}" href="#formation">Formation</a>
						<a class="menu-item {activeMenuLink == 3 ? 'active' : ''}" href="#competences">Compétences/Expériences</a>
						<a class="menu-item {activeMenuLink == 4 ? 'active' : ''}" href="#loisirs">Loisirs</a>
					</div>
				</div>
			</div>
			<div class="right-col">
				<h1 class="marginleft observable" id="presentation">Présentation</h1>
				<div class="presentation-card marginbottom lastObservable">
					<img class="presentation-img" src="/moi.jpg" alt="Photo de moi">
					<div class="presentation-text">
						<div class="row">
							<h2 class="marginless">Pierre Guchet</h2>
							<span class="bullet-separator">•</span>
							<span class="level">1E</span>
						</div>
						<p class="marginless">
							Je m'appelle Pierre Guchet.
							J'ai 15 ans et habite à Beaufort-en-Vallée.
							Je suis passionné d'informatique depuis que j'ai 8-9 ans et aimerais travailler dans ce domaine.
						</p>
						<div class="row social-networks">
							<a class="dark" href="https://github.com/firelop"><i class="bi bi-github"></i></a>
							<a class="dark" href="https://www.linkedin.com/in/pierre-guchet-a32087229/"><i class="bi bi-linkedin"></i></a>
							<a class="dark" href="https://youtube.com/@firel0p"><i class="bi bi-youtube"></i></a>
						</div>
					</div>
				</div>

				<h1 class="marginleft observable" id="formation">Formation</h1>
				<div class="marginleft timeline">
					<div class="verline first"><p><b>2019 à 2021</b> - Collège Molière</p></div>
					<div class="circle"></div>
					<div class="verline">
						<h3 class="marginless smallmarginleft">2021 - Obtention du DNB</h3>
					</div>
					<div class="circle"></div>
					<div class="verline">
						<h3 class="marginless smallmarginleft">Septembre 2021 - Entrée à Saint-Aubin la Salle en générale</h3>
						<p>J'avais envie du début à pratiquement la fin de l'année de m'orienter vers une première STI2D.<br>A la fin de l'année j'ai décidé de changer pour rester en générale avec les spécialités SVT, mathématiques et NSI.</p>
					</div>
					<div class="circle"></div>
					<div class="verline last">
						<h3 class="marginless smallmarginleft">Septembre 2022 - Entrée en 1ère générale</h3>
					</div>
				</div>
				<p class="marginleft marginbottom lastObservable">
					J'aimerais plus tard faire de l'intelligence artificielle ou travailler dans un autre domaine des data sciences.
				</p>

				<h1 class="marginleft observable" id="competences">Compétences/Expériences</h1>

				<div class="competence-cards row marginbottom lastObservable">
					<div class="competence-card">
						<img src="python.png" alt="Python" class="competence-img">
						<h3>Python</h3>
						<h4>Depuis : 5 ans</h4>
					</div>
					<div class="competence-card">
						<img src="html.jfif" alt="Logo HTML" class="competence-img">
						<h3>Html/Css</h3>
						<h4>Depuis : 6 mois</h4>
					</div>
					<div class="competence-card">
						<img src="c.png" alt="Language C" class="competence-img">
						<h3>C</h3>
						<h4>Durée : 3 ans</h4>
					</div>
					<div class="competence-card">
						<img src="csharp.jfif" alt="C#" class="competence-img">
						<h3>C#</h3>
						<h4>Durée : 2 ans</h4>
					</div>
					<div class="competence-card">
						<img src="java.png" alt="java" class="competence-img">
						<h3>Java</h3>
						<h4>Durée : 4 ans</h4>
					</div>
				</div>

				<h1 class="marginleft observable" id="loisirs">
					Loisirs
				</h1>
				<img src="escalade.png" alt="Photo d'un mur d'escalade" class="fullwidth">
				<h2 class="marginleft">Escalade</h2>
				<p class="marginleft marginbottom">Je pratique l'escalade une fois par semaine pendant 2h le lundi soir.<br>J'ai débuté cette année.</p>

				<img src="theatre.jpg" alt="Salle de théâtre" class="fullwidth">
				<h2 class="marginleft">Théâtre</h2>
				<p class="marginleft">Durant 3 ans j'ai fait du théâtre dans une association 2 heures par semaine.<br>Après une pause de 2 ans dûe au covid je reprends cette activité de nouveau.</p>
			</div>
		</div>



	</main>
	<footer>
		<div class="row spacebtw">
			<div>
				<h2 class="marginless">Projet Web NSI</h2>
				<div class="row">
					<a href="https://saintaubinlasalle.fr">Saint-Aubin La Salle</a>
					<a href="https://www.ecoledirecte.com/E/5685/EspacesTravail/2273/accueil">Espace de travail</a>
				</div>
			</div>
			<div class="licence">
				<div>
					<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/nc.svg?ref=chooser-v1">
				</div>
				<h5 class="marginless">Licensed under CC BY-NC 4.0</h5>
			</div>
		</div>
	</footer>


