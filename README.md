# Proyecto 2: Aprendizaje no supervisado sobre perfiles de una red de contactos

Disponemos de un conjunto de datos con información sobre los perfiles de la web de contactos [OkCupid](https://www.okcupid.com/). El problema de aprendizaje no supervisado a resolver consiste en determinar qué perfiles de la red social son compatibles entre sí; a fin de cuentas, se trata de una web de contactos.

## El conjunto de datos
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
