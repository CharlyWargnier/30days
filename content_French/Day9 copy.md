# st.line_chart

`st.line_chart` affiche un graphique linéaire.

Il s'agit de sucre syntaxique autour de `st.altair_chart`. La principale différence est que cette commande utilise la colonne et les indices des données pour déterminer les spécifications du graphique. En conséquence, cela est plus facile à utiliser pour de nombreux scénarios "juste tracer ceci", tout en étant moins personnalisable.

Si `st.line_chart` ne devine pas correctement la spécification des données, essayez de spécifier le graphique souhaité à l'aide de st.altair_chart.

## Qu'est-ce que nous construisons ?

Une application simple pour afficher un graphique linéaire.

Déroulement de l'application :
1. Créez un DataFrame `Pandas` à partir de nombres générés aléatoirement via `NumPy`.
2. Créez et affichez le graphique linéaire via la commande `st.line_chart()`.

## Application de démonstration

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.line_chart/)

##Code
Voici comment utiliser [`st.line_chart`](https://docs.streamlit.io/library/api-reference/charts/st.line_chart) :
```python
importer streamlit en tant que st
importer des pandas en tant que pd
importer numpy en tant que np

st.header('Graphique linéaire')

chart_data = pd.DataFrame(
     np.random.randn(20, 3),
     colonnes=['a', 'b', 'c'])

st.line_chart(chart_data)

```

## Explication ligne par ligne
La toute première chose à faire lors de la création d'une application Streamlit est de commencer par importer la bibliothèque `streamlit` en tant que `st` ainsi que d'autres bibliothèques comme celle-ci :
```python
importer streamlit en tant que st
importer des pandas en tant que pd
importer numpy en tant que np
```

Ensuite, nous créons un texte d'en-tête pour l'application :
```python
st.header('Graphique linéaire')
```

Ensuite, nous créons un DataFrame de nombres générés aléatoirement qui contient 3 colonnes.
```python
chart_data = pd.DataFrame(
     np.random.randn(20, 3),
     colonnes=['a', 'b', 'c'])
```

Enfin, un graphique linéaire est créé en utilisant `st.line_chart()` avec le DataFrame stocké dans la variable `chart_data` comme données d'entrée :
```python
st.line_chart(chart_data)
```

## Lectures complémentaires
En savoir plus sur la commande Streamlit connexe suivante à partir de laquelle [`st.line_chart`](https://docs.streamlit.io/library/api-reference/charts/st.line_chart) est basé sur :
- [`st.altair_chart`](https://docs.streamlit.io/library/api-reference/charts/st.altair_chart)