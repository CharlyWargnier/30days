# Composants Streamlit

Les composants sont des modules Python tiers qui étendent les possibilités de Streamlit [[1](https://docs.streamlit.io/library/components)].

## Quels composants Streamlit sont disponibles ?

Il existe plusieurs dizaines de composants Streamlit présentés sur le site Web de Streamlit [[2](https://streamlit.io/components)].

Fanilo (un créateur de Streamlit) a organisé une liste étonnante de composants Streamlit sur un article wiki [[3](https://discuss.streamlit.io/t/streamlit-components-community-tracker/4634)] qui répertorie environ 85 Streamlit composants à partir d'avril 2022.

## Comment utiliser?

Les composants Streamlit ne sont qu'à un pip d'installation.

Dans ce tutoriel, commençons à utiliser le composant `streamlit_pandas_profiling` [[4](https://share.streamlit.io/okld/streamlit-gallery/main?p=pandas-profiling)].

#### Installer le composant

```bash
pip install streamlit_pandas_profiling
```

## Application de démonstration

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/streamlit-components/)

##Code
Voici comment créer une application Streamlit à l'aide d'un composant :
```python
import streamlit as st
import pandas as pd
import pandas_profiling
depuis streamlit_pandas_profiling import st_profile_report

st.header('`streamlit_pandas_profiling`')

df = pd.read_csv('https://raw.githubusercontent.com/dataprofessor/data/master/penguins_cleaned.csv')

pr = df.profile_report()
st_profile_report(pr)
```

## Explication ligne par ligne
La toute première chose à faire lors de la création d'une application Streamlit est de commencer par import la bibliothèque `streamlit` as `st` ainsi que d'autres bibliothèques utilisées dans l'application comme ceci :
```python
import streamlit as st
import pandas as pd
import pandas_profiling
depuis streamlit_pandas_profiling import st_profile_report
```

Ceci est suivi par la création d'un texte d'en-tête pour l'application :
```python
st.header('`streamlit_pandas_profiling`')
```

Ensuite, nous chargeons le jeu de données Penguins à l'aide de la commande `read_csv` de `pandas`.
```python
df = pd.read_csv('https://raw.githubusercontent.com/dataprofessor/data/master/penguins_cleaned.csv')
```

Enfin, le rapport de profilage pandas est généré via la commande `profile_report()` et affiché à l'aide de `st_profile_report` :
```python
pr = df.profile_report()
st_profile_report(pr)
```

## Fabriquez vos propres composants

Si vous souhaitez créer votre propre composant, veuillez consulter les ressources suivantes :
- [Créer un composant](https://docs.streamlit.io/library/components/create)
- [Publier un composant](https://docs.streamlit.io/library/components/publish)
- [API des composants] (https://docs.streamlit.io/library/components/components-api)
- [Article de blog sur les composants] (https://blog.streamlit.io/introducing-streamlit-components/)

Alternativement, si vous préférez apprendre à l'aide de vidéos, notre ingénieur Tim Conkling a mis en place des tutoriels incroyables :
- [Comment construire un composant Streamlit | Partie 1 : Configuration et architecture](https://youtu.be/BuD3gILJW-Q)
- [Comment construire un composant Streamlit | Partie 2 : Partie 2 : Créer un widget Slider](https://youtu.be/QjccJl_7Jco)

## En savoir plus sur les composants
1. [Composants Streamlit - Documentation API](https://docs.streamlit.io/library/components)
2. [Composants Streamlit en vedette] (https://streamlit.io/components)
3. [Composants Streamlit - Community Tracker](https://discuss.streamlit.io/t/streamlit-components-community-tracker/4634)
4. [`streamlit_pandas_profiling`](https://share.streamlit.io/okld/streamlit-gallery/main?p=pandas-profiling)