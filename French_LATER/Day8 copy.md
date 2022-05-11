# premier curseur

`st.slider` permet l'affichage d'un widget de saisie de curseur.

Les types de données suivants sont pris en charge : int, float, date, time et datetime.

## Qu'est-ce que nous construisons ?

Une application simple qui montre les différentes manières d'accepter les entrées de l'utilisateur en ajustant le widget du curseur.

Déroulement de l'application :
1. L'utilisateur sélectionne la valeur en ajustant le widget du curseur
2. L'application imprime la valeur sélectionnée

## Application de démonstration

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.slider/)


##Code
Voici comment utiliser st.slider :

```python
import streamlit as st
à partir de l'heure d'importation datetime, datetime

st.header('st.slider')

# Exemple 1

st.subheader('Slider')

age = st.slider('Quel âge as-tu ?', 0, 130, 25)
st.write("Je suis ", age, 'ans')

# Exemple 2

st.subheader('Curseur de plage')

valeurs = st. slider(
     'Sélectionner une plage de valeurs',
     0.0, 100.0, (25.0, 75.0))
st.write('Valeurs :', valeurs)

# Exemple 3

st.subheader('Curseur de temps de plage')

rendez-vous = st.curseur(
     "Planifiez votre rendez-vous :",
     valeur=(temps(11, 30), temps(12, 45)))
st.write("Vous êtes programmé pour :", rendez-vous)

# Exemple 4

st.subheader('Curseur date/heure')

start_time = st.slider(
     "Quand tu commences?",
     valeur=datetime(2020, 1, 1, 9, 30),
     format="JJ/MM/AA - hh:mm")
st.write("Heure de début :", heure_début)

```

## Explication ligne par ligne
La toute première chose à faire lors de la création d'une application Streamlit est de commencer par import la bibliothèque `streamlit` as `st` comme ceci :
```python
import streamlit as st
à partir de l'heure d'importation datetime, datetime
```

Ceci est suivi par la création d'un texte d'en-tête pour l'application :
```python
st.header('st.slider')
```

**Exemple 1**

Glissière:

```python
st.subheader('Slider')

age = st.slider('Quel âge as-tu ?', 0, 130, 25)
st.write("Je suis ", age, 'ans')
```

Comme nous pouvons le voir, la commande `st.slider()`
est utilisé pour collecter les entrées des utilisateurs sur l'âge des utilisateurs.

Le premier argument d'entrée affiche le texte juste au-dessus du widget **slider** demandant `'Quel âge as-tu ?'`.

Les trois nombres entiers suivants "0, 130, 25" représentent respectivement les valeurs minimale, maximale et par défaut.

**Exemple 2**

Curseur de plage :

```python
st.subheader('Curseur de plage')

valeurs = st. slider(
     'Sélectionner une plage de valeurs',
     0.0, 100.0, (25.0, 75.0))
st.write('Valeurs :', valeurs)
```

Le curseur de plage permet de sélectionner une paire de valeurs limites inférieure et supérieure.

Le premier argument d'entrée affiche le texte juste au-dessus du widget **curseur de plage** demandant `'Sélectionner une plage de valeurs'`.

Les trois arguments suivants "0.0, 100.0, (25.0, 75.0)" représentent les valeurs minimale et maximale tandis que le dernier tuple indique les valeurs par défaut à utiliser comme valeurs de limite inférieure (25.0) et supérieure (75.0) sélectionnées.

**Exemple 3**

Curseur de temps de plage :

```python
st.subheader('Curseur de temps de plage')

rendez-vous = st.curseur(
     "Planifiez votre rendez-vous :",
     valeur=(temps(11, 30), temps(12, 45)))
st.write("Vous êtes programmé pour :", rendez-vous)
```

Le curseur de plage de temps permet de sélectionner une paire de valeurs limites inférieure et supérieure de date/heure.

Le premier argument d'entrée affiche le texte juste au-dessus du widget **curseur de plage de temps** demandant `'Planifiez votre rendez-vous :`.

Les valeurs par défaut des paires de valeurs limites inférieure et supérieure de datetime sont définies sur 11:30 et 12:45, respectivement.

**Exemple 4**

Curseur date/heure :

```python
st.subheader('Curseur date/heure')

start_time = st.slider(
     "Quand tu commences?",
     valeur=datetime(2020, 1, 1, 9, 30),
     format="JJ/MM/AA - hh:mm")
st.write("Heure de début :", heure_début)
```

Le curseur datetime permet de sélectionner une datetime.

Le premier argument d'entrée affiche le texte juste au-dessus du widget curseur **datetime** demandant `'Quand commencez-vous ?'`.

La valeur par défaut pour la date et l'heure a été définie à l'aide de l'option `value` pour être le 1er janvier 2020 à 9h30

## Lectures complémentaires
Vous pouvez également explorer le widget associé suivant :
- [`st.select_slider`](https://docs.streamlit.io/library/api-reference/widgets/st.select_slider)