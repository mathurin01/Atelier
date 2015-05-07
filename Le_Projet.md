Le projet
=========

Ce deuxi�me chapitre porte sur les sp�cifications du projet. Ils sont les m�mes que dans le tutoriel Jobeet d'origine de sorte que vous puissiez voir une description plus d�taill�e et une conception de la maquette.

Jobeet est un logiciel Open-Source d'offres d'emploi qui ne fait qu'une chose, mais il le fait bien. Il est facile � utiliser, personnaliser, �tendre et int�grer dans votre site web. Il prend en charge plusieurs langues, et bien s�r, utilise les derni�res technologies Web 2.0 pour am�liorer l'exp�rience utilisateur. Il fournit �galement des flux de donn�es (RSS) et une API pour interagir avec lui en programmant.

Histoires d'utilisateurs
------------------------

Nous avons quatre types d'utilisateurs: administrateur (poss�de et administre le site web), utilisateur (visite le site � la recherche d'un emploi), recruteur (visite le site pour publier des offres) et partenaire (re-publie les offres sur son site).

Dans le tutoriel original nous avons d� faire deux applications, le frontend, o� les utilisateurs interagissent avec le site, et le backend, o� les administrateurs g�rent le site. Avec Symfony2 nous ne le ferons pas. Nous aurons une seule application et, � l'int�rieur, une section distincte s�curis�e pour les administrateurs.


Sc�nario F1: 
============
Sur la page d'accueil, l'utilisateur voit les derni�res offres actives
----------------------------------------------------------------------
Sur la page d'accueil Jobeet, un utilisateur voit une liste des 10 derni�res offres actives regroup�es par cat�gorie. Seul le lieu, le poste et la soci�t� sont affich�s pour chaque offre. Pour chaque cat�gorie, des liens permettent d'�num�rer tous les offres. L'utilisateur peut �galement rechercher un emploi ou publier un nouvel emploi.


Sc�nario F2:
============
Un utilisateur peut afficher toutes les offres d'une cat�gorie
--------------------------------------------------------------
L'utilisateur voit une liste tri�e par date de toutes les offres d'emploi de la cat�gorie et pagin�e avec 20 offres par page.


Sc�nario F3:
============
Un utilisateur affine la liste avec quelques mots-cl�s
------------------------------------------------------
L'utilisateur peut saisir des mots-cl�s pour affiner sa recherche. Les mots-cl�s peuvent �tre des mots trouv�s dans le lieu, le poste, la cat�gorie ou les champs de l'entreprise.


Sc�nario F4:
============
Un utilisateur clique sur une offre pour obtenir des informations plus d�taill�es
---------------------------------------------------------------------------------
L'utilisateur peut s�lectionner une offre dans la liste pour afficher des informations plus d�taill�es.


Sc�nario F5:
============
Un utilisateur publie une offre
-------------------------------
Un utilisateur peut publier une offre. Une offre est compos�e de plusieurs informations:

- Nom de l'entreprise
- Type de contrat (temps plein, temps partiel, ou freelance)
- Logo (option)
- Lien (option)
- Intitul� du poste
- Lieu
- Cat�gorie (l'utilisateur choisit dans une liste de cat�gories possibles)
- Description du poste (les liens sont automatiquement cr��s)
- Comment postuler (les liens sont automatiquement cr��s)
- Publique (si l'offre peut �galement �tre publi�e sur les sites partenaires)
- E-mail (e-mail du recruteur)
Le processus comporte seulement deux �tapes: l'utilisateur remplit le formulaire avec toutes les informations n�cessaires pour d�crire l'offre, puis il valide les informations en pr�visualisant la fiche finale.

Il n'est pas n�cessaire de cr�er un compte pour publier une offre. Une offre peut �tre modifi�e ult�rieurement, gr�ce � un lien sp�cifique (prot�g� par un jeton) donn� � l'utilisateur lorsque celle-ci est cr��e.

Chaque offre d'emploi est en ligne pendant 30 jours (dur�e configurable par l'administrateur). Un utilisateur peut r�activer ou prolonger la validit� de l'offre pour une p�riode de 30 jours suppl�mentaires, mais uniquement lorsque l'offre expire dans moins de 5 jours.


Sc�nario F6:
============
Un utilisateur demande � devenir partenaire
-------------------------------------------
Un utilisateur doit demander � devenir partenaire et �tre autoris� � utiliser l'API Jobeet. Il peut aussi choisir d'obtenir des offres � partir d'un ensemble de sous-cat�gories disponibles. Pour postuler, l'utilisateur doit fournir les renseignements suivants:

- Nom
- E-mail
- Site
Le compte partenaire doit �tre activ� par l'administrateur. Une fois activ�, le partenaire re�oit un jeton � utiliser avec l'API par email.


Sc�nario F7:
============
Un partenaire r�cup�re la liste des emplois actifs
--------------------------------------------------
Un partenaire peut r�cup�rer la liste des offres en cours en appelant l'API avec son jeton partenaire. La liste peut �tre retourn�e dans le format XML, JSON ou YAML. Le partenaire peut limiter le nombre d'offres qui seront retourn�es, et affiner sa requ�te en sp�cifiant une cat�gorie.


Sc�nario B1:
============
Un administrateur configure le site
-----------------------------------
L'administrateur peut modifier les cat�gories disponibles sur le site.


Sc�nario B2:
============
Un administrateur g�re les offres
---------------------------------
L'administrateur peut modifier et supprimer toutes les offres affich�es.


Sc�nario B3:
============
Un administrateur g�re les partenaires
--------------------------------------
L'administrateur peut cr�er ou modifier des partenaires. Il est responsable de l'activation d'un partenaire et peut �galement d�sactiver celui-ci. Lorsque l'administrateur active un nouveau partenaire, le syst�me cr�e un jeton unique pour �tre utilis� par le partenaire.