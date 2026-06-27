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
[📚 Volver al Índice](README.md)
[⬅️ Pagina anterior](02_modificacion.md)
[➡️ Siguiente pagina](04_sistema_maestro.md)
