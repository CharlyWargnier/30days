# Personnalisation du thème des applications Streamlit

Nous pouvons personnaliser le thème en ajustant les paramètres dans `config.toml`, qui est un fichier de configuration stocké dans le même dossier que l'application dans le dossier `.streamlit`.

## Qu'est-ce que nous construisons ?

Une application simple qui montre le résultat de notre personnalisation de thème. Ceci est rendu possible en personnalisant le code HTML HEX à l'intérieur du [`.streamlit/config.toml`](https://github.com/dataprofessor/streamlit-custom-theme/blob/master/.streamlit/config.toml) dossier.

## Application de démonstration

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/streamlit-custom-theme/)

##Code
Voici le code du fichier [`streamlit_app.py`](https://github.com/dataprofessor/streamlit-custom-theme/blob/master/streamlit_app.py) :
```python
importer streamlit en tant que st

st.title('Personnalisation du thème des applications Streamlit')

st.write('Contenu du fichier `.streamlit/config.toml` de cette application')

st.code("""
[thème]
CouleurPrimaire="#F39C12"
backgroundColor="#2E86C1"
SecondaryBackgroundColor="#AED6F1"
textColor="#FFFFFF"
font="monospace"
""")

number = st.sidebar.slider('Sélectionnez un nombre :', 0, 10, 5)
st.write('Le nombre sélectionné dans le widget slider est :', nombre)
```

Voici le code du fichier [`.streamlit/config.toml`](https://github.com/dataprofessor/streamlit-custom-theme/blob/master/.streamlit/config.toml) :
```python
[thème]
CouleurPrimaire="#F39C12"
backgroundColor="#2E86C1"
SecondaryBackgroundColor="#AED6F1"
textColor="#FFFFFF"
font="monospace"
```

## Explication ligne par ligne
La toute première chose à faire lors de la création d'une application Streamlit est de commencer par importer la bibliothèque `streamlit` en tant que `st` comme ceci :
```python
importer streamlit en tant que st
```

Ceci est suivi par la création d'un texte de titre pour l'application :
```python
st.title('Thématisation avec config.toml')
```

Ensuite, nous allons montrer le contenu du fichier `.streamlit/config.toml` dont nous allons d'abord afficher une note via `st.write` suivi du code réel via `st.code` :
```python
st.write('Contenu du fichier ./streamlit/config.toml de cette application')

st.code("""
[thème]
CouleurPrimaire="#F39C12"
backgroundColor="#2E86C1"
SecondaryBackgroundColor="#AED6F1"
textColor="#FFFFFF"
font="monospace"
""")
```

Enfin, nous créons un widget de curseur dans la barre latérale suivi de l'affichage du nombre sélectionné :
```python
number = st.sidebar.slider('Sélectionnez un nombre :', 0, 10, 5)
st.write('Le nombre sélectionné dans le widget slider est :', nombre)
```

Examinons maintenant les couleurs personnalisées que nous avons utilisées dans cette application, qui sont spécifiées dans le fichier `.streamlit/config.toml` :
- `primaryColor="#F39C12"` - Cela définit la couleur primaire sur orange. Remarquez les couleurs orange dans le widget du curseur.
- `backgroundColor="#2E86C1"` - Cela définit la couleur d'arrière-plan sur le bleu. Notez que le panneau principal a une couleur de fond bleue.
- `secondaryBackgroundColor="#AED6F1"` - Cela définit la couleur d'arrière-plan secondaire sur gris foncé. Remarquez la couleur d'arrière-plan grise de la barre latérale et la couleur d'arrière-plan de la zone de code dans le panneau principal.
- `textColor="#FFFFFF"` - La couleur du texte est définie sur blanc.
- `font="monospace"` - Cela définit la police sur monospace.


## Lectures complémentaires
- [Theming](https://docs.streamlit.io/library/advanced-features/theming)
- [HTML Color Codes](https://htmlcolorcodes.com/) est un excellent outil pour sélectionner les couleurs qui vous intéressent.