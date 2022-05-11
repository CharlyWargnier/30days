# st.case à cocher

`st.checkbox` affiche un widget de case à cocher.

## Application de démonstration

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.checkbox/)

##Code
Voici comment utiliser `st.checkbox` :
```python
import streamlit as st

st.header('st.checkbox')

st.write ('Que souhaitez-vous commander ?')

glace = st.checkbox('Glace')
café = st.checkbox('Café')
cola = st.checkbox('Cola')

si glace :
     st.write("Génial ! En voici d'autres 🍦")
    
si café :
     st.write("D'accord, voici du café ☕")

si cola :
     st.write("Voilà 🥤")
```

## Explication ligne par ligne
La toute première chose à faire lors de la création d'une application Streamlit est de commencer par import la bibliothèque `streamlit` as `st` comme ceci :
```python
import streamlit as st
```

Ceci est suivi par la création d'un texte d'en-tête pour l'application :
```python
st.header('st.checkbox')
```

Ensuite, nous allons poser une question via `st.write' :
```python
st.write ('Que souhaitez-vous commander ?')
```

Nous allons ensuite fournir quelques éléments de menu à cocher :
```python
glace = st.checkbox('Glace')
café = st.checkbox('Café')
cola = st.checkbox('Cola')
```

Enfin, nous allons imprimer un texte personnalisé en fonction de la case cochée :
```python
si glace :
     st.write("Génial ! En voici d'autres 🍦")
    
si café :
     st.write("D'accord, voici du café ☕")

si cola :
     st.write("Voilà 🥤")
```

## Lectures complémentaires
- [`st.checkbox`](https://docs.streamlit.io/library/api-reference/widgets/st.checkbox)