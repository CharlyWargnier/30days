# Construire un tableau de bord déplaçable et redimensionnable avec Streamlit Elements

Streamlit Elements est un composant tiers créé par [okld](https://github.com/okld) qui vous donne les outils pour composer de belles applications et tableaux de bord avec les widgets Material UI, l'éditeur Monaco (Visual Studio Code), les graphiques Nivo , et plus.

## Comment utiliser?

###Installation

La première étape consiste à installer Streamlit Elements dans votre environnement :

```bash
pip install streamlit-elements==0.1.*
```

Il est recommandé d'épingler la version à `0.1.*`, car les futures versions pourraient introduire des changements d'API avec rupture.

### Utilisation

Vous pouvez vous référer à [Streamlit Elements README](https://github.com/okld/streamlit-elements#getting-started) pour un guide d'utilisation détaillé.

## Que construisons-nous ?

L'objectif du défi d'aujourd'hui est de créer un tableau de bord composé de trois cartes Material UI :

- Une première carte avec un éditeur de code Monaco pour saisir certaines données ;
- Une seconde carte pour afficher ces données dans un graphique Nivo Bump ;
- Une troisième carte pour afficher une URL de vidéo YouTube définie avec un `st.text_input`.

Vous pouvez y utiliser les données générées à partir de la démo de Nivo Bump, dans l'onglet 'data' : https://nivo.rocks/bump/.

## Application de démonstration

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/okld/streamlit-elements-demo/main)

## Code avec explication ligne par ligne

```python
# Tout d'abord, nous aurons besoin des importations suivantes pour notre application.

import json
import streamlit as st
à partir du chemin d'importation pathlib

# Comme pour Streamlit Elements, nous aurons besoin de tous ces objets.
# Tous les objets disponibles et leur utilisation y sont répertoriés : https://github.com/okld/streamlit-elements#getting-started

à partir de streamlit_elements import des éléments, tableau de bord, mui, éditeur, média, paresseux, synchroniser, nivo

# Modifiez la mise en page pour que le tableau de bord occupe toute la page.

st.set_page_config(layout="wide")

avec st.sidebar :
    st.title("🗓️ #30DaysOfStreamlit")
    st.header("Jour 27 - Éléments Streamlit")
    st.write("Construisez un tableau de bord déplaçable et redimensionnable avec Streamlit Elements.")
    st.write("---")

    # Définir l'URL du lecteur multimédia.
    media_url = st.text_input("URL du média", value="https://www.youtube.com/watch?v=vIQQR_yq-8I")

# Initialiser les données par défaut pour l'éditeur de code et le graphique.
#
# Pour ce tutoriel, nous aurons besoin de données pour un graphique Nivo Bump.
# Vous pouvez y obtenir des données aléatoires, dans l'onglet 'data' : https://nivo.rocks/bump/
#
# Comme vous le verrez ci-dessous, cet élément d'état de session sera mis à jour lorsque notre
# modification de l'éditeur de code, et il sera lu par le graphique Nivo Bump pour dessiner les données.

si "data" n'est pas dans st.session_state :
    st.session_state.data = Path("data.json").read_text()

# Définissez une disposition de tableau de bord par défaut.
# La grille du tableau de bord a 12 colonnes par défaut.
#
# Pour plus d'informations sur les paramètres disponibles :
# https://github.com/react-grid-layout/react-grid-layout#grid-item-props

mise en page = [
    # L'élément de l'éditeur est positionné aux coordonnées x=0 et y=0, et prend 6/12 colonnes et a une hauteur de 3.
    tableau de bord.Item("éditeur", 0, 0, 6, 3),
    # L'élément de graphique est positionné aux coordonnées x=6 et y=0, et prend 6/12 colonnes et a une hauteur de 3.
    tableau de bord.Item("graphique", 6, 0, 6, 3),
    # L'élément multimédia est positionné aux coordonnées x=0 et y=3, et prend 6/12 colonnes et a une hauteur de 4.
    tableau de bord.Item("média", 0, 2, 12, 4),
]

# Créer un cadre pour afficher les éléments.

avec éléments("démo") :

    # Créez un nouveau tableau de bord avec la mise en page spécifiée ci-dessus.
    #
    # draggableHandle est un sélecteur de requête CSS pour définir la partie déplaçable de chaque élément du tableau de bord.
    # Ici, les éléments avec un nom de classe "déplaçable" seront déplaçables.
    #
    # Pour plus d'informations sur les paramètres disponibles pour la grille du tableau de bord :
    # https://github.com/react-grid-layout/react-grid-layout#grid-layout-props
    # https://github.com/react-grid-layout/react-grid-layout#responsive-grid-layout-props

    avec dashboard.Grid(layout, draggableHandle=".draggable") :

        # Première carte, l'éditeur de code.
        #
        # Nous utilisons le paramètre 'key' pour identifier l'élément de tableau de bord correct.
        #
        # Pour que le contenu de la carte remplisse automatiquement la hauteur disponible, nous utiliserons CSS flexbox.
        # sx est un paramètre disponible avec chaque widget Material UI pour définir les attributs CSS.
        #
        # Pour plus d'informations concernant Card, flexbox et sx :
        # https://mui.com/components/cards/
        # https://mui.com/system/flexbox/
        # https://mui.com/system/the-sx-prop/

        avec mui.Card(key="editor", sx={"display": "flex", "flexDirection": "column"}) :

            # Pour rendre cet en-tête déplaçable, il suffit de définir son nom de classe sur 'draggable',
            # tel que défini ci-dessus dans le draggableHandle de dashboard.Grid.

            mui.CardHeader(title="Editor", className="glissable")

            # Nous voulons que le contenu de la carte prenne toute la hauteur disponible en définissant la valeur flex CSS sur 1.
            # Nous voulons également que le contenu de la carte soit réduit lorsque la carte est réduite en définissant minHeight sur 0.

            avec mui.CardContent(sx={"fl