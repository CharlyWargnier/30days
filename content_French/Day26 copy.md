# Comment utiliser l'API en créant l'application Bored API

L'application Bored API vous suggère des choses amusantes à faire lorsque vous vous ennuyez !

Techniquement, il démontre également l'utilisation des API à partir d'une application Streamlit.

## Application de démonstration

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/bored-api-app/)

##Code
Voici comment implémenter l'application Bored-API :
```python
importer streamlit en tant que st
demandes d'importation

st.title('🏀 Application API ennuyée')

st.sidebar.header('Entrée')
selected_type = st.sidebar.selectbox('Sélectionnez un type d'activité', ["éducation", "loisir", "social", "bricolage", "charité", "cuisine", "relaxation", "musique", "travail occupé "])

suggéré_activity_url = f'http://www.boredapi.com/api/activity?type={selected_type}'
json_data = demandes.get(suggested_activity_url)
activité_suggérée = json_data.json()

c1, c2 = st.colonnes(2)
avec c1 :
  with st.expander('About this app'):
    st.write('Vous ennuyez-vous ? L'application **Bored API** fournit des suggestions d'activités que vous pouvez faire lorsque vous vous ennuyez. Cette application est alimentée par l'API Bored.')
avec c2 :
  avec st.expander('Données JSON'):
    st.write(activité_suggérée)
    
st.header('Activité suggérée')
st.info(activité_suggérée['activité'])

col1, col2, col3 = st.columns(3)
avec col1 :
  st.metric(label='Nombre de participants', value=suggested_activity['participants'], delta='')
avec col2 :
  st.metric(label='Type of Activity', value=suggested_activity['type'].capitalize(), delta='')
avec col3 :
  st.metric(label='Price', value=suggested_activity['price'], delta='')
```

## Explication ligne par ligne
La toute première chose à faire lors de la création d'une application Streamlit est de commencer par importer la bibliothèque `streamlit` en tant que `st` et la bibliothèque `requests` comme suit :
```python
importer streamlit en tant que st
demandes d'importation
```

Le titre de l'application est affiché via `st.title` :
```python
st.title('🏀 Application API ennuyée')
```

Ensuite, nous accepterons la saisie de l'utilisateur sur le **type d'activité** au moyen de la commande `st.selectbox` :
```python
st.sidebar.header('Entrée')
selected_type = st.sidebar.selectbox('Sélectionnez un type d'activité', ["éducation", "loisir", "social", "bricolage", "charité", "cuisine", "relaxation", "musique", "travail occupé "])
```

L'activité sélectionnée mentionnée ci-dessus est ensuite ajoutée à l'URL via une f-string, qui est ensuite utilisée pour récupérer les données JSON résultantes :
```python
suggéré_activity_url = f'http://www.boredapi.com/api/activity?type={selected_type}'
json_data = demandes.get(suggested_activity_url)
activité_suggérée = json_data.json()
```

Ici, nous afficherons des informations sur l'application et les données JSON via la commande `st.expander`.
```python
c1, c2 = st.colonnes(2)
avec c1 :
  with st.expander('About this app'):
    st.write('Vous ennuyez-vous ? L'application **Bored API** fournit des suggestions d'activités que vous pouvez faire. Cette application est alimentée par l'API Bored.')
avec c2 :
  avec st.expander('Données JSON'):
    st.write(activité_suggérée)
```

Nous afficherons ensuite une activité suggérée comme celle-ci :
```python
st.header('Activité suggérée')
st.info(activité_suggérée['activité'])
```

Enfin, nous afficherons également les informations d'accompagnement de l'activité suggérée telles que le `Nombre de participants`, le `Type d'activité` et le `Prix`.
```python
col1, col2, col3 = st.columns(3)
avec col1 :
  st.metric(label='Nombre de participants', value=suggested_activity['participants'], delta='')
avec col2 :
  st.metric(label='Type of Activity', value=suggested_activity['type'].capitalize(), delta='')
avec col3 :
  st.metric(label='Price', value=suggested_activity['price'], delta='')
```

## Lectures complémentaires
- [API ennuyée] (http://www.boredapi.com/)