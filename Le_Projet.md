Le projet
=========

Ce deuxième chapitre porte sur les spécifications du projet. Ils sont les mêmes que dans le tutoriel Jobeet d'origine de sorte que vous puissiez voir une description plus détaillée et une conception de la maquette.

Jobeet est un logiciel Open-Source d'offres d'emploi qui ne fait qu'une chose, mais il le fait bien. Il est facile à utiliser, personnaliser, étendre et intégrer dans votre site web. Il prend en charge plusieurs langues, et bien sûr, utilise les dernières technologies Web 2.0 pour améliorer l'expérience utilisateur. Il fournit également des flux de données (RSS) et une API pour interagir avec lui en programmant.

Histoires d'utilisateurs
------------------------

Nous avons quatre types d'utilisateurs: administrateur (possède et administre le site web), utilisateur (visite le site à la recherche d'un emploi), recruteur (visite le site pour publier des offres) et partenaire (re-publie les offres sur son site).

Dans le tutoriel original nous avons dû faire deux applications, le frontend, où les utilisateurs interagissent avec le site, et le backend, où les administrateurs gèrent le site. Avec Symfony2 nous ne le ferons pas. Nous aurons une seule application et, à l'intérieur, une section distincte sécurisée pour les administrateurs.


Scénario F1: 
============
Sur la page d'accueil, l'utilisateur voit les dernières offres actives
----------------------------------------------------------------------
Sur la page d'accueil Jobeet, un utilisateur voit une liste des 10 dernières offres actives regroupées par catégorie. Seul le lieu, le poste et la société sont affichés pour chaque offre. Pour chaque catégorie, des liens permettent d'énumérer tous les offres. L'utilisateur peut également rechercher un emploi ou publier un nouvel emploi.


Scénario F2:
============
Un utilisateur peut afficher toutes les offres d'une catégorie
--------------------------------------------------------------
L'utilisateur voit une liste triée par date de toutes les offres d'emploi de la catégorie et paginée avec 20 offres par page.


Scénario F3:
============
Un utilisateur affine la liste avec quelques mots-clés
------------------------------------------------------
L'utilisateur peut saisir des mots-clés pour affiner sa recherche. Les mots-clés peuvent être des mots trouvés dans le lieu, le poste, la catégorie ou les champs de l'entreprise.


Scénario F4:
============
Un utilisateur clique sur une offre pour obtenir des informations plus détaillées
---------------------------------------------------------------------------------
L'utilisateur peut sélectionner une offre dans la liste pour afficher des informations plus détaillées.


Scénario F5:
============
Un utilisateur publie une offre
-------------------------------
Un utilisateur peut publier une offre. Une offre est composée de plusieurs informations:

- Nom de l'entreprise
- Type de contrat (temps plein, temps partiel, ou freelance)
- Logo (option)
- Lien (option)
- Intitulé du poste
- Lieu
- Catégorie (l'utilisateur choisit dans une liste de catégories possibles)
- Description du poste (les liens sont automatiquement créés)
- Comment postuler (les liens sont automatiquement créés)
- Publique (si l'offre peut également être publiée sur les sites partenaires)
- E-mail (e-mail du recruteur)
Le processus comporte seulement deux étapes: l'utilisateur remplit le formulaire avec toutes les informations nécessaires pour décrire l'offre, puis il valide les informations en prévisualisant la fiche finale.

Il n'est pas nécessaire de créer un compte pour publier une offre. Une offre peut être modifiée ultérieurement, grâce à un lien spécifique (protégé par un jeton) donné à l'utilisateur lorsque celle-ci est créée.

Chaque offre d'emploi est en ligne pendant 30 jours (durée configurable par l'administrateur). Un utilisateur peut réactiver ou prolonger la validité de l'offre pour une période de 30 jours supplémentaires, mais uniquement lorsque l'offre expire dans moins de 5 jours.


Scénario F6:
============
Un utilisateur demande à devenir partenaire
-------------------------------------------
Un utilisateur doit demander à devenir partenaire et être autorisé à utiliser l'API Jobeet. Il peut aussi choisir d'obtenir des offres à partir d'un ensemble de sous-catégories disponibles. Pour postuler, l'utilisateur doit fournir les renseignements suivants:

- Nom
- E-mail
- Site
Le compte partenaire doit être activé par l'administrateur. Une fois activé, le partenaire reçoit un jeton à utiliser avec l'API par email.


Scénario F7:
============
Un partenaire récupère la liste des emplois actifs
--------------------------------------------------
Un partenaire peut récupérer la liste des offres en cours en appelant l'API avec son jeton partenaire. La liste peut être retournée dans le format XML, JSON ou YAML. Le partenaire peut limiter le nombre d'offres qui seront retournées, et affiner sa requête en spécifiant une catégorie.


Scénario B1:
============
Un administrateur configure le site
-----------------------------------
L'administrateur peut modifier les catégories disponibles sur le site.


Scénario B2:
============
Un administrateur gère les offres
---------------------------------
L'administrateur peut modifier et supprimer toutes les offres affichées.


Scénario B3:
============
Un administrateur gère les partenaires
--------------------------------------
L'administrateur peut créer ou modifier des partenaires. Il est responsable de l'activation d'un partenaire et peut également désactiver celui-ci. Lorsque l'administrateur active un nouveau partenaire, le système crée un jeton unique pour être utilisé par le partenaire.