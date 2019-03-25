# ![](ressources/logo.jpeg) Prog web client riche - JavaScript 

### IUT Montpellier-Sète – Département Informatique

## TD1
#### _Thème : dynamiser une page web_

Cliquez sur le lien ci-dessous pour faire, dans un dossier public_html/JS/TD1, votre fork privé du TP (**attention, pas de fork à la main !**):

https://classroom.github.com/a/_nx8U2hg

## INTRODUCTION

Vos TD et projets de S1 (Conception Doc) vous ont appris à créer des sites web statiques, où les pages ne varient pas. Leur seul aspect dynamique était apporté pas le css qui permettait des effets (media querries, transitions, etc).
  
En S3 vous avez appris à réellement dynamiser vos sites web en utilisant des appels au serveur web, avec des pages web construites par le serveur, en fonction de données recueillies sur la base de données ou par le biais de formulaires, et au moyen du langage PHP.

L’aspect dynamique de ces sites tient donc au fait que le serveur web construit la page sur demande (en fonction de l’utilisateur, des données d’un formulaire, etc). La page construite est donc fonction des circonstances, et c’est ce qui lui donne son caractère dynamique.

JavaScript permet de rendre dynamique une page web par l’utilisation de scripts, en réponse à des sollicitations côté client. Par exemple, des événements comme un clic de souris, une action au clavier, etc. Ici l’aspect dynamique est indépendant d’un appel serveur.

Dans certains cas, il peut être excessif de faire des appels permanents au serveur. Dans ce TD1 vous allez devoir modifier une page web qui pour le moment est en partie remplie via PHP, par des appels exagérés au serveur web.

Créez dans votre public_html un dossier JS/TD1 et importez-y la structure du fichier td1-dynamiser_une_page_web.zip de moodle.

Dans ce TD1, vous commencez à coder en JavaScript, sans cours préalable. Pas d’inquiétude, vous avez déjà un passé de prog objet, et même s’il faut se méfier de pas mal de choses intuitives avec ce langage, cela ne vous empêchera pas de faire vos premiers pas en JavaScript !

## EXERCICE 1 - mécanisme client serveur

1. Rappelez dans un schéma concis le mécanisme client-serveur qui permet de servir les pages web suite à une requête http. Dans quel contexte avez-vous utilisé ce mécanisme en S3 ?

2. Appelez la page _index.php?fleur=rose_ et expliquez le rôle de chaque instruction PHP de cette page (lignes 1 à 12, lignes 26 et 30).

3. En cliquant sur un des 4 items du menu, on fait une requête http au serveur, en lui passant en GET une valeur de fleur. Expliquez ce qui est actualisé sur la page quand on clique sur un item du menu. Vous pouvez le voir en affichant le code source de la page, et en cliquant sur les liens du menu dans le code source. 

## EXERCICE 2 - dynamiser le menu

1. Excluez tous les appels au serveur dans les liens du menu en remplaçant les _href="index.php?fleur=…"_ par des _href="#"_. Vérifiez que le menu n’agit plus (ne lance plus de requête http).

2. Excluez de la partie PHP initiale (lignes 1 à 12) les lignes qui affectent une valeur à la variable _$fleur_.

3. Réactualisez la page web. Cliquez sur le menu. Expliquez ce que vous constatez.

4. Pour corriger l’erreur, modifiez le contenu de la balise html `<div class='galerie'>` pour que par défaut elle affiche les roses, en remplaçant les évocations au PHP par ce qu’il faut.

5. Modifiez les balises `<a>` du menu pour les transformer ainsi :


        <nav>
          <ul>
            <li><a href="#" onclick="adapter_galerie('rose');">rose</a></li>
            <li><a href="#" onclick="adapter_galerie('hortensia');">hortensia</a></li>
            <li><a href="#" onclick="adapter_galerie('fruitier');">fruitier</a></li>
            <li><a href="#" onclick="adapter_galerie('autre');">autre</a></li>
          </ul>
        </nav>

6. Ouvrez l’examinateur d’élément, menu « console » (F12), rafraîchissez la page, cliquez sur un item du menu et expliquez le message d’erreur qui apparaît.
L’attribut _onclick_ des balises `<a>` a pour valeur une chaîne   de caractères qui évoque l’exécution d’une fonction **adapter_galerie** avec un paramètre propre à chaque balise `<a>`.
Cet attribut _onclick_ permet un appel à un script JavaScript quand le lien est cliqué.

7. Juste avant la balise `</body>`, ajoutez le code suivant, et vérifiez que l’erreur précédente ne se produit plus.


        <script type="text/javascript">
            function adapter_galerie(nom) {
                // à compléter
            }
        </script>

8. Essayez, à la place du commentaire `// à compléter`, les divers codes suivants, et décrivez ce qu’ils font :


        console.log("bonjour de la part du menu !");

        console.log(nom);


9. Analysez ensuite le code suivant pour anticiper ce qu’il va produire :


        <script type="text/javascript">
          function adapter_galerie(nom) {
            for(var i = 1; i <= 6; i++) {
              var image = document.getElementById('fleur' + i);
              image.src = 'img/fleurs/' + nom + '/' + nom + i + '.jpg';
            }
          }
        </script>


   Que renvoie `document.getElementById('fleur' + i)` ?

   Que fait `image.src = …` ?

   Copiez le nouveau code de adapter_galerie, puis vérifiez vos  réponses par l’inspecteur d’éléments après les clics sur les  items du menu.


