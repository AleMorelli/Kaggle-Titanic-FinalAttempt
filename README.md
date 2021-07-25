# Kaggle-Titanic-FinalAttempt

![alt text](https://github.com/AleMorelli/Kaggle-Titanic-FinalAttempt/blob/main/titanic-survivors-lifeboat.jpg)

Final Attempt for Kaggle's Titanic: Machine Learning from Disaster
Al analizar la base de datos utilizando Pandas Profile report, lo primero que encontré fue una base de datos incompleta:
La mayoría de los pasajeros estaban inscriptos sin la cabina en la cual abordaron, luego de analizarlo pude ver que aquellos 
a los que se les había registrado la cabina habían sobrevivido en mayor proporción. A partir de ese dato, pude crear una nueva
categoría, en la que se informaba si los pasajeros poseían cabina declarada o no. Y, después, borrar dicha columna (‘Cabin’) 
ya que poseía más de la mitad de los valores faltantes.
Faltaban las edades de varias personas, por lo que, a partir del estudio de la dispersión de acuerdo a las clases y los sexos 
(utilizando seaborn y matplotlib para mostrar los resultados) pude calcular las medias por categoría. De esa forma se llegó a 
completar dicha columna. 
Otro obstáculo fue la columna ‘Name’, ya que contaba con una gran variedad de valores “string” diferentes entre sí. 
Utilizando “str.extract”, pude rastrear los títulos de nobleza presentes en los nombres y, crear una nueva columna en la que 
constaba el título que esa persona poseía. Lo cual me permitió borrar la columna ‘Name’, dejando otra en su lugar.  
Por último, utilizando la herramienta Pandas crosstab, constaté que aquellos individuos que habían viajado sin su familia 
tenían poco porcentaje de supervivencia. De esa manera creé una categoría más que indicó la presencia o ausencia de familiares 
en el barco.
Por último, utilizando le.fit_transform transformé en float, todas las categorías que habían quedado en valores tipo string.
Una vez sanada la base de datos, me dispuse a testear los siguientes modelos predictivos: 
LogisticRegression, GradientBoostingClassifier, RandomForestClassifier, XGBClassifier, MLPClassifier. 
Testeando su desempeño en primer lugar con la base de datos original, en segundo lugar utilizando Oversampling para aumentar 
la base de datos y, en tercer lugar, utilizando SMOTE para el mismo objetivo. 
El test se realizó con herramientas de sklearn metrics, para terminar decantando por utilizar un modelo de regresión logística, 
aumentando la base de datos con SMOTE (de esa forma se obtenían los mejores resultados logrando evitar un exceso de overfit).
