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
    <title>Histoire de l'ECMAScript</title>
    <link rel="stylesheet" href="style.css">
</svelte:head>

<main>
    <div class="grid-30-70 marginbottom">
        <div class="left-col">
            <div class="sticky">
                <h2 class="x-pad20">L'histoire de JavaScript</h2>
                <div class="lateral-menu">
                    <a class="menu-item {activeMenuLink == 1 ? 'active' : ''}" href="#meaning">Définition</a>
                    <a class="menu-item {activeMenuLink == 2 ? 'active' : ''}" href="#landmarkYears">Dates clefs</a>
                </div>
            </div>
        </div>
        <div class="right-col">
            <h1 class="marginleft" id="meaning">Définition</h1>
            <div class="row aligntop marginleft lastObservable">
                <img src="javascript.png" alt="Logo du javascript">
                <p class="marginless smallmarginleft">
                    JavaScript (souvent abrégé en « JS ») est un langage de script faiblement typé et orienté objet.<br>
                    Le standard qui spécifie JavaScript est ECMAScript.<br>
                    En 2012, tous les navigateurs modernes supportent complètement ECMAScript 5.1.<br> Les anciens navigateurs supportent au minimum ECMAScript 3. <br>Une sixième version majeure du standard a été finalisée et publiée le 17 juin 2015. Cette version s'intitule officiellement ECMAScript 2015 mais est encore fréquemment appelée ECMAScript 6 ou ES6.<br> Le standard ECMAScript est mis à jour annuellement.

                    Les languages Java et Javascript sont souvent confondus mais ils ne sont semblables en aucun point. Le Javascript tient son nom de son histoire expliquée dans la timeline.
                </p>
            </div>

            <h1 class="marginleft" id="landmarkYears">Dates clefs</h1>
            <div class="marginleft timeline lastObservable">
                <div class="verline first">
                    <p>
                        <b>Netscape</b>, le navigateur ayant le plus de parts de marché en 1995 cherche à ajouter de l'interactivité dans les sites web côté client.
                        Ils vont engager <b>Brendan Eich</b>, le créateur de LiveScript, language côté serveur, pour ajouter une version client de celui-ci côté client dans le navigateur.

                        Un accord sera signé entre Netscape et Sun, la société qui maintient Java.
                        <b>Cette version de LiveScript côté client sera renommé JavaScript.</b>
                    </p>
                </div>
                <div class="circle"></div>
                <div class="verline">
                    <h3 class="marginless smallmarginleft">4 décembre 1995</h3>
                    <p>Netscape et Sun annoncent ce nouveau language au public en le décrivant comme <b>un complément à Java</b> qui devait, à cette époque, être intégré à Netscape Navigator 2.0.</p>
                </div>
                <div class="circle"></div>
                <div class="verline">
                    <h3 class="marginless smallmarginleft">Mars 1996</h3>
                    <p>C'est en mars 1996 que sort <b>Netscape Navigator 2.0</b> embarqué avec un moteur javascript qui permet d'interpréter le code javascript intégré aux sites internet. Le succès est tellement fulgurant que Microsoft et son "Internet Explorer" développeront JScript une, à peu de choses près, copie de JavaScript.</p>
                </div>
                <div class="circle"></div>
                <div class="verline">
                    <h3 class="marginless smallmarginleft">Juin 1997</h3>
                    <p>Les problèmes de compatibilité entre les différentes versions de JavaScript et JScript vont pousser sa <b>standardisation</b> (la création de normes, de standards). Ainsi en juin 1997 naît le standard JavaScript: <b>ECMAScript</b></p>
                </div>
                <div class="circle"></div>
                <div class="verline last">
                    <h3 class="marginless smallmarginleft">27 mai 2009</h3>
                    <p>En 2009 Ryan Lienhart Dahl crée NodeJS, une version côté serveur de JavaScript. C'est ce qui fait aujourd'hui de JavaScript un language extrêmement polyvalent.</p>
                </div>
            </div>
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
