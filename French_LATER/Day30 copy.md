# L'art de créer des applications Streamlit

Aujourd'hui, jour 30 du défi *#30DaysOfStreamlit*. Félicitations pour avoir fait ce chemin dans le défi.

Dans ce didacticiel, nous allons mettre à profit nos nouvelles connaissances acquises grâce à ce défi d'apprentissage pour créer des applications Streamlit afin de résoudre des problèmes réels.

## Problème du monde réel

as créateur de contenu, l'accès aux images miniatures des vidéos YouTube est une ressource utile pour la promotion sociale et la création de contenu.

Voyons comment nous allons résoudre ce problème et créer une application Streamlit.

## Solution

Aujourd'hui, nous allons créer `yt-img-app`, qui est une application Streamlit capable d'extraire des images miniatures de vidéos YouTube.

En un mot, voici les 3 étapes simples que nous voulons que l'application Streamlit fasse :

1. Acceptez une URL YouTube comme entrée des utilisateurs
2. Effectuez un traitement de texte de l'URL pour extraire l'ID vidéo YouTube unique
3. Utilisez l'ID vidéo YouTube comme entrée pour une fonction personnalisée qui récupère et affiche l'image miniature des vidéos YouTube

## Des instructions

Pour commencer à utiliser l'application Streamlit, copiez et collez une URL YouTube dans la zone de saisie de texte.

## Application de démonstration

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/yt-img-app/)

##Code
Voici comment créer l'application Streamlit `yt-img-app` :
```python
import streamlit as st

st.title('🖼️ yt-img-app')
st.header('Application d'extraction d'images miniatures YouTube')

with st.expander('About this app'):
  st.write('Cette application récupère l'image miniature d'une vidéo YouTube.')
  
# Paramètres des images
st.sidebar.header('Paramètres')
img_dict = {'Max' : 'maxresdefault', 'Élevé' : 'hqdefault', 'Moyen' : 'mqdefault', 'Standard' : 'sddefault'}
selected_img_quality = st.sidebar.selectbox('Sélectionner la qualité d'image', ['Max', 'Elevé', 'Moyen', 'Standard'])
img_quality = img_dict[selected_img_quality]

yt_url = st.text_input('Coller l'URL YouTube', 'https://youtu.be/JwSS70SZdyM')

def get_ytid(input_url):
  si 'youtu.be' dans input_url :
    ytid = input_url.split('/')[-1]
  si 'youtube.com' dans input_url :
    ytid = input_url.split('=')[-1]
  retour ytid
    
# Afficher l'image miniature YouTube
si yt_url != '' :
  ytid = get_ytid(yt_url) # yt ou yt_url

  yt_img = f'http://img.youtube.com/vi/{ytid}/{img_quality}.jpg'
  st.image(yt_img)
  st.write('URL de l'image miniature de la vidéo YouTube : ', yt_img)
autre:
  st.write('☝️ Entrez l'URL pour continuer ...')
```

## Explication ligne par ligne
La toute première chose à faire lors de la création d'une application Streamlit est de commencer par import la bibliothèque `streamlit` as `st` comme ceci :
```python
import streamlit as st
```

Ensuite, nous affichons le titre de l'application et l'en-tête qui l'accompagne :
```python
st.title('🖼️ yt-img-app')
st.header('Application d'extraction d'images miniatures YouTube')
```
Pendant que nous y sommes, autant ajouter une boîte extensible À propos.
```python
with st.expander('About this app'):
  st.write('Cette application récupère l'image miniature d'une vidéo YouTube.')
 
Ici, nous créons une boîte de sélection pour accepter les entrées de l'utilisateur sur la qualité d'image à utiliser.
```python
# Paramètres des images
st.sidebar.header('Paramètres')
img_dict = {'Max' : 'maxresdefault', 'Élevé' : 'hqdefault', 'Moyen' : 'mqdefault', 'Standard' : 'sddefault'}
selected_img_quality = st.sidebar.selectbox('Sélectionner la qualité d'image', ['Max', 'Elevé', 'Moyen', 'Standard'])
img_quality = img_dict[selected_img_quality]
```

Une zone de saisie de texte s'affiche pour accepter la saisie de l'utilisateur sur l'URL de la vidéo YouTube à utiliser pour extraire l'image.
```python
yt_url = st.text_input('Coller l'URL YouTube', 'https://youtu.be/JwSS70SZdyM')
```

Une fonction personnalisée pour effectuer le traitement de texte de l'URL d'entrée.
```python
def get_ytid(input_url):
  si 'youtu.be' dans input_url :
    ytid = input_url.split('/')[-1]
  si 'youtube.com' dans input_url :
    ytid = input_url.split('=')[-1]
  retour ytid
```

Enfin, nous utilisons le contrôle de flux pour déterminer s'il faut afficher un rappel pour entrer l'URL (c'est-à-dire comme dans l'instruction `else`) ou pour afficher l'image miniature YouTube (c'est-à-dire comme dans l'instruction `if`).
```python
# Afficher l'image miniature YouTube
si yt_url != '' :
  ytid = get_ytid(yt_url) # yt ou yt_url

  yt_img = f'http://img.youtube.com/vi/{ytid}/{img_quality}.jpg'
  st.image(yt_img)
  st.write('URL de l'image miniature de la vidéo YouTube : ', yt_img)
autre:
  st.write('☝️ Entrez l'URL pour continuer ...')
```

## Résumé

En résumé, nous avons vu que lors de la création de toute application Streamlit, nous commençons normalement par identifier et définir le problème. Ensuite, nous concevons une solution pour résoudre le problème en le décomposant en étapes granulaires, que nous implémentons dans l'application Streamlit.

Ici, nous devons également déterminer les données ou informations dont nous avons besoin comme entrée des utilisateurs, l'approche et la méthode à utiliser pour traiter l'entrée de l'utilisateur afin de produire le résultat final souhaité.

J'espère que vous avez apprécié ce tutoriel, Happy Streamlit-ing !