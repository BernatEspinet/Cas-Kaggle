# Cas-Kaggle
Anàlisi exhaustiu de dades, amb el dataset :https://www.kaggle.com/purumalgi/music-genre-classification

# Pràctica Kaggle APC UAB 2021-22
### Nom: Bernat Espinet Torrescassana
### DATASET: Music Genre Classification
### URL: [kaggle](https://www.kaggle.com/purumalgi/music-genre-classification)
## Resum
El dataset conté informació de cançons com ara el nom de l'autor, el nom de la cançó, la instrumentalitat i el tempo d'entre d'altres.
Tenim 17996 dades amb 17 atributs. Un 11% d'ells és categòric i els altres són numèrics. Les dades no estan normalitzades i hi ha un 24.3% de mostres amb NA
### Objectius del dataset
Volem crear un classificador bo per determinar el gènere musical d'una cançó donades les seves característiques.
## Experiments
Primer vàrem aplicar un preprocessat bàsic i vam generar els models, aplicant hyperparameter tunning pels millors. Després vam tornar al preprocessament per trobar quina configuració era la òptima per la nostra base de dades.
### Preprocessat
Per preparar el dataset, hem codificat el nom de l'artista, eliminat el nom de la cançó, omplert els NA amb -1 i estandarditzant les dades. Amb aquest preprocessament és amb el que hem aconseguit els millors resultats.
### Model
| Model | Hiperparametres | Mètrica | Temps |
| -- | -- | -- | -- |
| OneVsOneClassifier | LogisticRegression() | 49.4% | 1.467s |
| OneVsRestClassifier | LogisticRegression() | 49.1% | 0.816s |
| OutputCodeClassifier | LogisticRegression() | 42.0% | 0.950s |
| KNeighborsClassifier | n_neighbors=45 | 49.6% | 0.177s |
| KNeighborsClassifier | n_neighbors=45, weights="distance" | 44.9% | 0.209s |
| DecisionTreeClassifier | criterion= 'entropy', max_depth= None, max_features= 14, min_samples_leaf= 61, splitter= 'best' | 48.3% | 0.625s |
| RandomForestClassifier | criterion= 'entropy', max_depth= 10, max_features= 'sqrt', n_estimators= 1000 | 53.1% | 123.250s |
| XGBClassifier | colsample_bytree= 0.8011935532275019, gamma= 0.0967861901103601, learning_rate= 0.06881623529678811, max_depth= 3, n_estimators= 114, objective= 'o', subsample= 0.8160718933070602 | 69.3% | 7.347s |
| Stacked | Model creat a partir del OneVsOneClassifier, RandomForestClassifier, KNeighborsClassifier i XGBClassifier| 55.3% | 31.735s |
## Demo
Per tal de fer una prova, primer hem d'executar el codi principal per generar el .db i després l'arxiu Demo.ipybn.
Aquest arxiu ens permet classificar noves cançons que no tenen un gènere associat.
## Conclusions
El millor model basant-nos amb l'accuracy és el XGBClassifier però, un cop fem la Cross Validation, ens adonem que el Stacked és millor, ja que no comet overfitting.
Hi ha pocs treballs sobre aquest dataset, però tots aconsegueixen entorn el 50% de accuracy.
## Idees per treballar en un futur
En un futur seria interessant classificar més mostres d'entrenament dels gèneres amb menys mostres. Això permetria crear un model més general i robust.
