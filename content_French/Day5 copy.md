# st.écrire

`st.write` permet d'écrire du texte et des arguments dans l'application Streamlit.

En plus de pouvoir afficher du texte, les éléments suivants peuvent également être affichés via la commande `st.write()` :


- Imprime des chaînes ; fonctionne comme `st.markdown()`
- Affiche un `dict` Python
- Affiche `pandas` DataFrame peut être affiché sous forme de tableau
- Tracés/graphiques/chiffres de `matplotlib`, `plotly`, `altair`, `graphviz`, `bokeh`
- Et plus (voir [st.write on API docs](https://docs.streamlit.io/library/api-reference/write-magic/st.write))

## Qu'est-ce que nous construisons ?

Une application simple montrant les différentes manières d'utiliser la commande `st.write()` pour afficher du texte, des nombres, des DataFrames et des tracés.

## Application de démonstration

L'application Streamlit déployée devrait ressembler à celle illustrée dans le lien ci-dessous :

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.write/)

##Code

Voici comment utiliser st.write :

```python
importer numpy en tant que np
importer altair en tant qu'alt
importer des pandas en tant que pd
importer streamlit en tant que st

st.header('st.write')

# Exemple 1

st.write('Bonjour, *Monde !* :lunettes de soleil :')

# Exemple 2

st.écrire (1234)

# Exemple 3

df = pd.DataFrame({
     'première colonne' : [1, 2, 3, 4],
     'deuxième colonne' : [10, 20, 30, 40]
     })
st.écrire (df)

# Exemple 4

st.write('Ci-dessous est un DataFrame :', df, 'Ci-dessus est un dataframe.')

# Exemple 5

df2 = pd.DataFrame(
     np.random.randn(200, 3),
     colonnes=['a', 'b', 'c'])
c = alt.Chart(df2).mark_circle().encode(
     x='a', y='b', size='c', color='c', tooltip=['a', 'b', 'c'])
st.écrire(c)
```

## Explication ligne par ligne

La toute première chose à faire lors de la création d'une application Streamlit est de commencer par importer la bibliothèque `streamlit` en tant que `st` comme ceci :

```python
importer streamlit en tant que st
```

Ceci est suivi par la création d'un texte d'en-tête pour l'application :

```python
st.header('st.write')
```

**Exemple 1**
Son cas d'utilisation de base consiste à afficher du texte et du texte au format Markdown :

```python
st.write('Bonjour, *Monde !* :lunettes de soleil :')
```

**Exemple 2**
Comme mentionné ci-dessus, il peut également être utilisé pour afficher d'autres formats de données tels que des nombres :

```python
st.écrire (1234)
```

**Exemple 3**
Les DataFrames peuvent également être affichés comme suit :

```python
df = pd.DataFrame({
     'première colonne' : [1, 2, 3, 4],
     'deuxième colonne' : [10, 20, 30, 40]
     })
st.écrire (df)
```

**Exemple 4**
Vous pouvez passer plusieurs arguments :

```python
st.write('Ci-dessous est un DataFrame :', df, 'Ci-dessus est un dataframe.')
```

**Exemple 5**
Enfin, vous pouvez également afficher des tracés en le passant à une variable comme suit :

```python
df2 = pd.DataFrame(
     np.random.randn(200, 3),
     colonnes=['a', 'b', 'c'])
c = alt.Chart(df2).mark_circle().encode(
     x='a', y='b', size='c', color='c', tooltip=['a', 'b', 'c'])
st.écrire(c)
```

## Application de démonstration

L'application Streamlit déployée devrait ressembler à celle illustrée dans le lien ci-dessous :

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.write/)

## Prochaines étapes

Maintenant que vous avez créé l'application Streamlit localement, il est temps de la déployer sur [Streamlit Cloud](https://streamlit.io/cloud) comme cela sera expliqué prochainement dans un prochain défi.

Comme il s'agit de la première semaine de votre défi, nous fournissons le code complet (comme indiqué dans la zone de code ci-dessus) et la solution (l'application de démonstration) directement sur cette page Web.

Pour avancer dans les prochains défis, il est recommandé d'essayer d'abord d'implémenter l'application Streamlit vous-même.

Ne vous inquiétez pas si vous êtes bloqué, vous pouvez toujours jeter un coup d'œil à la solution.

## Lectures complémentaires

En plus de [`st.write`](https://docs.streamlit.io/library/api-reference/write-magic/st.write), vous pouvez explorer les autres façons d'afficher du texte :

- [`st.markdown`](https://docs.streamlit.io/library/api-reference/text/st.markdown)
- [`st.header`](https://docs.streamlit.io/library/api-reference/text/st.header)
- [`st.subheader`](https://docs.streamlit.io/library/api-reference/text/st.subheader)
- [`st.caption`](https://docs.streamlit.io/library/api-reference/text/st.caption)
- [`st.text`](https://docs.streamlit.io/library/api-reference/text/st.text)
- [`st.latex`](https://docs.streamlit.io/library/api-reference/text/st.latex)
- [`st.code`](https://docs.streamlit.io/library/api-reference/text/st.code)