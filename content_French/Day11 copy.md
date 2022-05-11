# st.multiselect

`st.multiselect` affiche un widget multiselect.

## Application de démonstration

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.multiselect/)

##Code
Voici comment utiliser `st.multiselect` :
```python
importer streamlit en tant que st

st.header('st.multiselect')

options = st.multiselect(
     'Quelles sont tes couleurs préférées',
     ['Vert', 'Jaune', 'Rouge', 'Bleu'],
     ['Jaune', 'Rouge'])

st.write('Vous avez sélectionné :', options)
```

## Explication ligne par ligne
La toute première chose à faire lors de la création d'une application Streamlit est de commencer par importer la bibliothèque `streamlit` en tant que `st` comme ceci :
```python
importer streamlit en tant que st
```

Ceci est suivi par la création d'un texte d'en-tête pour l'application :
```python
st.header('st.multiselect')
```

Ensuite, nous allons utiliser le widget `st.multiselect` pour accepter les entrées où les utilisateurs pourront sélectionner une ou plusieurs couleurs de leur choix.

```python
options = st.multiselect(
     'Quelles sont tes couleurs préférées',
     ['Vert', 'Jaune', 'Rouge', 'Bleu'],
     ['Jaune', 'Rouge'])
```

Enfin, nous écrirons les couleurs sélectionnées :
```python
st.write('Vous avez sélectionné :', options)
```

## Lectures complémentaires
- [`st.multiselect`](https://docs.streamlit.io/library/api-reference/widgets/st.multiselect)