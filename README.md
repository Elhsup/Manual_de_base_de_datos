GUÍA DE SQL: BASES DE DATOS DESDE CERO 🎮
Aca vamos a explicar un poquiño de los que es el dml lo basiquiño para enteder que hace cada cosiña.

📊 Estructura Visual de la Data
Plaintext
Fila  ___________________
       |
       |
columna|
       |
       | 
       |
💡 por si no lo sabias toda esta informacion son tablas de excel gigantes pa k no te me confundais

🥚 BLOQUE 1: LO BÁSICO (Manipulación de Datos - DML)
📥 1. El Comando INSERT INTO
Es el comando encargado de crear filas nuevas (registros) dentro de una tabla. Es el que alimenta la base de datos con información real.

(recordemos que las columnas son la forma en que se agrupa la info es decir sin columnas no sabemos a donde iria ese dato que vamos a ingresar en este caso la fila es lo que nos indica en donde iria ese dato ejemlo: una columna que se llame nombre, en la fila tiene que ir los nombres como juan pancho maduro goku etcetc)

🏗️ La Estructura Obligatoria
(porque tiene un orden sin un orden el programa no sabe lo que va a hacer) se divide en tres partes:

SQL
INSERT INTO nombre_tabla (columna1, columna2, columna3) 
VALUES (valor1, valor2, valor3);
🧠 (La Lógica):
📑 INSERT INTO nombre_tabla: Le dices a SQL: "¡Ey! Prepárate que voy a meter información en esta tabla específica". insert singinifica insertar o agregar, into es dentro, el nombre de la tabla indica si hay muchas tablas en donde va. osea inserta dentro de esta tabla colocate que se llama : tablaMario.

📋 Los campos entre paréntesis (columna1, columna2...): (hay tecnicamente van los nombres de la columna y si la tabla se llama mario entences los nombres de la columna serian (champiñon, monedas)): Aquí listas los nombres de las columnas que vas a llenar. Regla de examen: Van separados por comas y no llevan comillas.

🪙 VALUES (valor1, valor2...): (si es mario seria : verde, rojas): Aquí metes los datos reales que se van a guardar. Regla de oro: Tienen que ir en el mismo orden exacto en el que escribiste las columnas arriba. Si la columna 1 es la champiñon, el valor 1 tiene que ser en este caso el color del champiñon. VALUES Indica los valores exactos que coinciden con esas columnas. osea lo que va adentro p.

🛑 Reglas de Escritura de Datos
(ademas tenemos un grupo de reglas que estas son sobre como escribir los datos y literalmente te sirve para que te corra el programa bien po k chi no no)

🔤 Textos (VARCHAR) y Fechas (DATE): Obligatoriamente van encerrados en comillas simples (' ').

🔢 Números (INT, DECIMAL): Van sueltos, sin comillas.

🔥 coloquemos un ejemplo random >:D

SQL
INSERT INTO tablaMario (champiñon, monedas) VALUES ('verde', 'rojas');
👁️ 2. El Comando SELECT * FROM
Aca lo que vamos a hacer es ver todo lo que tenemos en la tabla al tu meter la informacion con el insert into lo guardaras pero no podras ver como esta la info etonces para poder ver si te equivocaste esta bien o mal colocaras selec * from.

🏗️ Estructura Estándar
SQL
SELECT * FROM nombre_tabla;
🧠 La Lógica:
🔍 SELECT: Significa "Selecciona o búscame...".

⭐ * (El asterisco): Es un comodín que significa "TODAS las columnas".

🗺️ FROM nombre_tabla: Significa "desde esta tabla específica".

🗣️ Traducción: "Búscame todas las columnas desde la tabla Mario".

🔥 ejemplo: SELECT * FROM tablaMario;

🎯 Forma B: Para ver columnas específicas (Filtrar columnas)
Si el profesor te dice: "Muestre solo cuántas monedas hay, no me interesa ver el color del champiñón", tú quitas el asterisco y escribes el nombre de la columna:

SQL
SELECT monedas FROM tablaMario;
aca lo que diria es muestrame(select) toda la columna osea recortamos un pedazo que se llama monedas de la tabla(from); tablaMario(nombre de la tabla)

🔄 3. El Comando UPDATEEEEEE
¿Qué hace?: Es el comando que sirve para modificar o actualizar un dato que ya está guardado dentro de una fila. Por ejemplo, si registraste que el champiñón era 'verde' pero en realidad querías ponerle 'azul', usas UPDATE. osea cambias el valor a una fila.

🏗️ Estructura Fija de Tres Pasos
(que se lee de arriba a abajo):

SQL
UPDATE nombre_tabla   
SET columna_a_cambiar = 'nuevo_valor'          
WHERE columna_filtro = 'valor_buscado';
🎯 Descifrando los Valores
donde dice "nuevo valor" y "valor buscado" significa los nombres que vas (o los datos como los quieras llamar) a cambiar y buscar:

🔵 nuevo valor: por ejemplo azul (osea el dato que vas a buscar).

🔴 valor buscado: rojo (como el dato que quieres cambiar).
(ejemplo de las monedas)

🧠 La Lógica de cada paso:
🚪 UPDATE nombre_tabla: Le dices a SQL: "update(cambia) y Entra a esta tabla porque voy a hacer una edición".

✍️ SET columna_a_cambiar = 'nuevo_valor': La palabra SET significa "Establecer o Colocar". Aquí le dices: "Quiero que metas este nuevo dato en esta columna".

🎯 WHERE columna_filtro = 'valor_buscado': ¡EL PASO MÁS IMPORTANTE! Aquí le dices a qué fila exacta le vas a hacer el cambio. (WHERE significa "Donde": Pone una condición. SQL va a ir fila por fila y solo te va a pintar en la pantalla las filas que cumplan exactamente con lo que pides. Las demás las deja ocultas).

🚨 La Regla del Desastre:
Si tú escribes en el examen UPDATE tablaMario SET champiñon = 'azul'; y se te olvida poner el WHERE, SQL le va a cambiar el color a TODOS los champiñones de la tabla completa. El profesor te va a raspar de una vez por "destruir" la base de datos. El WHERE es el francotirador que le dice a SQL: "Cámbiame el dato ÚNICAMENTE en esta fila".

¿Que pasa con el where y colocarle el nombre de la tabla?
Sin ponerle un filtro, entra a la tabla y le cambia el valor a todas las filas que existan. Si tenías monedas rojas, verdes, doradas, negras... absolutamente todas pasan a ser azules. Borraste el historial del juego por error.

osea que si le coloco el where sin el nombre de la tabla me puede cambiar en otros lugares que no quiero.

si "no" le coloco el where me puede cambiar todo hasta lo que no quiero que se cambie.

❌ 4. El Comando DELETE
¿Qué hace?: Sirve para borrar filas (registros) completas de una tabla. Ojo: borra la fila entera (el objeto), no una casilla suelta.

🏗️ Estructura Obligatoria en la Pizarra:
SQL
DELETE FROM nombre_tabla 
WHERE nombre_columna = 'valor_buscado';
🧠 La Lógica de examen:
🧼 DELETE FROM tablaMario: Le dices a SQL: "Voy a eliminar registros de esta tabla". (Nota que aquí no se ponen nombres de columnas, porque vas a borrar la fila completa).

🛡️ WHERE monedas = 'azules': El guardaespaldas otra vez. Si no pones el WHERE, ejecutas un DELETE FROM tablaMario; y vías la tabla por completo, dejas a Mario sin ningún dato. El WHERE le dice: "Borra ÚNICAMENTE la fila donde las monedas sean azules".

🏆 Laboratorio Práctico de DML (Caso de Examen)
SQL
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
🧠 BLOQUE 2: LO AVANZADO (Diseño, Llaves y Relaciones)
🔑 Conceptos Clave: Claves y Relaciones
🔑 °clave primaria: identificador unico de una tabla, que no puede repetirse ni ser nula.

🔗 °clave foranea: se lleva la clave primaria de una tabla, o otro dato. es la conexion de una tabla a otra (decimos ques esta es la segunda tabla tecnicamente tambien tiene su clave primaria).

📐 Jerarquía Padre e Hijo
La clave primaria puede salir en cualquier tabla (llamemoslo tabla padre), sin embargo la clave foranea se va a mover o eredar o aparecer en la tabla QUE NO ES principal (llamemoslo tabla hijo) ejemplo:

en un hospital necesita el historial de el paciente

principal (padre): paciente (tiene su clave primaria)

Derivada o no principal (hijo) es: ->historial<- ahi va a aparecer la clave foranea (que es la clave principal de paciente)

¿Donde van las claves foraneas?
En este caso hay 3 razones por las que van en la parte de muchos o en la tabla hijo:

El profesor dijo que donde iban muchos ahi van las foraneas.

Primero sale el padre y despues el hijo la clave foranea por logica no puede ir donde va el padre porque el padre salio primero que el hijo.

Cuando tienes muchas cosas que se conectan con una sola necesitas administrar quien es el dueño, de ahi agarras y le colocas las claves foraneas a las cosas que necesitas administrar.

o haci pa que entiendas:
Por regla de cardinalidad: El lado del "Muchos" es el único que permite repetir el identificador del padre para conectar varios registros a un mismo origen.

Por jerarquía de creación: La tabla Padre es independiente y debe crearse primero; la tabla Hijo depende de la existencia del Padre para poder referenciarlo.

Por integridad y propiedad: La clave foránea actúa como el vínculo de pertenencia que define exactamente a qué registro de la tabla principal está asociado cada elemento derivado.

🧬 Tipos de Relaciones
Las relaciones es como se relacionan(XD) cada tabla hay 3 principales: uno a uno, uno a muchos, muchos a uno (es los mismo pero al reves) y muchos a muchos (graficamente el uno es una linea y el mucho es un para de gallo).

👆 Uno a uno: Es cuando un elemento de una tabla se puede conectar con otro elemento por ejemplo: -->persona y huela dactilar<-- en este caso solo existe una aca obviamente la tabla padre seria persona y el hijo la huella y la clave foranea estaria en la del hijo osea agarramos la clave primaria del padre.

🥖 Uno a muchos: en este caso es cuando hay algo dentro de una tabla que se puede conectar con muchas cosas de otra tabla ejemplo: -->Personas y Autos<-- una persona puede tener muchos autos pero los autos no pueden tener muchos dueños en este caso la clave foranea seria los autos ya que como son muchos autos necesitamos saber quienes son los dueños.

🦅 Muchos a muchos: Es cuando muchos elementos se conectan con otra tabla con tambien muchos elementos por ejemplo -->consolas y videojuegos<-- hay muchos elementos en ambas tablas, no puede crearse una clave foranea en ninguna de las 2 porque cada una es especifica para guardar la informacion de consolas y videojuegos ademas de la clave foranea ese no seria tanto el problema sino que tendriamos que meter todos los datos manualmente porque son muchos elementos entonces para resolver ese problema podemos crear otra tabla en donde juntemos las 2 claves foraneas y algo que pueda hacer una relacion entre las 2 tablas: Lanzamiento (con esta podras ademas de crear su propia clave primaria guardar la informacion de ambas y sirve de intermediario porque pomedio de la fecha del lanzamiento darnos una pista de que consola y juego estamos guardando o sino haces una fusion de los 2 nombres de las 2 tablas que queremos unir y ya :b).

💻 Código de Arquitectura de Base de Datos (DDL)
SQL
-- Ejemplo de el tipo de caracteres con ejemplo:
CREATE DATABASE IF NOT EXISTS mi_base_de_datos 
CHARACTER SET utf8mb4 
COLLATE utf8mb4_unicode_ci;
🛠️ Ejercicio de Práctica (Ejemplo Paciente con FK)
SQL
CREATE TABLE Paciente (
    id_paciente INT PRIMARY KEY AUTO_INCREMENT, -- Entero, Clave Primaria y se suma solo
    cedula VARCHAR(20) NOT NULL UNIQUE,          -- Texto de hasta 20 letras, obligatorio y no se repite
    nombre VARCHAR(50) NOT NULL,                 -- Texto de hasta 50 letras, obligatorio
    apellido VARCHAR(50) NOT NULL,               -- Texto de hasta 50 letras, obligatorio
    fecha_nacimiento DATE,                       -- Solo la fecha
    estatura_metros DECIMAL(3,2),                -- Decimal (ej: 1.75)
    historial_clinico TEXT,                      -- Texto largo para observaciones
    id_distrito INT,                            -- Entero para la Clave Foránea
    
    -- Aquí creas la conexión con la tabla distrito
    FOREIGN KEY (id_distrito) REFERENCES Distrito(id_distrito)
);

-- Cambiarle nombre a la tabla / columna: 
-- ALTER TABLE nombre_tabla CHANGE nombre_antiguo nombre_nuevo TIPO_DE_DATO(longitud);
🏢 Estructura de Producción: Sistema Maestro-Detalle (Requisiciones y Cotizaciones)
1. Creación de las Tablas Maestras (Padres Independientes)
SQL
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
2. Creación de las Tablas de Documentos (Hijas con 1:N)
SQL
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
3. Creación de las Tablas Detalle (Tablas Puente N:N)
SQL
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

y ya bro eso es todo unos saludiños brrrrrrrrrrrr
