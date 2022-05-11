# streamlit-shap

[`streamlit-shap`](https://github.com/snehankekre/streamlit-shap) est un composant Streamlit qui fournit un wrapper pour afficher les tracés [SHAP](https://github.com/slundberg/shap) dans [Streamlit](https://streamlit.io/).

La bibliothèque est développée par notre personnel interne [Snehan Kekre](https://github.com/snehankekre) qui gère également le site Web [Streamlit Documentation](https://docs.streamlit.io/).

Tout d'abord, installez Streamlit (bien sûr !) puis pip installez la bibliothèque `streamlit-shap` :
```bash
pip install streamlit
pip install streamlit-shap
```

Il existe également d'autres bibliothèques prérequises à installer (par exemple, `matplotlib`, `pandas`, `scikit-learn` et `xgboost`) si vous ne l'avez pas encore fait.


## Application de démonstration

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/streamlit-shap/)

##Code
Voici comment utiliser `streamlit-shap` :
```python
import streamlit as st
depuis streamlit_shap import st_shap
forme d'importation
depuis sklearn.model_selection import train_test_split
import xgboost
import numpy as np
import pandas as pd

st.set_page_config(layout="wide")

@st.experimental_memo
def load_data() :
    retourner shap.datasets.adult()

@st.experimental_memo
def load_model(X, y):
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=7)
    d_train = xgboost.DMatrix(X_train, label=y_train)
    d_test = xgboost.DMatrix(X_test, label=y_test)
    paramètres = {
        "eta": 0.01,
        "objective": "binary:logistique",
        "sous-échantillon": 0,5,
        "base_score": np.mean(y_train),
        "eval_metric": "logloss",
        "n_jobs": -1,
    }
    model = xgboost.train(params, d_train, 10, evals = [(d_test, "test")], verbose_eval=100, early_stopping_rounds=20)
    modèle de retour

st.title("`streamlit-shap` pour afficher les tracés SHAP dans une application Streamlit")

with st.expander('About the app'):
    st.markdown('''[`streamlit-shap`](https://github.com/snehankekre/streamlit-shap) est un composant Streamlit qui fournit un wrapper pour afficher [SHAP](https://github.com /slundberg/shap) tracés dans [Streamlit](https://streamlit.io/).
                    La bibliothèque est développée par notre personnel interne [Snehan Kekre](https://github.com/snehankekre) qui gère également le site Web [Streamlit Documentation](https://docs.streamlit.io/).
                ''')

st.header('Données d'entrée')
X,y = load_data()
X_display,y_display = shap.datasets.adult(display=True)

with st.expander('A propos des données'):
    st.write('Les données du recensement des adultes sont utilisées comme exemple de jeu de données.')
avec st.expander('X'):
    st.dataframe(X)
avec st.expander('y'):
    st.dataframe(y)

st.header('Sortie SHAP')
 
# former le modèle XGBoost
modèle = load_model(X, y)

# calculer les valeurs SHAP
explicateur = shap.Explainer(modèle, X)
shap_values ​​= explicateur(X)

with st.expander('Waterfall plot'):
    st_shap(shap.plots.waterfall(shap_values[0]), hauteur=300)
with st.expander('Beeswarm plot'):
    st_shap(shap.plots.beeswarm(shap_values), hauteur=300)

explicateur = shap.TreeExplainer(modèle)
shap_values ​​= explicateur.shap_values(X)

avec st.expander('Force plot'):
    st.subheader('Première instance de données')
    st_shap(shap.force_plot(explainer.expected_value, shap_values[0,:], X_display.iloc[0,:]), hauteur=200, largeur=1000)
    st.subheader('Mille premières instances de données')
    st_shap(shap.force_plot(explainer.expected_value, shap_values[:1000,:], X_display.iloc[:1000,:]), hauteur=400, largeur=1000)
```

## Explication ligne par ligne
La toute première chose à faire lors de la création d'une application Streamlit est de commencer par import la bibliothèque `streamlit` as `st` comme ceci :
```python
import streamlit as st
depuis streamlit_shap import st_shap
forme d'importation
depuis sklearn.model_selection import train_test_split
import xgboost
import numpy as np
import pandas as pd
```

Ensuite, nous allons définir la mise en page sur une largeur telle que le contenu de l'application Streamlit puisse s'étendre sur toute la largeur de la page.
```python
st.set_page_config(layout="wide")
```

Ensuite, nous allons charger un ensemble de données à partir de la bibliothèque `shap` :
```python
@st.experimental_memo
def load_data() :
    retourner shap.datasets.adult()
```

Par la suite, nous allons définir une fonction appelée `load_model` pour prendre la paire de matrices `X, y` en entrée, effectuer le fractionnement des données pour former/tester les ensembles, construire une `DMatrix` et construire un modèle XGBoost.
```python
@st.experimental_memo
def load_model(X, y):
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=7)
    d_train = xgboost.DMatrix(X_train, label=y_train)
    d_test = xgboost.DMatrix(X_test, label=y_test)
    paramètres = {
        "eta": 0.01,
        "objective": "binary:logistique",
        "sous-échantillon": 0,5,
        "base_score": np.mean(y_train),
        "eval_metric": "logloss",
        "n_jobs": -1,
    }
    model = xgboost.train(params, d_train, 10, evals = [(d_test, "test")], verbose_eval=100, early_stopping_rounds=20)
    modèle de retour
```

Le titre de l'application Streamlit s'affiche alors :
```python
st.title("`streamlit-shap` pour afficher SHAP