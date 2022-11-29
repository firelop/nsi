<script>
    let activeMenuLink = 1;
</script>

<svelte:head>
    <title>Histoire de l'ECMAScript</title>
    <link rel="stylesheet" href="style.css">
</svelte:head>

<main>
    <div class="grid-30-70 marginbottom">
        <div class="left-col">
            <div class="sticky">
                <h2 class="x-pad20">Les sources</h2>
                <div class="lateral-menu">
                    <a class="menu-item {activeMenuLink == 1 ? 'active' : ''}" href="#sources">Sources</a>
                </div>
            </div>
        </div>
        <div class="right-col">
            <h1 class="marginleft" id="meaning">Sources</h1>
            <ul class="marginleft sources">
                <li class="smallmarginbottom">
                    <h2 class="marginless">Wikipedia</h2><a href="https://fr.wikipedia.org/wiki/JavaScript">JavaScript</a>
                    <a href="https://fr.wikipedia.org/wiki/Node.js">Node.js</a>
                </li>
                <li class="smallmarginbottom">
                    <h2 class="marginless">MDN Web Docs</h2>
                    <a href="https://developer.mozilla.org/fr/docs/Web/JavaScript">JavaScript</a>
                </li>
                <li>
                    <h2 class="marginless">Youtube</h2>
                    <a href="https://youtu.be/cdDPQkF7hRA">Ce langage me donne envie de vomir ! - Histoire de Javascript</a>
                </li>
            </ul>
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
