# st.selectbox

`st.selectbox` permet l'affichage d'un widget de sélection.

## Qu'est-ce que nous construisons ?

Une application simple qui demande à l'utilisateur quelle est sa couleur préférée.

Déroulement de l'application :
1. L'utilisateur sélectionne une couleur
2. L'application imprime la couleur sélectionnée

## Application de démonstration
L'application Streamlit déployée devrait ressembler à celle illustrée dans le lien ci-dessous :

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.selectbox/)

##Code
Voici le code pour implémenter l'application mentionnée ci-dessus :
```python
import streamlit as st

st.header('st.selectbox')

option = st.selectbox(
     'Quelle est votre couleur préférée?',
     ('Bleu', 'Rouge', 'Vert'))

st.write('Votre couleur préférée est ', option)
```

## Explication ligne par ligne
La toute première chose à faire lors de la création d'une application Streamlit est de commencer par import la bibliothèque `streamlit` as `st` comme ceci :
```python
import streamlit as st
```

Ceci est suivi par la création d'un texte d'en-tête pour l'application :
```python
st.header('st.selectbox')
```

Ensuite, nous allons créer une variable appelée `option` qui acceptera l'entrée de l'utilisateur sous la forme d'un widget d'entrée **select** via la commande `st.selectbox()`.

```python
option = st.selectbox(
     'Quelle est votre couleur préférée?',
     ('Bleu', 'Rouge', 'Vert'))
```
Comme nous pouvons le voir dans la boîte de code ci-dessus, la commande `st.selectbox()` accepte 2 arguments d'entrée :
1. Le texte qui se trouve au-dessus du widget de sélection, c'est-à-dire `'Quelle est votre couleur préférée ?'`
2. Les valeurs possibles à sélectionner parmi `('Blue', 'Red', 'Green')`

Enfin, nous imprimerons la couleur sélectionnée comme suit :
```python
st.write('Votre couleur préférée est ', option)
```

## Prochaines étapes
Maintenant que vous avez créé l'application Streamlit localement, il est temps de la déployer sur [Streamlit Cloud](https://streamlit.io/cloud).

## Références
En savoir plus sur [`st.selectbox`](https://docs.streamlit.io/library/api-reference/widgets/st.selectbox)