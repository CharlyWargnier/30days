# Comment mettre en page votre application Streamlit

Dans ce tutoriel, nous allons utiliser les commandes suivantes pour mettre en page notre application Streamlit :
- `st.set_page_config(layout="wide")` - Affiche le contenu de l'application en mode large (sinon par défaut, le contenu est encapsulé dans une boîte à largeur fixe.
- `st.sidebar` - Place les widgets ou les affichages texte/image dans la barre latérale.
- `st.expander` - Place les affichages de texte/image dans une boîte de conteneur pliable.
- `st.columns` - Crée un espace tabulaire (ou colonne) dans lequel le contenu peut être placé à l'intérieur.

## Application de démonstration

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/streamlit-layout/)

##Code
Voici comment personnaliser la mise en page de votre application Streamlit :
```python
import streamlit as st

st.set_page_config(layout="wide")

st.title('Comment mettre en page votre application Streamlit')

with st.expander('About this app'):
  st.write('Cette application montre les différentes manières de mettre en page votre application Streamlit.')
  st.image('https://streamlit.io/images/brand/streamlit-logo-secondary-colormark-darktext.png', width=250)

st.sidebar.header('Entrée')
user_name = st.sidebar.text_input('Quel est votre nom ?')
user_emoji = st.sidebar.selectbox('Choisissez un emoji', ['', '😄', '😆', '😊', '😍', '😴', '😕', '😱'])
user_food = st.sidebar.selectbox('Quel est votre plat préféré ?', ['', 'Tom Yum Kung', 'Burrito', 'Lasagne', 'Hamburger', 'Pizza'])

st.header('Sortie')

col1, col2, col3 = st.columns(3)

avec col1 :
  si nom_utilisateur != '' :
    st.write(f'👋 Bonjour {user_name} !')
  autre:
    st.write('👈 Veuillez entrer votre **nom** !')

avec col2 :
  si user_emoji != '' :
    st.write(f'{user_emoji} est votre **emoji** préféré !')
  autre:
    st.write('👈 Veuillez choisir un **emoji** !')

avec col3 :
  si user_food != '' :
    st.write(f'🍴 **{user_food}** est votre **nourriture** préférée !')
  autre:
    st.write('👈 Veuillez choisir votre **nourriture** préférée !')
```

## Explication ligne par ligne
La toute première chose à faire lors de la création d'une application Streamlit est de commencer par import la bibliothèque `streamlit` as `st` comme ceci :
```python
import streamlit as st
```

Nous commencerons par définir d'abord la mise en page à afficher en mode "large", qui permet au contenu de la page de s'étendre à la largeur du navigateur.
```python
st.set_page_config(layout="wide")
```

Ensuite, nous donnerons un titre à l'application Streamlit.
```python
st.title('Comment mettre en page votre application Streamlit')
```

Une zone extensible intitulée "À propos de cette application" est placée sous le titre de l'application. Lors de l'expansion, nous verrons des détails supplémentaires à l'intérieur.
```python
with st.expander('About this app'):
  st.write('Cette application montre les différentes manières de mettre en page votre application Streamlit.')
  st.image('https://streamlit.io/images/brand/streamlit-logo-secondary-colormark-darktext.png', width=250)
```

Les widgets d'entrée pour accepter l'entrée de l'utilisateur sont placés dans la barre latérale comme spécifié en utilisant la commande `st.sidebar` avant les commandes Streamlit `text_input` et `selectbox`. Les valeurs d'entrée saisies ou sélectionnées par l'utilisateur sont affectées et stockées dans les variables `user_name`, `user_emoji` et `user_food`.
```python
st.sidebar.header('Entrée')
user_name = st.sidebar.text_input('Quel est votre nom ?')
user_emoji = st.sidebar.selectbox('Choisissez un emoji', ['', '😄', '😆', '😊', '😍', '😴', '😕', '😱'])
user_food = st.sidebar.selectbox('Quel est votre plat préféré ?', ['', 'Tom Yum Kung', 'Burrito', 'Lasagne', 'Hamburger', 'Pizza'])
```

Enfin, nous allons créer 3 colonnes à l'aide de la commande `st.columns` qui correspond à `col1`, `col2` et `col3`. Ensuite, nous attribuons un contenu à chacune des colonnes en créant des blocs de code individuels commençant par l'instruction `with`. En dessous, nous créons des instructions conditionnelles qui affichent 1 texte alternatif sur 2 selon que l'utilisateur a fourni ses données d'entrée (spécifiées dans la barre latérale) ou non. Par défaut, la page affiche le texte sous l'instruction `else`. Lors de la saisie de l'utilisateur, les informations correspondantes que l'utilisateur donne à l'application sont affichées sous le texte d'en-tête "Sortie".
```python
st.header('Sortie')

col1, col2, col3 = st.columns(3)

avec col1 :
  si nom_utilisateur != '' :
    st.write(f'👋 Bonjour {user_name} !')
  autre:
    st.write('👈 Veuillez entrer votre **nom** !')

avec col2 :
  si user_emoji != '' :
    st.write(f'{user_emoji} est votre **emoji** préféré !')
  autre:
    st.write('👈 Veuillez choisir un **emoji** !')

avec col3 :
  si user_food != '' :
    st.write(f'🍴 **{user_food}** est votre **nourriture** préférée !')
  autre:
    st.write('👈 Veuillez choisir votre **nourriture** préférée !')
```
Il convient également de noter que les chaînes "f" ont été utilisées pour combiner le texte pré-enregistré avec les valeurs fournies par l'utilisateur.

## Lectures complémentaires
- [Mises en page et conteneurs](https://docs.streamlit.io/library/api-reference/layout)