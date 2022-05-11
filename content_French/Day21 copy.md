# st.progrès

`st.progress` affiche une barre de progression qui se met à jour graphiquement au fur et à mesure que l'itération progresse.

## Application de démonstration

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.progress/)

##Code
Voici comment utiliser `st.progress` :
```python
importer streamlit en tant que st
temps d'importation

st.title('st.progress')

with st.expander('About this app'):
     st.write('Vous pouvez maintenant afficher la progression de vos calculs dans une application Streamlit avec la commande `st.progress`.')

ma_bar = st.progress(0)

pour percent_complete dans la plage (100):
     temps.sleep(0.05)
     my_bar.progress(percent_complete + 1)

st.ballons()
```

## Explication ligne par ligne
La toute première chose à faire lors de la création d'une application Streamlit est de commencer par importer la bibliothèque `streamlit` en tant que `st` avec la bibliothèque `time` comme ceci :
```python
importer streamlit en tant que st
temps d'importation
```

Ensuite, nous créons un texte de titre pour l'application :
```python
st.title('st.progress')
```

Une **boîte À propos** est créée à l'aide de `st.expander` et la description est affichée via `st.write` :
```python
with st.expander('About this app'):
     st.write('Vous pouvez maintenant afficher la progression de vos calculs dans une application Streamlit avec la commande `st.progress`.')
```

Enfin, nous définissons une barre de progression et l'instancions avec une valeur de départ de "0". Ensuite, une boucle `for` itérera de `0` jusqu'à ce que `100` soit atteint. À chaque itération, nous utilisons `time.sleep(0.05)` pour permettre à l'application d'attendre `0.05` avant d'ajouter une valeur de `1` à la barre de progression `my_bar` et, ce faisant, l'affichage graphique de la barre augmente à chaque itération.
```python
ma_bar = st.progress(0)

pour percent_complete dans la plage (100):
     temps.sleep(0.05)
     my_bar.progress(percent_complete + 1)

st.ballons()
```

## Lectures complémentaires
- [`st.progress`](https://docs.streamlit.io/library/api-reference/status/st.progress)