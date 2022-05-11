# st.session_state

Nous définissons l'accès à une application Streamlit dans un onglet de navigateur comme une session. Pour chaque onglet du navigateur qui se connecte au serveur Streamlit, une nouvelle session est créée. Streamlit réexécute votre script de haut en bas chaque fois que vous interagissez avec votre application. Chaque rediffusion a lieu dans une ardoise vierge : aucune variable n'est partagée entre les exécutions.

L'état de session est un moyen de partager des variables entre les réexécutions, pour chaque session utilisateur. En plus de la possibilité de stocker et de conserver l'état, Streamlit expose également la possibilité de manipuler l'état à l'aide de rappels.

Dans ce didacticiel, nous allons illustrer l'utilisation de l'état de session et des rappels lors de la création d'une application de conversion de poids.

`st.session_state` permet l'implémentation de l'état de session dans une application Streamlit.

## Application de démonstration

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.session_state/)

##Code
Voici comment utiliser `st.session_state` :
```python
importer streamlit en tant que st

st.title('st.session_state')

def lbs_to_kg() :
  st.session_state.kg = st.session_state.lbs/2.2046
def kg_to_lbs() :
  st.session_state.lbs = st.session_state.kg*2.2046

st.header('Entrée')
col1, espaceur, col2 = st.columns([2,1,2])
avec col1 :
  livres = st.number_input("Livres :", key = "lbs", on_change = lbs_to_kg)
avec col2 :
  kilogramme = st.number_input("Kilogrammes :", key = "kg", on_change = kg_to_lbs)

st.header('Sortie')
st.write("objet st.session_state : ", st.session_state)
```

## Explication ligne par ligne
La toute première chose à faire lors de la création d'une application Streamlit est de commencer par importer la bibliothèque `streamlit` en tant que `st` comme ceci :
```python
importer streamlit en tant que st
```

Tout d'abord, nous allons commencer par créer le titre de l'application :
```python
st.title('st.session_state')
```

Ensuite, nous définissons des fonctions personnalisées pour la conversion du poids de lbs en kg et vice versa :
```python
def lbs_to_kg() :
  st.session_state.kg = st.session_state.lbs/2.2046
def kg_to_lbs() :
  st.session_state.lbs = st.session_state.kg*2.2046
```

Ici, nous utilisons `st.number_input` pour accepter les entrées numériques des valeurs de poids :
```python
st.header('Entrée')
col1, espaceur, col2 = st.columns([2,1,2])
avec col1 :
  livres = st.number_input("Livres :", key = "lbs", on_change = lbs_to_kg)
avec col2 :
  kilogramme = st.number_input("Kilogrammes :", key = "kg", on_change = kg_to_lbs)
```
Les 2 fonctions personnalisées ci-dessus seront appelées dès qu'une valeur numérique sera entrée dans la zone numérique créée à l'aide de la commande `st.number_input`. Remarquez comment l'option `on_change` spécifie les 2 fonctions personnalisées `lbs_to_kg` et `kg_to_lbs`).

En un mot, lors de la saisie d'un nombre dans la case `st.number_input`, le nombre est converti par ces fonctions personnalisées.

Enfin, les valeurs de poids en unités `kg` et `lbs` telles que stockées dans l'état de session sous `st.session_state.kg` et `st.session_state.lbs` seront imprimées via `st.write` :
```python
st.header('Sortie')
st.write("objet st.session_state : ", st.session_state)
```

## Lectures complémentaires
- [État de la session] (https://docs.streamlit.io/library/api-reference/session-state)
- [Ajouter un état aux applications] (https://docs.streamlit.io/library/advanced-features/session-state)