# st.experimental_get_query_params

`st.experimental_get_query_params` permet la récupération des paramètres de requête directement à partir de l'URL du navigateur de l'utilisateur.

## Application de démonstration

1. Le lien suivant charge l'application de démonstration sans paramètres de requête (notez le message d'erreur) :

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.experimental_get_query_params/)

2. Le lien suivant charge l'application de démonstration avec les paramètres de requête (pas de message d'erreur ici) :

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](http://share.streamlit.io/dataprofessor/st.experimental_get_query_params/?firstname=Jack&surname=Beanstalk)

##Code
Voici comment utiliser `st.experimental_get_query_params` :
```python
import streamlit as st

st.title('st.experimental_get_query_params')

with st.expander('About this app'):
  st.write("`st.experimental_get_query_params` permet la récupération des paramètres de requête directement à partir de l'URL du navigateur de l'utilisateur.")

# 1. Mode d'emploi
st.header('1. Instructions')
st.markdown('''
Dans la barre d'URL ci-dessus de votre navigateur Internet, ajoutez ce qui suit :
`?name=Jack&surname=Haricot magique`
après l'URL de base `http://share.streamlit.io/dataprofessor/st.experimental_get_query_params/`
telle qu'elle devienne
`http://share.streamlit.io/dataprofessor/st.experimental_get_query_params/?firstname=Jack&surname=Beanstalk`
''')


# 2. Contenu de st.experimental_get_query_params
st.header('2. Contenu de st.experimental_get_query_params')
st.write(st.experimental_get_query_params())


# 3. Récupérer et afficher les informations de l'URL
st.header('3. Récupérer et afficher les informations de l'URL')

prénom = st.experimental_get_query_params()['prenom'][0]
nom = st.experimental_get_query_params()['nom'][0]

st.write(f'Bonjour **{prénom} {nom}**, comment allez-vous ?')
```

## Explication ligne par ligne
La toute première chose à faire lors de la création d'une application Streamlit est de commencer par import la bibliothèque `streamlit` as `st` comme ceci :
```python
import streamlit as st
```

Ensuite, nous donnerons un titre à l'application :
```python
st.title('st.experimental_get_query_params')
```

Ajoutons également une liste déroulante À propos :
```python
with st.expander('About this app'):
  st.write("`st.experimental_get_query_params` permet la récupération des paramètres de requête directement à partir de l'URL du navigateur de l'utilisateur.")
```

Ensuite, nous fournirons des instructions aux visiteurs de l'application sur la façon dont ils peuvent transmettre les paramètres de requête directement à l'URL :
```python
# 1. Mode d'emploi
st.header('1. Instructions')
st.markdown('''
Dans la barre d'URL ci-dessus de votre navigateur Internet, ajoutez ce qui suit :
`?name=Jack&surname=Haricot magique`
après l'URL de base `http://share.streamlit.io/dataprofessor/st.experimental_get_query_params/`
telle qu'elle devienne
`http://share.streamlit.io/dataprofessor/st.experimental_get_query_params/?firstname=Jack&surname=Beanstalk`
''')
```

Par la suite, nous afficherons le contenu de la commande `st.experimental_get_query_params`.
```python
# 2. Contenu de st.experimental_get_query_params
st.header('2. Contenu de st.experimental_get_query_params')
st.write(st.experimental_get_query_params())
```

Enfin, nous sélectionnerons et afficherons des informations sélectives à partir du paramètre de requête de l'URL :
```python
# 3. Récupérer et afficher les informations de l'URL
st.header('3. Récupérer et afficher les informations de l'URL')

prénom = st.experimental_get_query_params()['prenom'][0]
nom = st.experimental_get_query_params()['nom'][0]

st.write(f'Bonjour **{prénom} {nom}**, comment allez-vous ?')
```

## Lectures complémentaires
- [`st.experimental_get_query_params`](https://docs.streamlit.io/library/api-reference/utilities/st.experimental_get_query_params)