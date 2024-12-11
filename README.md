# Anàlisi i Predicció de Frames de Pel·lícules mitjançant Bag of Visual Words

Aquest projecte implementa algorismes de visió per computador per analitzar i predir frames de tràilers de pel·lícules. Les tasques principals són:

1. **Classificació**: Determinar a quina pel·lícula pertany un frame.
2. **Predicció seqüencial**: Identificar el següent frame dins d’una seqüència de tràiler.

---

## **Descripció**

Aquest treball se centra en la implementació de tècniques com Bag of Visual Words (BoVW) per transformar descriptors visuals en histogrames representatius. S’han utilitzat diversos models d’aprendreçatge supervisat, com SVM, KNN, Random Forest i Regressió Logística, per classificar els frames en pel·lícules. També s’ha implementat un sistema de “retrieval” per predir frames seqüencials, aplicant mètriques com la distància Chi-Squared i la similitud cosinus.

---

## **Requisits previs**

### **Dependències necessàries**

* L'entorn utilitzat ha estat python. 

* Per executar aquest projecte, assegura’t de tenir instal·lades les biblioteques que apareixen a l'inici del Notebook.

---

## **Instruccions d'ús**

### **Execució del projecte**

Per al correcte funcionament de tot el projecte, s'hauria de crear un directori local que segueixi la següent estructura:
PROJECT_ROOT/
├── APC/
│   ├── CAS_KAGGLE/
│   │   ├── FRAME-PREDICTION/
│   │   │   ├── FRAMES__FINALS/
│   │   │   │   ├── FRAMES_DATASET_FINAL.csv
│   │   │   │   ├── histograms.npy
│   │   │   │   ├── rutas_validas.npy
│   │   │   │   ├── rutas_validas_ordenadas.npy
│   │   │   │   ├── descriptors.npz
│   │   │   │   ├── descriptors_ordenats.npz
│   │   │   │   ├── ...
│   │   │   │   ├── FRAMES_GODFATHER/
│   │   │   │   │   ├── frame_1.jpg
│   │   │   │   │   ├── frame_2.jpg
│   │   │   │   │   ├── ...
│   │   │   │   ├── FRAMES_SHINING/
│   │   │   │   │   ├── frame_1.jpg
│   │   │   │   │   ├── frame_2.jpg
│   │   │   │   │   ├── ...

1. **Preparar el dataset**
Inicialment s'ha de crear el dataset amb tots els frames corresponents a les 10 pel·lícules diferents. Per motius d'espai, el zip amb tots els frames no pot estar al repositori GIT, però el podem proporcionar per altres interfícies posant-vos en contacte amb nosaltres (Apartat de contacte). Un cop es té el zip, per generar la base de dades s'ha d'executar la funció `agregar_carpeta_al_csv` per cada carpeta del zip. Prèviament a això, també s'haurien d'haver executat les funcions `calcular_brillantor_promig` i `calcular_contrast`.  

Un cop fet això estaria creada la base de dades. L'únic que haurieu de fer és assegurar-vos que esteu a l'arrel del projecte. Us podeu assegurar executant el codi `os.chdir('ROOT').

2. **Entrenament i validació dels models**

   - Els vocabularis, histogrames i rutes valides es troben ja precomputats en format `npy` en el repositori de GITHUB.

   - Cal remarcar que hi ha dos vocabularis, dos histogrames i dues rutes valides per a les dues parts del projecte. El no ordenats (primers) fan referència a la primera part del projecte (classificació de pel·lícules), i els ordenats (segons) a la segona (predicció següent frame). El Notebook està preparat per suportar un execució seqüencial de cel·les, és a dir, no hi hauria d'haver cap problema. Però és adequat mencionar-ho.

   - De la mateixa manera que amb els frames, GITHUB tampoc és capaç de suportar el pes dels descriptors. Aquests no són necessaris per a l'execució, ja que ja hi ha els histogrames. Si es necessiten els podem proporcionar per altres interfícies posant-vos en contacte amb nosaltres (Apartat de contacte). 



3. **Predicció pel·lícula**

   - Exemple d’ús per predir la pel·lícula d’un frame:

     `predir_pelicula_per_frame(frame_index, model_to_use)`

     * `frame_index`: Índex del frame a predir la pel·lícula. Índex màxim 2989. 

     * `model_to_use`: Model a triar per a predir la pel·lícula. Models a triar: "SVM", "Random Forest", "Knn" i "Logistic Regression".  
     

4. **Predicció següent frame**

   - Exemple d'ús per predir el següent frame d’una seqüència:

   `mostrar_candidats(peliculas_dict, pelicula, frame_index, num_candidats)`

     * `peliculas_dict`: Diccionari creat amb anterioritat en el Notebook. 

     * `pelicula`: Pel·lícula a triar per a la predicció del següent frame. Cal remarcar que per posar el nom de la pel·lícula, s'ha de posar el nom de la carpeta on estan els frames d'aquesta pel·lícula. 

     * `frame_index`: Índex del frame a predir el següent frame. Índex màxim 2987. 

     * `num_candidats`: Nombre de candidats (frames més semblants) que agafa el el model. Ha de ser un nombre natural major que 0.     
     
    - Exemple d'ús per veure els "matches" (coincidències dels descriptors) de dos frames consecutius:

    `mostrar_matches(frame_index)`

    * `frame_index`: Índex del frame del qual es mostraran els "matches" amb el següent. Índex màxim 2987.
    
---


## **Contacte**

Per a dubtes o suggeriments:
- **Noms**: [David Araujo García] i [Enric Ortega Barreda]
- **Email**: [1671077@uab.cat] i [1672973@uab.cat]
