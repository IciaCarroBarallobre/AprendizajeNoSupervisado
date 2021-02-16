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

Separar el dataset por las columnas obligatorias:
- sex: sexo
- orientation: orientación sexual

Borramos las finales en caso de "homosexual_f" o "homosexual_m": sex y orientation
Borramos las finales en caso de "heterosexual":  orientation


Eliminar las que nos parecen claramente sesgatorias o irrelevante:
- ethnicity: etnia
- income: ingresos anuales (en dólares americanos $)
- body_type: tipo de cuerpo
- sign: signo del zodiaco

Las mas importantes:
- age: edad
- status: estado de la relación 
- location: lugar de residencia (la pasaremos a coordenadas) , longitud y latitud
- height: altura

Las demas:
- last_online: fecha de la última conexión (Descartar las anteriores a un mes y borrar fila)
- diet: dieta seguida por el usuario (TODO)
- drinks: ¿bebedor? (Hemos reducido las posibilidades a varias y aplicado one hot encoder- nos falta tratamiento de nulos)
- smokes: ¿fumador? (Hemos reducido las posibilidades a si o no - nos falta tratamiento de nulos)
- drugs: ¿consumidor de drogas? (Hemos reducido las posibilidades a si o no- nos falta tratamiento de nulos)
- education: máximo nivel educativo alcanzado (TODO)
- job: empleo/industria (TODO)
- offspring: preferencia con respecto a los hijos (TODO)
- pets: preferencia con respecto a las mascotas (TODO)
- religion: preferencias religiosas (TODO)
- speaks: idiomas  (Hemos hecho una columna por idioma y su % de conocimiento, si no ponen nada 0.5)
    - Todos hablan ingles asi que la hemos dejado como menos importante
    - Tiene valores atipicos como c++
- essay0 - essay9: Aplicar algoritmo LDA para sacar los topics mas importantes (TODO)
