# Cas-Kaggle
Anàlisi exhaustiu de dades, amb el dataset :https://www.kaggle.com/purumalgi/music-genre-classification

# Pràctica Kaggle APC UAB 2021-22
### Nom: Bernat Espinet Torrescassana
### DATASET: Music Genre Classification
### URL: [kaggle](https://www.kaggle.com/purumalgi/music-genre-classification)
## Resum
El dataset utilitza dades de...
Tenim X dades amb N atributs. Un % d'ells és categoric / els altres són numérics i estàn normalitzats...
### Objectius del dataset
Volem crear un classificador bo per determinar el gènere musical d'una nova mostra.
## Experiments
Durant aquesta pràctica hem realitzat diferents experiments.
### Preprocessat
Per preparar el dataset, hem codificat el nom del artista, eliminat el nom de la cançó, omplert els NA amb -1 i estandaritzat les dades. Amb aquest preprocessament es amb el que hem aconseguit els millors resultats.
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
| XGBClassifier | XXX | 69.3% | ?ms |
| Stacked | XXX | 55.3% | ?ms |
## Demo
Per tal de fer una prova, primer hem de executar el codi principal per generar el .db i després l'arxiu Demo.ipybn.
Aquest arxiu ens permet classificar noves cançons que no tenen un genere asociat.
## Conclusions
El millor model basantnos amb el accuracy és el XGBClassifier però un cop fem la Cross Validation, ens adonem que el Stacked és millor ja que no comet overfitting.
Hi han pocs treballs sobre aquest dataset, però tots aconsegueixen entorn el 50% de accuracy.
## Idees per treballar en un futur
En un futur seria interessant classificar més mostres de entrenament dels gèneres amb menys mostres. Això permetria crear un model més general i robust.
