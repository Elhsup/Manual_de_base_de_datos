# 🎮 GUÍA DE SQL: BASES DE DATOS DESDE CERO 🎮

Acá vamos a explicar un poquiño de lo que es el DML, lo basiquiño para entender qué hace cada cosiña. `^_^`

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

---

### 🔄 3. El Comando UPDATEEEEEE `xD`
**¿Qué hace?:** Es el comando que sirve para modificar o actualizar un dato que ya está guardado dentro de una fila. Por ejemplo, si registraste que el champiñón era `'verde'` pero en realidad querías ponerle `'azul'`, usas `UPDATE`. O sea, cambias el valor a una fila.

#### 🏗️ Estructura Fija de Tres Pasos (Se lee de arriba a abajo):
```sql
UPDATE nombre_tabla   
SET columna_a_cambiar = 'nuevo_valor'          
WHERE columna_filtro = 'valor_buscado';
```

#### 🎯 Descifrando los Valores
Donde dice `nuevo_valor` y `valor_buscado` significa los nombres (o los datos, como los quieras llamar) que vas a cambiar y buscar:
* 🔵 **`nuevo_valor`**: Por ejemplo, `'azul'` (o sea, el dato fresco que vas a colocar).
* 🔴 **`valor_buscado`**: Por ejemplo, `'rojo'` (el dato viejo que quieres cambiar). *(Ejemplo de las monedas)*.

#### 🧠 La Lógica de cada paso:
* 🚪 **`UPDATE nombre_tabla`**: Le dices a SQL: *"UPDATE (cambia) y entra a esta tabla porque voy a hacer una edición"*.
* ✍️ **`SET columna_a_cambiar = 'nuevo_valor'`**: La palabra `SET` significa "Establecer o Colocar". Aquí le dices: *"Quiero que metas este nuevo dato en esta columna"*.
* 🎯 **`WHERE columna_filtro = 'valor_buscado'`**: **¡EL PASO MÁS IMPORTANTE!** Aquí le dices a qué fila exacta le vas a hacer el cambio. (`WHERE` significa "Donde": Pone una condición. SQL va a ir fila por fila y solo te va a pintar en la pantalla las filas que cumplan exactamente con lo que pides. Las demás las deja ocultas).

#### 🚨 La Regla del Desastre:
Si tú escribes en el examen `UPDATE tablaMario SET champiñon = 'azul';` y se te olvida poner el `WHERE`, SQL le va a cambiar el color a TODOS los champiñones de la tabla completa. El profesor te va a raspar de una vez por "destruir" la base de datos `x_x`. El `WHERE` es el francotirador que le dice a SQL: *"Cámbiame el dato ÚNICAMENTE en esta fila"*.

**¿Qué pasa con el WHERE y colocarle el nombre de la tabla?**
Sin ponerle un filtro, entra a la tabla y le cambia el valor a todas las filas que existan. Si tenías monedas rojas, verdes, doradas, negras... absolutamente todas pasan a ser azules. Borraste el historial del juego por error.

* O sea, que si le coloco el `WHERE` sin la columna correcta, me puede cambiar en otros lugares que no quiero.
* Si "no" le coloco el `WHERE`, me puede cambiar todo, hasta lo que no quiero que se cambie.

---

### ❌ 4. El Comando DELETE
**¿Qué hace?:** Sirve para borrar filas (registros) completas de una tabla. **Ojo:** borra la fila entera (el objeto), no una casilla suelta.

#### 🏗️ Estructura Obligatoria en la Pizarra:
```sql
DELETE FROM nombre_tabla 
WHERE nombre_columna = 'valor_buscado';
```

#### 🧠 La Lógica de examen:
* 🧼 **`DELETE FROM tablaMario`**: Le dices a SQL: *"Voy a eliminar registros de esta tabla"*. (Nota que aquí no se ponen nombres de columnas, porque vas a borrar la fila completa).
* 🛡️ **`WHERE monedas = 'azules'`**: El guardaespaldas otra vez. Si no pones el `WHERE`, ejecutas un `DELETE FROM tablaMario;` y vacías la tabla por completo, dejas a Mario sin ningún dato. El `WHERE` le dice: *"Borra ÚNICAMENTE la fila donde las monedas sean azules"*.

---

### 🏆 Laboratorio Práctico de DML (Caso de Examen)
```sql
-- Insert into Consola 
INSERT INTO Consola (IdConsola, Nombre, Marca) 
VALUES (5, 'PS5', 'Sony');

-- Insert into Videojuego
INSERT INTO Videojuego (IdJuego, Titulo, Genero) 
VALUES (101, 'Spider-Man', 'Accion');

-- Update Videojuego 
UPDATE Videojuego 
SET Genero = 'Aventura'
WHERE IdJuego = 101; 
-- 💡 Nota: Usamos el IdJuego = 101 como francotirador para cambiar el género de forma única sin alterar otros registros.

-- Delete de Videojuego
DELETE FROM Videojuego 
WHERE IdJuego = 101;
```

---
---

## 🧠 BLOQUE 2: LO AVANZADO (Diseño, Llaves y Relaciones)

### 🔑 Conceptos Clave: Claves y Relaciones
* 🔑 **Clave Primaria (Primary Key):** Identificador único de una tabla, que no puede repetirse ni ser nula.
* 🔗 **Clave Foránea (Foreign Key):** Se lleva la clave primaria de una tabla a otro lado. Es la conexión de una tabla a otra (decimos que esta es la segunda tabla; técnicamente también tiene su propia clave primaria).

### 📐 Jerarquía Padre e Hijo
La clave primaria puede salir en cualquier tabla (llamémosla **tabla padre**). Sin embargo, la clave foránea se va a mover, heredar o aparecer en la tabla QUE NO ES principal (llamémosla **tabla hijo**). `OwO`

**Ejemplo:** En un hospital se necesita el historial del paciente.
* **Principal (Padre):** Paciente *(tiene su clave primaria)*.
* **Derivada o no principal (Hijo):** Historial *(ahí va a aparecer la clave foránea, que es la clave principal del paciente)*.

#### ¿Dónde van las claves foráneas?
En este caso, hay 3 razones por las que van en la parte de "muchos" o en la tabla hijo:
1. El profesor dijo que donde iban "muchos", ahí van las foráneas `:b`.
2. Primero sale el padre y después el hijo. La clave foránea, por lógica, no puede ir donde va el padre porque el padre salió primero que el hijo.
3. Cuando tienes muchas cosas que se conectan con una sola, necesitas administrar quién es el dueño; de ahí agarras y le colocas las claves foráneas a las cosas que necesitas administrar.

**O así pa' que entiendas mejor:**
* **Por regla de cardinalidad:** El lado de "Muchos" es el único que permite repetir el identificador del padre para conectar varios registros a un mismo origen.
* **Por jerarquía de creación:** La tabla Padre es independiente y debe crearse primero; la tabla Hijo depende de la existencia del Padre para poder referenciarlo.
* **Por integridad y propiedad:** La clave foránea actúa como el vínculo de pertenencia que define exactamente a qué registro de la tabla principal está asociado cada elemento derivado.

### 🧬 Tipos de Relaciones
Las relaciones son cómo se relaciona (`XD`) cada tabla. Hay 3 principales: *uno a uno*, *uno a muchos* (o muchos a uno, es lo mismo pero al revés) y *muchos a muchos* (gráficamente, el "uno" es una línea y el "muchos" es una pata de gallo).

* 👆 **Uno a uno:** Es cuando un elemento de una tabla se puede conectar con un solo elemento de otra. **Ejemplo:** `Persona y huella dactilar`. En este caso solo existe una; acá obviamente la tabla padre sería "persona" y el hijo la "huella", y la clave foránea estaría en la del hijo (o sea, agarramos la clave primaria del padre).
* 🥖 **Uno a muchos:** En este caso es cuando hay algo dentro de una tabla que se puede conectar con muchas cosas de otra tabla. **Ejemplo:** `Personas y Autos`. Una persona puede tener muchos autos, pero los autos no pueden tener muchos dueños. En este caso, la clave foránea iría en los autos ya que, como son muchos autos, necesitamos saber quiénes son los dueños.
* 🦅 **Muchos a muchos:** Es cuando muchos elementos se conectan con otra tabla con también muchos elementos. **Ejemplo:** `Consolas y Videojuegos`. Hay muchos elementos en ambas tablas; no puede crearse una clave foránea en ninguna de las dos porque cada una es específica para guardar la información de consolas o de videojuegos. Además, ese no sería tanto el problema, sino que tendríamos que meter todos los datos manualmente porque son muchos elementos. Entonces, para resolver ese problema, creamos **otra tabla** (Tabla Puente/Intermedia) en donde juntemos las 2 claves foráneas y algo que pueda hacer una relación entre las 2 tablas. **Ejemplo:** `Lanzamiento` (con esta podrás, además de crear su propia clave primaria, guardar la información de ambas y sirve de intermediario porque, por medio de la fecha de lanzamiento, nos da una pista de qué consola y juego estamos guardando... o si no, haces una fusión de los nombres de las 2 tablas que queremos unir y ya `:b`).

---

### 💻 Código de Arquitectura de Base de Datos (DDL)
```sql
-- Ejemplo del tipo de caracteres con ejemplo:
CREATE DATABASE IF NOT EXISTS mi_base_de_datos 
CHARACTER SET utf8mb4 
COLLATE utf8mb4_unicode_ci;
```

### 🛠️ Ejercicio de Práctica (Ejemplo Paciente con FK)
```sql
CREATE TABLE Paciente (
    id_paciente INT PRIMARY KEY AUTO_INCREMENT,  -- Entero, Clave Primaria y se suma solo
    cedula VARCHAR(20) NOT NULL UNIQUE,          -- Texto de hasta 20 letras, obligatorio y no se repite
    nombre VARCHAR(50) NOT NULL,                 -- Texto de hasta 50 letras, obligatorio
    apellido VARCHAR(50) NOT NULL,               -- Texto de hasta 50 letras, obligatorio
    fecha_nacimiento DATE,                       -- Solo la fecha
    estatura_metros DECIMAL(3,2),                -- Decimal (ej: 1.75)
    historial_clinico TEXT,                      -- Texto largo para observaciones
    id_distrito INT,                             -- Entero para la Clave Foránea
    
    -- Aquí creas la conexión con la tabla distrito
    FOREIGN KEY (id_distrito) REFERENCES Distrito(id_distrito)
);

-- Cambiarle nombre a la tabla / columna: 
-- ALTER TABLE nombre_tabla CHANGE nombre_antiguo nombre_nuevo TIPO_DE_DATO(longitud);
```

---

### 🏢 Estructura de Producción: Sistema Maestro-Detalle (Requisiciones y Cotizaciones)

#### 1. Creación de las Tablas Maestras (Padres Independientes)
```sql
-- Tabla: Estatus
CREATE TABLE estatus (
    id_estatus INT PRIMARY KEY AUTO_INCREMENT,
    descripcion_estatus VARCHAR(50) NOT NULL
);

-- Tabla: Departamentos
CREATE TABLE departamentos (
    id_departamento INT PRIMARY KEY AUTO_INCREMENT,
    nombre_departamento VARCHAR(100) NOT NULL
);

-- Tabla: Proveedores
CREATE TABLE proveedores (
    rif_proveedor VARCHAR(20) PRIMARY KEY, -- El RIF es único y sirve como PK
    nombre_proveedor VARCHAR(100) NOT NULL,
    direccion_proveedor VARCHAR(255),
    telefono_proveedor VARCHAR(20)
);

-- Tabla: Productos
CREATE TABLE productos (
    codigo_producto INT PRIMARY KEY AUTO_INCREMENT,
    nombre_producto VARCHAR(100) NOT NULL,
    existencia_producto INT NOT NULL DEFAULT 0,
    stock_maximo_producto INT,
    stock_minimo_producto INT,
    precio_del_producto DECIMAL(10,2) NOT NULL
);
```

#### 2. Creación de las Tablas de Documentos (Hijas con 1:N)
```sql
-- Tabla: Requisiciones (Cabecera)
CREATE TABLE requisiciones (
    numero_de_la_requisicion INT PRIMARY KEY AUTO_INCREMENT,
    fecha_de_la_requisicion DATE NOT NULL,
    id_departamento INT,
    id_estatus INT,
    
    -- Conexiones físicas (FKs)
    FOREIGN KEY (id_departamento) REFERENCES departamentos(id_departamento),
    FOREIGN KEY (id_estatus) REFERENCES estatus(id_estatus)
);

-- Tabla: Cotizaciones (Cabecera)
CREATE TABLE cotizaciones (
    numero_de_la_cotizacion INT PRIMARY KEY AUTO_INCREMENT,
    fecha_de_la_cotizacion DATE NOT NULL,
    rif_proveedor VARCHAR(20),
    
    -- Conexiones físicas (FKs)
    FOREIGN KEY (rif_proveedor) REFERENCES proveedores(rif_proveedor)
);
```

#### 3. Creación de las Tablas Detalle (Tablas Puente N:N)
```sql
-- Tabla Puente: Detalle de Requisición
CREATE TABLE detalle_requisicion (
    numero_detalle_de_la_requisicion INT PRIMARY KEY AUTO_INCREMENT,
    numero_de_la_requisicion INT,
    codigo_producto INT,
    cantidad_del_producto_en_requisicion INT NOT NULL,
    
    -- Unimos la Requisición con el Producto
    FOREIGN KEY (numero_de_la_requisicion) REFERENCES requisiciones(numero_de_la_requisicion),
    FOREIGN KEY (codigo_producto) REFERENCES productos(codigo_producto)
);

-- Tabla Puente: Detalle de Cotización
CREATE TABLE detalle_cotizacion (
    numero_detalle_de_la_cotizacion INT PRIMARY KEY AUTO_INCREMENT,
    numero_de_la_cotizacion INT,
    codigo_producto INT,
    cantidad_del_producto_cotizado INT NOT NULL,
    precio_del_producto_cotizado DECIMAL(10,2) NOT NULL, -- El precio que ofrece este proveedor específico
    
    -- Unimos la Cotización con el Producto
    FOREIGN KEY (numero_de_la_cotizacion) REFERENCES cotizaciones(numero_de_la_cotizacion),
    FOREIGN KEY (codigo_producto) REFERENCES productos(codigo_producto)
);
```

Y ya, bro. Eso es todo. ¡Unos saludiños brrrrrrrrrrrr! `xD`
