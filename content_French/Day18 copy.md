# st.file_uploader

`st.file_uploader` affiche un widget de téléchargement de fichiers [[1](https://docs.streamlit.io/library/api-reference/widgets/st.file_uploader)].

Par défaut, les fichiers téléchargés sont limités à 200 Mo. Vous pouvez le configurer à l'aide de l'option de configuration server.maxUploadSize. Pour plus d'informations sur la définition des options de configuration, consultez [[2](https://docs.streamlit.io/library/advanced-features/configuration#set-configuration-options)].

## Application de démonstration

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.file_uploader/)

##Code
Voici comment utiliser `st.file_uploader` :
```python
importer streamlit en tant que st
importer des pandas en tant que pd

st.title('st.file_uploader')

st.subheader('Entrée CSV')
upload_file = st.file_uploader("Choisir un fichier")

si uploaded_file n'est pas None :
  df = pd.read_csv(téléchargé_fichier)
  st.subheader('DataFrame')
  st.écrire (df)
  st.subheader('Statistiques descriptives')
  st.write(df.describe())
autre:
  st.info('☝️ Téléchargez un fichier CSV')
```

## Explication ligne par lignea
La toute première chose à faire lors de la création d'une application Streamlit est de commencer par importer la bibliothèque `streamlit` en tant que `st` et d'autres bibliothèques prérequises comme suit :
```python
importer streamlit en tant que st
importer des pandas en tant que pd
```

Ceci est suivi par la création d'un texte de titre pour l'application :
```python
st.title('st.file_uploader')
```

Ensuite, nous utiliserons `st.file_uploader` pour afficher un widget de téléchargement de fichiers pour accepter le fichier d'entrée utilisateur :
```python
st.subheader('Entrée CSV')
upload_file = st.file_uploader("Choisir un fichier")
```

Enfin, nous définissons des instructions conditionnelles pour afficher initialement un message de bienvenue invitant les utilisateurs à télécharger leur fichier (comme implémenté dans la condition `else`). Lors du téléchargement du fichier, les instructions "if" sont activées et le fichier CSV est lu par la bibliothèque "pandas" et affiché via la commande "st.write".
```python
si uploaded_file n'est pas None :
  df = pd.read_csv(téléchargé_fichier)
  st.subheader('DataFrame')
  st.écrire (df)
  st.subheader('Statistiques descriptives')
  st.write(df.describe())
autre:
  st.info('☝️ Téléchargez un fichier CSV')
```

## Lectures complémentaires
1. [`st.file_uploader`](https://docs.streamlit.io/library/api-reference/widgets/st.file_uploader)
2. [Définir les options de configuration](https://docs.streamlit.io/library/advanced-features/configuration#set-configuration-options)