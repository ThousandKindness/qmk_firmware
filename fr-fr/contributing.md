# Comment contribuer

👍🎉 Premièrement, merci de prendre le temps de lire ceci et de contribuer! 🎉👍

Les contributions de tiers nous aide à améliorer et faire grandir QMK. Nous voulons rendre les pull requests et le processus de contribution utile et simple à la fois pour les contributeurs et les mainteneurs. C'est pourquoi nous avons mis en places des directives pour les contributeurs afin que votre pull request puisse être accepté sans changement majeur.

* [Aperçu du projet](#project-overview)
* [Conventions de codage](#coding-conventions)
* [Directives générales](#general-guidelines)
* [Que veut dire le code de conduite pour moi?](#what-does-the-code-of-conduct-mean-for-me)

## Je ne veux pas lire tout ce pavé! J'ai juste une question!

Si vous voulez poser une question sur QMK, vous pouvez le faire sur le [sous-reddit OLKB](https://reddit.com/r/olkb) ou sur [Discord](https://discord.gg/Uq7gcHh).

Merci de garder ceci en tête:

* Cela peut prendre plusieurs heures pour que quelqu'un réponde à votre question. Merci d'être patient!
* Tous ceux impliqués avec QMK fait don de son temps et de son énergie. Nous ne sommes pas payés pour travailler sur ou répondre aux questions concernant QMK.
* Essayez de poser vos questions de manière à ce qu'elles soient le plus simple à répondre possible. Si vous n'êtes pas sûrs de savoir comment faire, voici quelques bon guides (en anglais):
  * https://opensource.com/life/16/10/how-ask-technical-questions
  * http://www.catb.org/esr/faqs/smart-questions.html

# Aperçu du projet

QMK est majoritairement écrit en C, avec quelques fonctions et parties spécifiques écrites en C++. Il est destiné aux processeurs intégrés que l'on trouve dans des clavier, particulièrement AVR ([LUFA](https://www.fourwalledcubicle.com/LUFA.php)) et ARM ([ChibiOS](https://www.chibios.org)). Si vous maîtrisez déjà la programmation sur Arduino, vous trouverez beaucoup de concepts et de limitations familiers. Une expérience préalable avec les Arduino n'est pas nécessaire à contribuer avec succès à QMK.

<!-- FIXME: We should include a list of resources for learning C here. -->

# Où trouver de l'aide?

Si vous avez besoin d'aide, vous pouvez [ouvrir une issue](https://github.com/qmk/qmk_firmware/issues) ou [un chat sur Discord](https://discord.gg/Uq7gcHh).

# Comment contribuer?

Vous n'avez encore jamais contribué à un projet open source? Vous vous demandez comment les contributions dans QMK fonctionnent? Voici un aperçu rapide!

0. Enregistrez-vous sur [GitHub](https://github.com).
1. Définissez une keymap à contribuer, [trouvez une issue](https://github.com/qmk/qmk_firmware/issues) que vous souhaitez corriger, ou [une fonction](https://github.com/qmk/qmk_firmware/issues?q=is%3Aopen+is%3Aissue+label%3Afeature) que vous voulez ajouter.
2. Créez un fork sur le dépôt associé avec une issue sur votre compte GitHub. Cela veut dire que vous allez avoir une copie du dépôt sous `votre-login-GitHub/qmk_firmware`.
3. Clonez le dépôt sur votre machine locale en utilisant `git clone https://github.com/login-github/repository-name.git`.
4. Si vous travaillez sur une nouvelle fonctionnalité, pensez à ouvrir une issue pour parler avec nous du travail que vous souhaitez démarrer.
5. Créez une nouvelle branche pour votre correctif en utilisant `git checkout -b nom-de-branche`.
6. Faites les changements nécessaires pour corriger le problème ou ajouter la fonctionnalité.
7. Utilisez `git add chemin-de-fichier` pour ajouter les contenus des fichiers modifiés au "snapshot" que git utilise pour gérer l'état du projet, appelé aussi l'index.
8. Utilisez `git commit -m "Insérez une description courte des changements (en anglais)"` pour enregistrer le contenu de l'index avec un message descriptif.
9. Poussez les changements vers votre dépôt sur GitHub en utilisant `git push origin nom-de-branche`.
10. Créez un pull request sur [QMK Firmware](https://github.com/qmk/qmk_firmware/pull/new/master).
11. Donnez un titre à votre pull request en utilisant une description courte des changements que vous avez fait et ajoutez le numéro de l'issue ou du bug associé avec votre changement. Les commentaires de PR devraient se faire en anglais de préférence. Par exemple, vous pouvez utiliser un titre tel que celui-là: "Added more log outputting to resolve #4352".
12. Dans la description du pull request, expliquez les changements que vous avez fait et tous les problèmes qui existent, selon vous, sur le pull request que vous avez fait. Vous pouvez aussi utiliser la description pour poser des questions au mainteneur. Il n'est pas nécessaire que votre pull request soit parfait (aucun pull request ne l'est), le reviewer sera là pour vous aider à résoudre les problèmes et l'améliorer!
13. Attendez que le pull request soit revu par un mainteneur.
14. Faites des changements au pull request si le mainteneur le recommande.
15. Célébrez votre succès une fois votre pull request fusionné!

# Conventions de codage

La grande majorité de notre style est plutôt simple à comprendre. Si vous connaissez C ou Python, vous ne devriez pas avoir trop de difficulté avec notre style.

* [Conventions de codage - C](coding_conventions_c.md)
* [Conventions de codage - Python](coding_conventions_python.md)

# Directives générales

Nous avons un certain nombre de type de changements dans QMK, chacun nécessitant un niveau de rigueur différent. Nous voulons que vous gardiez les directives suivantes en tête quel que soit le changement que vous êtes en train de faire.

* Séparez les PR dans des unités logiques. Par exemple, ne soumettez pas un PR qui couvre deux fonctionnalités séparées, soumettez plutôt un PR pour chaque fonctionnalité.
* Vérifiez les espaces blancs non nécessaires avec `git diff --check` avant de commit.
* Assurez-vous que votre code compile.
  * Keymaps: Assurez-vous que `make keyboard:your_new_keymap` ne renvoie pas d'erreur.
  * Claviers: Assurez-vous que `make keyboard:all` ne renvoie pas d'erreur.
  * Core: Assurez-vous que `make all` ne renvoie pas d'erreur.
* Assurez-vous que les messages de commit soient compréhensibles d'eux-mêmes. Vous devriez écrire une description simple (pas plus de 70 caractères) sur la première ligne, suivi d'une ligne vide, suivi d'un détail de votre commit, si nécessaire. Exemple:

```
Adjust the fronzlebop for the kerpleplork

The kerpleplork was intermittently failing with error code 23. The root cause was the fronzlebop setting, which causes the kerpleplork to activate every N iterations.

Limited experimentation on the devices I have available shows that 7 is high enough to avoid confusing the kerpleplork, but I'd like to get some feedback from people with ARM devices to be sure.
```

## Documentation

La documentation est l'une des manières les plus simples de démarrer la contribution sur QMK. Il est simple de trouver des endroits où la documentation est fausse ou incomplète, et il est tout aussi simple de la corriger! Nous avons aussi grandement besoin de quelqu'un pour éditer notre documentation, donc si vous avez des compétences en édition mais que vous n'êtes pas sûr de savoir où aller, n'hésitez pas [demandez de l'aide](#where-can-i-go-for-help)!

Vous trouverez toute notre documentation dans le répertoire `qmk_firmware/docs`, ou si vous préférez utiliser des outils web, vous pouvez cliquer sur le bouton "Suggest An Edit" en haut de chaque page sur https://docs.qmk.fm/.

Lorsque vous donnez des exemples de code dans la documentation, essayez de suivre les conventions de nommage utilisées ailleurs dans la documentation. Par exemple, standardisez les enums en utilisant `my_layers` ou `my_keycodes` afin de garder une consistance:

```c
enum my_layers {
  _FIRST_LAYER,
  _SECOND_LAYER
};

enum my_keycodes {
  FIRST_LAYER = SAFE_RANGE,
  SECOND_LAYER
};
```

## Keymaps

La plupart des contributeurs débutants démarrent avec leurs keymaps personnelles. Nous essayons de garder les standards pour les keymaps pluôt simple (les keymaps reflètent, après tout, la personnalité de leurs créateurs) mais nous demandons que vous suiviez les directives suivantes afin que d'autres puissent découvrir et apprendre de votre keymap.

* Ecrivez un fichier `readme.md` en utilisant [la template](documentation_templates.md).
* Tous les PR de keymaps doivent être "squashés", donc si la manière dont vos commits sont squashés vous est important, vous devez le faire vous-même.
* Ne regroupez pas des fonctionnalités avec votre PR de keymap. Envoyez d'abord votre fonctionnalité, puis créez un second PR pour la keymap.
* N'incluez pas de fichier `Makefile` dans votre dossier de keymap (ils ne sont plus utilisés)
* Mettez à jour les copyrights dans les en-têtes de fichiers (cherchez `%YOUR_NAME%`)

## Claviers

Les claviers sont la raison d'être de QMK. Certains claviers sont maintenus par la communauté, alors que d'autre sont maintenus par les gens responsables de la création du clavier. Le fichier `readme.md` devrait vous informer de qui maintient le clavier. Si vous avez des questions concernant un clavier en particulier, vous pouvez [Ouvrir une issue](https://github.com/qmk/qmk_firmware/issues) et tagger le mainteneur dans votre question.

Nous vous demandons aussi que vous suiviez ces directives:

* Ecrivez un fichier `readme.md` en utilisant [le template](documentation_templates.md).
* Gardez un nombre de commits raisonnable, ou nous squasherons votre PR.
* Ne regroupez pas des fonctionnalités avec le PR pour votre clavier. Envoyez d'abord votre fonctionnalité, puis créez un second PR pour le clavier.
* Appelez les fichiers `.c`/`.h` du nom du dossier parent, par exemple `/keyboards/<kb1>/<kb2>/<kb2>.[ch]`
* N'incluez pas de fichier `Makefile` dans votre dossier de keymap (ils ne sont plus utilisés)
* Mettez à jour les copyrights dans les en-têtes de fichiers (cherchez `%YOUR_NAME%`)

## Quantum/TMK Core

Faites attention d'être sûr d'implémenter votre nouvelle fonctionnalité de la meilleure manière qu'il soit avant d'investir beaucoup de travail à son développement. Vous pouvez apprendre les bases de QMK en lisant [Comprendre QMK](understanding_qmk.md), qui vous donnera une idée du flux du programme QMK. A partir de là, parlez nous afin de définir la meilleure façon d'implémenter votre idée. Il y a deux façons principale de le faire:

* [Chat sur Discord](https://discord.gg/Uq7gcHh)
* [Ouvrir une Issue](https://github.com/qmk/qmk_firmware/issues/new)

Les PR de nouvelles fonctionnalités de de correction de bug affectent tous les claviers. Nous sommes aussi dans un processus de restructuration de QMK. Pour cette raison, il est absolument nécessaire que tout changement important ou significatif soit discuté avant que l'implémentation soit faite. Si vous ouvrez un PR sans nous avoir parlé, préparez-vous à faire des refontes significatives si vos changements ne sont pas compatibles avec ce que nous avons planifié.

Voici quelques choses à garder en tête lorsque vous travaillez sur une fonctionnalité ou un bug fix.

* **Désactivé par défaut** - la mémoire est plutôt limitée sur la plupart des puces que QMK supporte, et il est important que les keymaps courantes ne soient pas cassées. S'il vous plaît faites que vos features doivent être **activées** plutôt que désactivées. Si vous pensez qu'elle devrait être activée par défaut, ou que cela réduit la taille du code, parlez-nous-en.
* **Compilez localement avant de soumettre** - Cela devrait aller sans dire, mais votre code doit compiler! Vous devriez toujours faire gaffe à ce que vos changements compilent avant d'ouvrir une pull request.
* **Faites attention aux révisions et différentes bases de puces** - beaucoup de claviers ont des révisions qui permettent des changements de configuration mineurs, voir des bases de chip différentes. Essayez de faire que votre fonctionnalité soit supportée à la fois sur ARM et AVR, ou désactivez-là automatiquement sur les plateformes non supportées.
* **Expliquez votre fonctionnalité** - Documentez-là dans `docs/`, soit dans un nouveau fichier, ou dans une partie d'un fichier existant. Si vous ne la documentez pas, personne ne pourra bénéficier de votre dur labeur.

Nous vous demandons aussi de suivre ces directives:

* Gardez un nombre de commits raisonnable, ou nous squasherons votre PR.
* Ne regroupez pas des claviers ou des keymaps avec des changements core. Soumettez vos changements core en premier.
* Ecrivez des [Tests Unitaires](unit_testing.md) pour votre fonctionnalité.
* Suivez le style du fichier que vous modifiez. Si le style n'est pas clair ou qu'il y a un mélange de fichiers, vous devriez vous conformer aux [conventions de codage](#coding-conventions) au dessus.

## Refactoriser

Afin de maintenir une vision claire sur comment les choses sont architectuées dans QMK, nous essayons de planifier des refactorisations en profondeur et qu'un collaborateur fasse le changement. Si vous avez une idée de refactorisation, ou une suggestion, [ouvrez une issue] [open an issue](https://github.com/qmk/qmk_firmware/issues), nous adorons discuter de comment améliorer QMK.

# Que veut dire le code de conduite pour moi?

Note [Code De Conduite](https://github.com/qmk/qmk_firmware/blob/master/CODE_OF_CONDUCT.md) veut dire que vous avez la responsabilité de traiter tout le monde dans le projet avec respect et courtoisie, peu importe leur identité. Si vous êtes victime d'une attitude ou de commentaires inappropriés, tels que décrit dans notre Code de Conduite, nous sommes là pour vous et nous ferons de notre mieux pour nous assurer que le fautif soit réprimandé, tel que décrit dans notre code.
