# Proyecto 2: Aprendizaje no supervisado sobre perfiles de una red de contactos

Disponemos de un conjunto de datos con información sobre los perfiles de la web de contactos [OkCupid](https://www.okcupid.com/). El problema de aprendizaje no supervisado a resolver consiste en determinar qué perfiles de la red social son compatibles entre sí; a fin de cuentas, se trata de una web de contactos.

## Tabla de contenido

- [El conjunto de datos](#el-conjunto-de-datos).
- [Decisiones Tomadas](#decidisiones-tomadas).

Puedes encontrar el conjunto de datos en un fichero comprimido en el siguiente [enlace.](https://drive.upm.es/index.php/s/LkFtKeCdq9ElQZX)


### El conjunto de datos
El conjunto de datos contiene unos 60000 perfiles de usuario, incluyendo información sobre 31 características:

- age: edad
- status: estado de la relación
- sex: sexo
- orientation: orientación sexual
- body_type: tipo de cuerpo
- diet: dieta seguida por el usuario
- drinks: ¿bebedor?
- drugs: ¿consumidor de drogas?
- education: máximo nivel educativo alcanzado
- ethnicity: etnia
- height: altura
- income: ingresos anuales (en dólares americanos $)
- job: empleo/industria
- last_online: fecha de la última conexión
- location: lugar de residencia
- offspring: preferencia con respecto a los hijos
- pets: preferencia con respecto a las mascotas
- religion: preferencias religiosas
- sign: signo del zodiaco
- smokes: ¿fumador?
- speaks: idiomas
- essay0 - essay9: campos de texto libre que el usuario ha rellenado en orden arbitrario. **Esto quiere decir que en cada columna del conjunto de datos puede haber texto sobre cualquiera de los siguientes temas**. Estos campos se corresponden con las siguientes preguntas:
   - Acerca de mí / Autorresumen
   - Objetivos actuales / aspiraciones
   - Mi regla de oro / Mis rasgos
   - Probablemente podría ganarte en / Talento
   - La última serie que he visto / Hobbies
   - Un día perfecto / Momentos
   - Yo valoro / Necesito
   - La cosa más privada que estoy dispuesto a admitir / Secretos
   - Lo que realmente estoy buscando / Citas
   - Puedes encontrar el conjunto de datos en un fichero comprimido en el siguiente enlace.



### Decidisiones tomadas

### Subdataset
Separar el dataset por las columnas **obligatorias**:
- sex: sexo
- orientation: orientación sexual

Borramos las finales en caso de "homosexual_f" o "homosexual_m": sex y orientation
Borramos las finales en caso de "heterosexual":  orientation, en sex realizamos un OneHotEncoder

[Los datasets resultantes](https://drive.google.com/drive/folders/1LtThNckGpizyT0Co1qTsR4kHP6ikEZUE?usp=sharing)

### Columnas sesgatorias

Eliminar las que nos parecen claramente sesgatorias o irrelevante:
- ethnicity: etnia
- income: ingresos anuales (en dólares americanos $)
- body_type: tipo de cuerpo
- sign: signo del zodiaco
- education: máximo nivel educativo alcanzado


### Las más relevantes
- status: estado de la relación 
  - Tipo: Available/Single- 0, Seeing someone-1, Married-2 o Unknown-nan
  - Hay numericamente una relacion, de la menos "restrictiva" a la mas restrictiva 
- location: lugar de residencia (la pasaremos a coordenadas: longitud y latitud)
- age: edad
- height: altura
- speaks: idiomas  (columna por idioma y su % de conocimiento, si no ponen nada 0.5)
    - Tiene valores atipicos como c++, lisp pero los hemos dejado porque esa gente tiene gustos similares
    - Borramos las que no hablan ningun idioma
    - Hemos creado una columna derivada: N de idiomas que hablas


### Menos importantes

- last_online: fecha de la última conexión (Descartar las anteriores a un mes y borrar fila)

- diet: dieta seguida por el usuario (One Hot Encoder, dejando unicamente vegan y vegetarian)
- drinks: ¿bebedor? Reducimos posibilidades (0 No - 1 Socialmente, Raramente - 2 Si)
- smokes: ¿fumador? Reducimos posibilidades(Si 1 y No 0)
- drugs: ¿consumidor de drogas? Reducimos posibilidades (Si 1 y No 0)

- job: empleo/industria
  - Cambiar unemployed, other y rather not say a nulo para evitar sesgos
  - Hemos dejado las siguientes: { 'student', 'retired'}
  - Y hemos generado por gustos parecidos las siguientes:
   - art: 'entertainment / media', 'artistic / musical / writer'
   - tech: 'computer / hardware / software', 'science / tech / engineering'
   - health: 'medicine / health'
   - social: 'banking / financial / real estate', 'law / legal services', 'sales / marketing / biz dev', 'clerical / administrative', 'executive / management', 'political / government', 'education / academia', 'hospitality / travel', 'military'
   - industrial: 'construction / craftsmanship', 'transportation'

- offspring: preferencia con respecto a los hijos
  - hijos: Tiene hijos (Si 1 o No 0)
  - quiere_hijos: Si quiere hijos (Si 1 o No 0) 
- pets: preferencia con respecto a las mascotas 
 - dog: Tiene o le gustan los perros (Si 1 o No 0) 
 - cat: Tiene o le gustan los gatos  (Si 1 o No 0) 
- religion: preferencias religiosas (columna por religion y su % de seriedad, si no ponen nada 0.5)

- essay0 - essay9: Aplicar algoritmo LDA para sacar los topics mas importantes (TODO)

### Como tratar nulos

En la mayoría de las columnas haremos la moda, el casos de muy pocos nulos, dropearemos las filas. En casos como la religion, consideraremos que si no ha puesto ninguna, no pertenece a ninguna.
