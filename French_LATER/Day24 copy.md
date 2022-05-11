# st.cache

`st.cache` vous permet d'optimiser les performances de votre application Streamlit.

Streamlit fournit un mécanisme de mise en cache qui permet à votre application de rester performante même lors du chargement de données à partir du Web, de la manipulation de grands ensembles de données ou de l'exécution de calculs coûteux. Ceci est fait avec le décorateur `@st.cache`.

Lorsque vous marquez une fonction avec le décorateur @st.cache, il indique à Streamlit que chaque fois que la fonction est appelée, elle doit vérifier quelques éléments :

1. Les paramètres d'entrée avec lesquels vous avez appelé la fonction
2. La valeur de toute variable externe utilisée dans la fonction
3. Le corps de la fonction
4. Le corps de toute fonction utilisée dans la fonction mise en cache

Si c'est la première fois que Streamlit voit ces quatre composants avec ces valeurs exactes et dans cette combinaison et cet ordre exacts, il exécute la fonction et stocke le résultat dans un cache local. Ensuite, la prochaine fois que la fonction mise en cache est appelée, si aucun de ces composants n'a changé, Streamlit ignorera simplement l'exécution de la fonction et, à la place, renverra la sortie précédemment stockée dans le cache.

La façon dont Streamlit garde une trace des changements dans ces composants se fait par hachage. Considérez le cache comme un magasin clé-valeur en mémoire, où la clé est un hachage de tout ce qui précède et la valeur est l'objet de sortie réel passé par référence.

Enfin, `@st.cache` prend en charge les arguments pour configurer le comportement du cache. Vous pouvez trouver plus d'informations sur ceux-ci dans notre référence API.

## Comment utiliser?

Vous pouvez simplement ajouter le décorateur `st.cache` sur la ligne précédente d'une fonction personnalisée que vous définissez dans votre application Streamlit. Voir l'exemple ci-dessous.

## Application de démonstration

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.cache/)

##Code
Voici comment utiliser `st.cache` :
```python
import streamlit as st
import numpy as np
import pandas as pd
à partir du moment de l'importation

st.title('st.cache')

# Utiliser le cache
a0 = temps()
st.subheader('Utilisation de st.cache')

@st.cache(suppress_st_warning=True)
def load_data_a() :
  df = pd.DataFrame(
    np.random.rand(2000000, 5),
    colonnes=['a', 'b', 'c', 'd', 'e']
  )
  retour df

st.write(load_data_a())
a1 = temps()
st.info(a1-a0)


# Ne pas utiliser le cache
b0 = temps()
st.subheader('Ne pas utiliser st.cache')

def load_data_b() :
  df = pd.DataFrame(
    np.random.rand(2000000, 5),
    colonnes=['a', 'b', 'c', 'd', 'e']
  )
  retour df

st.write(load_data_b())
b1 = temps()
st.info(b1-b0)
```

## Explication ligne par ligne
La toute première chose à faire lors de la création d'une application Streamlit est de commencer par import la bibliothèque `streamlit` as `st` ainsi que d'autres bibliothèques utilisées dans l'application comme ceci :
```python
import streamlit as st
import numpy as np
import pandas as pd
à partir du moment de l'importation
```

Ceci est suivi par la création d'un texte de titre pour l'application :
```python
st.title('Streamlit Cache')
```

Ensuite, nous définirons 2 fonctions personnalisées pour générer un grand DataFrame où la première utilise le décorateur `st.cache` tandis que la seconde ne le fait pas :
```python
@st.cache(suppress_st_warning=True)
def load_data_a() :
  df = pd.DataFrame(
    np.random.rand(1000000, 5),
    colonnes=['a', 'b', 'c', 'd', 'e']
  )
  retour df

def load_data_b() :
  df = pd.DataFrame(
    np.random.rand(1000000, 5),
    colonnes=['a', 'b', 'c', 'd', 'e']
  )
  retour df
```

Enfin, nous exécutons la fonction personnalisée tout en chronométrant le temps d'exécution à l'aide de la commande `time()`.
```python
# Utiliser le cache
a0 = temps()
st.subheader('Utilisation de st.cache')

# Nous insérons ici la fonction load_data_a

st.write(load_data_a())
a1 = temps()
st.info(a1-a0)

# Ne pas utiliser le cache
b0 = temps()
st.subheader('Ne pas utiliser st.cache')

# Nous insérons ici la fonction load_data_b

st.write(load_data_b())
b1 = temps()
st.info(b1-b0)
```

Remarquez comment la première exécution peut fournir un temps d'exécution à peu près similaire. Rechargez l'application et notez comment le temps d'exécution change lorsque vous utilisez le décorateur `st.cache`. Avez-vous observé une augmentation de la vitesse ?

## Lectures complémentaires
- [Documentation API `st.cache`](https://docs.streamlit.io/library/api-reference/performance/st.cache)
- [Optimiser les performances avec `st.cache`](https://docs.streamlit.io/library/advanced-features/caching)
- [Primitives de cache expérimentales] (https://docs.streamlit.io/library/advanced-features/experimental-cache-primitives)
- [`st.experimental_memo`](https://docs.streamlit.io/library/api-reference/performance/st.experimental_memo)
- [`st.experimental_singleton`](https://docs.streamlit.io/library/api-reference/performance/st.experimental_singleton)