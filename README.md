# 💰 Cash-Flow & Budget Forecasting | Outil de Prévision de Trésorerie 🟢 Live App

> *🇺🇸 A time-series forecasting tool that projects cash position 30/60/90 days ahead and flags overdraft risk before it happens.*
> *🇫🇷 Un outil de prévision de trésorerie qui projette la position de cash à 30/60/90 jours et alerte sur les risques de découvert avant qu'ils n'arrivent.*

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://cash-flow-forecast-portfolio-ofk.streamlit.app/)
![Prophet](https://img.shields.io/badge/Model-Prophet-blue)
![Plotly](https://img.shields.io/badge/Viz-Plotly_Interactive-orange)

👉 **[Tester l'application en direct](https://cash-flow-forecast-portfolio-ofk.streamlit.app/)**

---

## 📉 1. Le Problème Business

La trésorerie est le premier facteur de mortalité des PME. Pourtant beaucoup de dirigeants pilotent **au rétroviseur** : ils lisent des soldes passés et découvrent les tensions — échéance de TVA, salaires, loyer — au moment où elles arrivent.

Le problème n'est pas l'absence de données comptables. C'est qu'elles décrivent hier et ne projettent pas demain.

---

## 💡 2. La Solution

Un outil de forecasting qui transforme un historique de flux en projection actionnable :

1. **Visualiser** la trésorerie future à 30 / 60 / 90 jours, avec intervalle de confiance.
2. **Décomposer** les cycles récurrents pour comprendre *pourquoi* la courbe bouge.
3. **Alerter** sur les franchissements de seuil avant qu'ils ne se produisent.

**Le parti pris produit :** ne pas afficher une courbe de prévision seule. Une projection sans son intervalle de confiance donne une fausse impression de certitude — et un dirigeant qui prend une décision de trésorerie sur une fausse certitude est plus en danger qu'un dirigeant qui n'a pas d'outil.

---

## 🧠 3. Intelligence Embarquée (Time Series)

L'outil s'appuie sur **Prophet** (modèle additif, développé par Meta) pour décomposer les flux financiers en composantes lisibles :

* **Tendance** — l'activité est-elle en croissance ou en érosion structurelle ?
* **Saisonnalité hebdomadaire** — effet des week-ends sur les encaissements.
* **Saisonnalité mensuelle** — décaissements fixes récurrents (salaires, loyer, charges).

Le choix de Prophet plutôt qu'un modèle plus lourd est délibéré : sur des séries financières courtes et fortement saisonnières, un modèle additif interprétable bat un modèle opaque — parce que le dirigeant peut voir *quelle composante* explique la tension, et pas seulement qu'il y en a une.

---

## ⚠️ 4. Périmètre & Honnêteté des Données

**Les données de démonstration sont simulées.** Elles reproduisent le comportement comptable d'une agence digitale (cycles d'encaissement clients, décaissements de paie en fin de mois, échéances fiscales trimestrielles).

**Ce que le projet démontre :** la conception d'un outil de forecasting de bout en bout — modélisation, décomposition, restitution décisionnelle, déploiement d'une app utilisable.

**Ce que le projet ne démontre pas :** une performance prédictive sur des données financières réelles d'entreprise. Les métriques de précision sur données simulées ne se transposent pas.

---

## 🛠️ 5. Stack Technique

* **Langage :** Python 3.10
* **Time Series :** Prophet (modèle additif)
* **Visualisation :** Plotly (graphiques interactifs et zoomables)
* **App Web :** Streamlit

---

## 💻 6. Installation Locale

```bash
git clone https://github.com/oufoke/cash-flow-forecast.git
cd cash-flow-forecast
pip install -r requirements.txt
streamlit run app.py
```

---

## 👤 Auteur

**Oumar Fodé Kebe** — *Senior Data Product Manager*
> Gouvernance data et IA appliquée. Je transforme des systèmes data complexes en produits décisionnels fiables.

[Portfolio](https://oufoke.github.io/) · [LinkedIn](https://www.linkedin.com/in/oumarfodek/)
