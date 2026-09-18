# Prévision de trésorerie — Voir venir les tensions à 90 jours

> 🇫🇷 Un outil de prévision qui décompose une série financière en tendance et saisonnalité, pour anticiper les tensions plutôt que les constater.
> 🇬🇧 A forecasting tool that separates trend from seasonality in a financial series, to anticipate pressure rather than observe it.

**[Lancer la démo](https://cash-flow-forecast-portfolio-ofk.streamlit.app/)**


---

## Le problème

Beaucoup d'organisations pilotent leurs flux financiers au rétroviseur : on constate une tension au moment où elle se produit, parce que la seule vue disponible est celle du passé.

Les flux financiers ne sont pourtant pas erratiques. Ils portent une tendance de fond et des cycles réguliers — échéances mensuelles, effets de fin de trimestre. Ce qui est cyclique est anticipable.

---

## Ce que fait le système

Le modèle décompose la série en composantes additives : une tendance de fond ajustée par segments, des cycles réguliers approchés par des fonctions périodiques, l'effet de dates particulières, et un reste inexpliqué.

Chaque composante est affichable séparément. C'est l'intérêt principal du choix de modèle : on peut montrer la tendance et la saisonnalité à un décideur, ce qu'un modèle opaque ne permet pas.

---

## Stack

* **Langage** — Python
* **Prévision** — Prophet, modèle additif
* **Visualisation** — Plotly
* **Interface** — Streamlit

---

## Décisions & arbitrages

*Section rétrospective.*

### Un modèle lisible plutôt qu'un modèle performant

**Contexte.** Le destinataire est un décideur, pas un analyste.
**Décision.** Un modèle décomposable dont chaque composante s'explique.
**Pourquoi.** Une prévision qu'un directeur financier ne peut pas interroger n'est pas utilisée. La lisibilité est ici une fonctionnalité produit, pas une préférence esthétique.
**Ce que ça coûte.** Sur beaucoup de séries, une méthode moins lisible ferait mieux. Le compromis est assumé — mais il n'a pas été mesuré, ce qui est le vrai manque du projet.

### Modèle additif plutôt que multiplicatif

**Décision.** Décomposition additive.
**Ce que ça suppose.** Que l'amplitude des cycles ne croît pas avec le niveau de la série. Sur une série en forte croissance, cette hypothèse tombe et une décomposition multiplicative serait plus juste.
**Statut.** Hypothèse non testée sur les données du projet.

---

## Limites connues

* **Le modèle ajuste une courbe, il n'explique rien.** Aucune causalité. Il prolonge ce qu'il a vu et se trompe systématiquement au premier changement de régime.
* **Les points de rupture détectés automatiquement peuvent inventer des tendances.** Le modèle voit un virage là où il n'y avait que du bruit, puis le prolonge.
* **Les intervalles d'incertitude sont trop étroits.** Ils ne capturent qu'une partie des sources d'erreur, ce qui donne une fausse impression de maîtrise sur une prévision budgétaire — le pire endroit pour ça.
* **Les données sont simulées.** Même limite circulaire que sur tout modèle entraîné sur des données générées : ce qu'on mesure, c'est la capacité à retrouver la structure du générateur.

---

## Ce qui n'a pas été mesuré

**Il n'y a pas de comparaison avec une référence naïve, et c'est le manque le plus grave de ce projet.**

Sans référence, une erreur de prévision n'est pas interprétable. Une erreur de 8 % est excellente si la méthode naïve fait 20 %, et inutile si elle en fait 7. Le premier réflexe sur tout sujet de prévision devrait être de comparer à « la période suivante ressemble à la précédente ».

**Ce qu'il faudrait faire.** Validation rétrospective glissante, comparaison à deux références naïves — dernière valeur et moyenne saisonnière — et publication de l'écart quel qu'il soit.

---

## Difficultés rencontrées

* **La construction du jeu de données simulé.** Reproduire un comportement financier crédible — cycles d'encaissement, échéances fixes, bruit réaliste — sans rendre le problème artificiellement facile.

---

*Oumar Fodé KEBE — [oufoke.github.io](https://oufoke.github.io) · [LinkedIn](https://www.linkedin.com/in/oumarfodek/)*

