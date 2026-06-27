# 🎮 GUÍA DE SQL: BASES DE DATOS DESDE CERO 🎮

Acá vamos a explicar un poquiño lo basiquiño para entender qué hace cada cosiña. `^_^`

## 📊 Estructura Visual de la Data

```text
Fila  ___________________ (Horizontal: Los datos completos de tus personajes)
       |
       |
Columna| (Vertical: La categoría o el tipo de dato)
       |
       | 
       |
```

> 💡 **Por si no lo sabías:** Toda esta información son tablas de Excel gigantes pa' k no te me confundáis `O_o`.

---

## 🥚 BLOQUE 1: LO BÁSICO (Manipulación de Datos - DML)

### 📥 1. El Comando `INSERT INTO`
Es el comando encargado de crear filas nuevas (registros) dentro de una tabla. Es el que alimenta la base de datos con información real.

*(Recordemos que las columnas son la forma en que se agrupa la info; es decir, sin columnas no sabemos a dónde iría ese dato que vamos a ingresar. En este caso, la fila es lo que nos indica en dónde iría ese dato. Ejemplo: en una columna que se llame "nombre", en la fila tienen que ir los nombres como Juan, Pancho, Maduro, Goku, etc. etc.)*

#### 🏗️ La Estructura Obligatoria
*(Porque tiene un orden; sin un orden, el programa no sabe lo que va a hacer `>_<`)*. Se divide en tres partes:

```sql
INSERT INTO nombre_tabla (columna1, columna2, columna3) 
VALUES (valor1, valor2, valor3);
```

#### 🧠 La Lógica detrás del Código:
* 📑 **`INSERT INTO nombre_tabla`**: Le dices a SQL: *"¡Ey! Prepárate que voy a meter información en esta tabla específica"*. `INSERT` significa insertar o agregar, `INTO` es dentro. El nombre de la tabla indica, si hay muchas tablas, en dónde va. O sea, "inserta dentro de esta tabla", colócate que se llama: `tablaMario`.
* 📋 **Los campos entre paréntesis `(columna1, columna2...)`**: *(Ahí técnicamente van los nombres de la columna y si la tabla se llama Mario, entonces los nombres de la columna serían `(champiñon, monedas)`)*. Aquí listas los nombres de las columnas que vas a llenar. **Regla de examen:** Van separados por comas y NO llevan comillas.
* 🪙 **`VALUES (valor1, valor2...)`**: *(Si es Mario sería: `'verde'`, `'rojas'`)*. Aquí metes los datos reales que se van a guardar. **Regla de oro:** Tienen que ir en el mismo orden exacto en el que escribiste las columnas arriba. Si la columna 1 es el champiñón, el valor 1 tiene que ser, en este caso, el color del champiñón. `VALUES` indica los valores exactos que coinciden con esas columnas. O sea, lo que va adentro p.

#### 🛑 Reglas de Escritura de Datos
*(Además, tenemos un grupo de reglas sobre cómo escribir los datos, y literalmente te sirven para que te corra el programa bien po k chi no no `T_T`)*

* 🔤 **Textos (`VARCHAR`) y Fechas (`DATE`)**: Obligatoriamente van encerrados en comillas simples (`' '`).
* 🔢 **Números (`INT`, `DECIMAL`)**: Van sueltos, sin comillas.

🔥 **Coloquemos un ejemplo random `>:D`**
```sql
INSERT INTO tablaMario (champiñon, monedas) VALUES ('verde', 'rojas');
```

---

### 👁️ 2. El Comando `SELECT * FROM`
Acá lo que vamos a hacer es ver todo lo que tenemos en la tabla. Al tú meter la información con el `INSERT INTO`, lo guardarás, pero no podrás ver cómo está la info. Entonces, para poder ver si te equivocaste, si está bien o mal, colocarás `SELECT * FROM`.

#### 🏗️ Estructura Estándar
```sql
SELECT * FROM nombre_tabla;
```

#### 🧠 La Lógica:
* 🔍 **`SELECT`**: Significa "Selecciona o búscame...".
* ⭐ **`*` (El asterisco)**: Es un comodín que significa "TODAS las columnas".
* 🗺️ **`FROM nombre_tabla`**: Significa "desde esta tabla específica".
* 🗣️ **Traducción**: *"Búscame todas las columnas desde la tabla Mario"*.

🔥 **Ejemplo:** `SELECT * FROM tablaMario;`

#### 🎯 Forma B: Para ver columnas específicas (Filtrar columnas)
Si el profesor te dice: *"Muestre solo cuántas monedas hay, no me interesa ver el color del champiñón"*, tú quitas el asterisco y escribes el nombre de la columna:

```sql
SELECT monedas FROM tablaMario;
```
Acá lo que diría es: muéstrame (`SELECT`) toda la columna, o sea, recortamos un pedazo que se llama "monedas" de la tabla (`FROM`); `tablaMario` (nombre de la tabla).

[📚 Volver al Índice](README.md)
[➡️ Siguiente pagina](02_modificacion.md)
