# 📝 Recopilación de datos — Store 1

<p align="center">
  <img src="https://img.shields.io/badge/Python-Listas%20%26%20Strings-blue?logo=python" />
  <img src="https://img.shields.io/badge/Fase-Recopilación%20de%20Datos-orange" />
  <img src="https://img.shields.io/badge/Enfoque-Calidad%20de%20datos-success" />
</p>

---

## 📌 Descripción general

Este proyecto corresponde a la **primera fase** del análisis de clientes de **Store 1**.  
El objetivo es **evaluar la calidad de una muestra de datos**, aplicar correcciones básicas y dejar la información lista para futuros análisis.

Los datos se entregan como una **lista de listas en Python**, donde cada sublista representa a una persona usuaria con la siguiente estructura:

```python
users = [
    ['32415', ' mike_reed ', 32.0, ['ELECTRONICS', 'SPORT', 'BOOKS'], [894, 213, 173]],
    ['31980', 'kate morgan', 24.0, ['CLOTHES', 'BOOKS'], [439, 390]],
    ['32156', ' john doe ', 37.0, ['ELECTRONICS', 'HOME', 'FOOD'], [459, 120, 99]],
    ['32761', 'SAMANTHA SMITH', 29.0, ['CLOTHES', 'ELECTRONICS', 'BEAUTY'], [299, 679, 85]],
    ['32984', 'David White', 41.0, ['BOOKS', 'HOME', 'SPORT'], [234, 329, 243]],
    ['33001', 'emily brown', 26.0, ['BEAUTY', 'HOME', 'FOOD'], [213, 659, 79]],
    ['33767', ' Maria Garcia', 33.0, ['CLOTHES', 'FOOD', 'BEAUTY'], [499, 189, 63]],
    ['33912', 'JOSE MARTINEZ', 22.0, ['SPORT', 'ELECTRONICS', 'HOME'], [259, 549, 109]],
    ['34009', 'lisa wilson ', 35.0, ['HOME', 'BOOKS', 'CLOTHES'], [329, 189, 329]],
    ['34278', 'James Lee', 28.0, ['BEAUTY', 'CLOTHES', 'ELECTRONICS'], [189, 299, 579]],
]
Campos:

user_id: identificador único (cadena de texto).

user_name: nombre y apellido en un solo string.

user_age: edad (float inicialmente).

fav_categories: categorías favoritas (en mayúsculas).

total_spendings: lista de montos gastados por categoría.

🔍 Paso 1 – Evaluación inicial de calidad de datos
Se revisó un registro ejemplo:

python
Copy code
user_id = '32415'
user_name = ' mike_reed '
user_age = 32.0
fav_categories = ['ELECTRONICS', 'SPORT', 'BOOKS']
Observaciones:

user_id: puede mantenerse como texto, no es obligatorio convertirlo a entero si solo se usa como identificador.

user_name: tiene espacios innecesarios y un guion bajo entre nombre y apellido → requiere limpieza.

user_age: tipo float, pero para análisis numérico y consistencia es preferible entero.

fav_categories: todo está en mayúsculas. No es un error, pero es mejor normalizar a minúsculas para evitar problemas en filtros y comparaciones.

🧹 Paso 2 – Limpieza de user_name
Se limpiaron espacios y se reemplazó el guion bajo _ por un espacio:

python
Copy code
user_name = ' mike_reed '
user_name = user_name.strip()        # elimina espacios al inicio y al final
user_name = user_name.replace("_", " ")

print(user_name)  # 'mike reed'
✂️ Paso 3 – Separar nombre y apellido
Se dividió el nombre en una lista [nombre, apellido]:

python
Copy code
user_name = 'mike reed'
name_split = user_name.split()

print(name_split)  # ['mike', 'reed']
🔢 Paso 4 – Conversión de edad a entero
Se corrigió el tipo de dato de user_age:

python
Copy code
user_age = 32.0
user_age = int(user_age)

print(user_age)  # 32
🛡️ Paso 5 – Manejo robusto de errores en edad
Para evitar que el sistema falle si la edad no es numérica, se usó try/except:

python
Copy code
user_age = 'treinta y dos'

try:
    user_age_int = int(user_age)
    print(user_age_int)
except:
    print("Please provide your age as a numerical value")
Salida:

text
Copy code
Please provide your age as a numerical value
📚 Paso 6 – Ordenar la lista de usuarios
Se ordenó la lista users de forma ascendente por user_id:

python
Copy code
users.sort()
print(users)
La lista resultante queda ordenada por el primer elemento de cada sublista (el ID).

💰 Paso 7 – Cálculo del gasto total por usuario
Dadas las categorías favoritas y los gastos por categoría:

python
Copy code
fav_categories_low = ['electronics', 'sport', 'books']
spendings_per_category = [894, 213, 173]

total_amount = sum(spendings_per_category)
print(total_amount)  # 1280
Se utilizó sum() para obtener el monto total gastado.

🧾 Paso 8 – Cadena formateada para un usuario
Se generó una descripción amigable del usuario:

python
Copy code
user_id = '32415'
user_name = ['mike', 'reed']
user_age = 32

user_info = f"User {user_id} is {user_name[0]} who is {user_age} years old"
print(user_info)
Salida:

text
Copy code
User 32415 is mike who is 32 years old
👥 Paso 9 – Contar cuántos clientes hay
Se creó una cadena con la cantidad total de registros:

python
Copy code
users = [
    ['32415', ' mike_reed ', 32.0, ['ELECTRONICS', 'SPORT', 'BOOKS'], [894, 213, 173]],
    ['31980', 'kate morgan', 24.0, ['CLOTHES', 'BOOKS'], [439, 390]],
    ['32156', ' john doe ', 37.0, ['ELECTRONICS', 'HOME', 'FOOD'], [459, 120, 99]],
    ['32761', 'SAMANTHA SMITH', 29.0, ['CLOTHES', 'ELECTRONICS', 'BEAUTY'], [299, 679, 85]],
    ['32984', 'David White', 41.0, ['BOOKS', 'HOME', 'SPORT'], [234, 329, 243]],
    ['33001', 'emily brown', 26.0, ['BEAUTY', 'HOME', 'FOOD'], [213, 659, 79]],
    ['33767', ' Maria Garcia', 33.0, ['CLOTHES', 'FOOD', 'BEAUTY'], [499, 189, 63]],
    ['33912', 'JOSE MARTINEZ', 22.0, ['SPORT', 'ELECTRONICS', 'HOME'], [259, 549, 109]],
    ['34009', 'lisa wilson ', 35.0, ['HOME', 'BOOKS', 'CLOTHES'], [329, 189, 329]],
    ['34278', 'James Lee', 28.0, ['BEAUTY', 'CLOTHES', 'ELECTRONICS'], [189, 299, 579]],
]

user_info = f"Hemos registrado datos de {len(users)} clientes."
print(user_info)
Salida:

text
Copy code
Hemos registrado datos de 10 clientes.
🧼 Paso 10 – Construcción de users_clean
Se aplicaron las transformaciones a una lista reducida de usuarios:

Eliminar espacios y guiones bajos en user_name.

Convertir user_age a entero.

Dividir el nombre en [nombre, apellido].

python
Copy code
users = [
    ['32415', ' mike_reed ', 32.0, ['ELECTRONICS', 'SPORT', 'BOOKS'], [894, 213, 173]],
    ['31980', 'kate morgan', 24.0, ['CLOTHES', 'BOOKS'], [439, 390]],
    ['32156', ' john doe ', 37.0, ['ELECTRONICS', 'HOME', 'FOOD'], [459, 120, 99]],
]

users_clean = []

# Usuario 1
user_name_1 = users[0][1].strip().replace("_", " ")
user_age_1 = int(users[0][2])
user_name_1 = user_name_1.split()
users_clean.append([users[0][0], user_name_1, user_age_1, users[0][3], users[0][4]])

# Usuario 2
user_name_2 = users[1][1].strip().replace("_", " ")
user_age_2 = int(users[1][2])
user_name_2 = user_name_2.split()
users_clean.append([users[1][0], user_name_2, user_age_2, users[1][3], users[1][4]])

# Usuario 3
user_name_3 = users[2][1].strip().replace("_", " ")
user_age_3 = int(users[2][2])
user_name_3 = user_name_3.split()
users_clean.append([users[2][0], user_name_3, user_age_3, users[2][3], users[2][4]])

print(users_clean)
Resultado final:

python
Copy code
[
  ['32415', ['mike', 'reed'], 32, ['ELECTRONICS', 'SPORT', 'BOOKS'], [894, 213, 173]],
  ['31980', ['kate', 'morgan'], 24, ['CLOTHES', 'BOOKS'], [439, 390]],
  ['32156', ['john', 'doe'], 37, ['ELECTRONICS', 'HOME', 'FOOD'], [459, 120, 99]]
]
✅ Conclusiones
Se identificaron y corrigieron problemas típicos de calidad de datos:

Espacios innecesarios y guiones bajos en nombres.

Tipos de datos no apropiados para la edad.

Necesidad de manejar errores en entradas no numéricas.

Necesidad de ordenamiento y conteo básico.

Se generaron:

Mensajes formateados para usuarios individuales y para el total de clientes.

Una versión limpia de la información: users_clean, lista para futuras fases del proyecto.

Esta fase deja la base preparada para avanzar a análisis más complejos en el siguiente sprint, donde se usarán estos mismos datos pero ya estructurados y depurados.
