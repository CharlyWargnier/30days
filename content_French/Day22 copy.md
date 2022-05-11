# st.forme

`st.form` crée un formulaire qui regroupe les éléments avec un bouton "Soumettre".

En règle générale, chaque fois qu'un utilisateur interagit avec un widget, l'application Streamlit est réexécutée.

Un formulaire est un conteneur qui regroupe visuellement d'autres éléments et widgets et contient un bouton Soumettre. Ici, un utilisateur peut interagir avec un ou plusieurs widgets autant de fois qu'il le souhaite sans provoquer de réexécution. Enfin, lorsque le bouton Soumettre du formulaire est enfoncé, toutes les valeurs de widget à l'intérieur du formulaire seront envoyées à Streamlit en un seul lot.

Pour ajouter des éléments à un objet de formulaire, vous pouvez utiliser la notation `with` (préférée) ou vous pouvez l'utiliser comme notation d'objet en appelant simplement des méthodes directement sur le formulaire (en l'affectant d'abord à une variable et en appliquant ensuite les méthodes Streamlit sur ce). Voir dans l'exemple d'application.

Les formulaires ont quelques contraintes :
- Chaque formulaire doit contenir un `st.form_submit_button`.
- `st.button` et `st.download_button` ne peuvent pas être ajoutés à un formulaire.
- Les formulaires peuvent apparaître n'importe où dans votre application (barre latérale, colonnes, etc.), mais ils ne peuvent pas être intégrés à d'autres formulaires.

Pour plus d'informations sur les formulaires, consultez notre [article de blog](https://blog.streamlit.io/introducing-submit-button-and-forms/).

## Application de démonstration

[![Application Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.form/)

##Code
Voici comment utiliser `st.form` :
```python
importer streamlit en tant que st

st.title('st.form')

# Exemple complet d'utilisation de la notation with
st.header('1. Exemple d'utilisation de la notation `with`')
st.subheader('Machine à café')

avec st.form('my_form'):
    st.write('**Commandez votre café**')
    
    # Widgets d'entrée
    coffee_bean_val = st.selectbox('Grain de café', ['Arabica', 'Robusta'])
    coffee_roast_val = st.selectbox('Torréfaction de café', ['Léger', 'Moyen', 'Foncé'])
    brewing_val = st.selectbox('Méthode de brassage', ['Aeropress', 'Drip', 'Presse française', 'Moka pot', 'Siphon'])
    servir_type_val = st.selectbox('Format de service', ['Chaud', 'Glacé', 'Frappe'])
    milk_val = st.select_slider('Intensité du lait', ['Aucun', 'Faible', 'Moyenne', 'Elevée'])
    owncup_val = st.checkbox('Apporter sa propre tasse')
    
    # Chaque formulaire doit avoir un bouton d'envoi
    soumis = st.form_submit_button('Soumettre')

si soumis :
    st.markdown(f'''
        ☕ Vous avez commandé :
        - Grain de café : `{coffee_bean_val}`
        - Torréfaction de café : `{coffee_roast_val}`
        - Brassage : `{brewing_val}`
        - Type de diffusion : `{serving_type_val}`
        - Lait : `{milk_val}`
        - Apportez votre propre tasse : `{owncup_val}`
        ''')
autre:
    st.write('☝️ Passez votre commande !')


# Court exemple d'utilisation d'une notation d'objet
st.header('2. Exemple de notation d'objet')

formulaire = st.form('my_form_2')
selected_val = form.slider('Sélectionner une valeur')
form.form_submit_button('Soumettre')

st.write('Valeur sélectionnée : ', valeur_sélectionnée)
```

## Explication ligne par ligne
La toute première chose à faire lors de la création d'une application Streamlit est de commencer par importer la bibliothèque `streamlit` en tant que `st` comme ceci :
```python
importer streamlit en tant que st
```

Ceci est suivi par la création d'un texte de titre pour l'application :
```python
st.title('st.form')
```

### Premier exemple
Commençons par le premier exemple, ici nous appliquerons la commande `st.form` via la notation `write`. Dans le formulaire, nous commencerons par écrire un sous-en-tête "Commandez votre café", puis créerons plusieurs widgets de saisie (`st.selectbox`, `st.select_slider` et `st.checkbox`) pour collecter des informations sur la commande de café. Enfin, un bouton de soumission est créé via la commande `st.form_submit_button`, qui, une fois cliqué, enverra toutes les entrées de l'utilisateur sous la forme d'un seul lot d'informations à l'application pour traitement.
```python
# Exemple complet d'utilisation de la notation with
st.header('1. Exemple d'utilisation de la notation `with`')
st.subheader('Machine à café')

avec st.form('my_form'):
    st.subheader('**Commandez votre café**')
    
    coffee_bean_val = st.selectbox('Grain de café', ['Arabica', 'Robusta'])
    coffee_roast_val = st.selectbox('Torréfaction de café', ['Léger', 'Moyen', 'Foncé'])
    brewing_val = st.selectbox('Méthode de brassage', ['Aeropress', 'Drip', 'Presse française', 'Moka pot', 'Siphon'])
    servir_type_val = st.selectbox('Format de service', ['Chaud', 'Glacé', 'Frappe'])
    milk_val = st.select_slider('Intensité du lait', ['Aucun', 'Faible', 'Moyenne', 'Elevée'])
    owncup_val = st.checkbox('Apporter sa propre tasse')
    
    # Chaque formulaire doit avoir un bouton d'envoi.
    soumis = st.form_submit_button('Soumettre')
```

Ensuite, nous ajouterons la logique de ce qui se passe après avoir cliqué sur le bouton Soumettre. Par défaut, chaque fois que l'application Streamlit est chargée, l'instruction `else` sera exécutée et nous verrons un message `☝️ Passez votre commande !`. Alors qu'en cliquant sur le bouton Soumettre, toutes les entrées fournies par l'utilisateur via les différents widgets sont stockées dans plusieurs variables (par exemple, `coffee_bean_val`, `coffee_roast_val`, etc.) et imprimées via la commande `st.markdown` à l'aide de f -corde.
```python
si soumis :
    st.markdown(f'''
        ☕ Vous avez commandé :
        - Grain de café : `{coffee_bean_val}`
        - Torréfaction de café : `{co