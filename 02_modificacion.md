### 🔄 3. El Comando UPDATEEEEEE `xD`
<br> 
**¿Qué hace?:** Es el comando que sirve para modificar o actualizar un dato que ya está guardado dentro de una fila. Por ejemplo, si registraste que el champiñón era `'verde'` pero en realidad querías ponerle `'azul'`, usas `UPDATE`. O...sea, cambias el valor a una fila.
<br> 

#### 🏗️ Estructura Fija de Tres Pasos (Se lee de arriba a abajo):
```sql
UPDATE nombre_tabla   
SET columna_a_cambiar = 'nuevo_valor'          
WHERE columna_filtro = 'valor_buscado';
```
<br> 

#### 🎯 Descifrando los Valores
Donde dice `nuevo_valor` y `valor_buscado` significa los nombres (o los datos, como los quieras llamar) que vas a cambiar y buscar:
* 🔵 **`nuevo_valor`**: Por ejemplo, `'azul'` (o sea, el dato fresco que vas a colocar).
* 🔴 **`valor_buscado`**: Por ejemplo, `'rojo'` (el dato viejo que quieres cambiar). *(Ejemplo de las monedas)*.
---
<br>

#### 🧠 La Lógica de cada paso:
* 🚪 **`UPDATE nombre_tabla`**: Le dices a SQL: *"UPDATE (cambia) y entra a esta tabla porque voy a hacer una edición"*.
---
* ✍️ **`SET columna_a_cambiar = 'nuevo_valor'`**: La palabra `SET` significa "Establecer o Colocar". Aquí le dices: *"Quiero que metas este nuevo dato en esta columna"*.
---

* 🎯 **`WHERE columna_filtro = 'valor_buscado'`**: **¡EL PASO MÁS IMPORTANTE!** Aquí le dices a qué fila exacta le vas a hacer el cambio. (`WHERE` significa "Donde": Pone una condición. SQL va a ir fila por fila y solo te va a pintar en la pantalla las filas que cumplan exactamente con lo que pides. Las demás las deja ocultas).
<br>
<br> 

### 🚨 La Regla del Desastre:
Si tú escribes en el examen `UPDATE tablaMario SET champiñon = 'azul';` y se te olvida poner el `WHERE`, SQL le va a cambiar el color a TODOS los champiñones de la tabla completa. El profesor te va a raspar de una vez por "destruir" la base de datos `x_x`. El `WHERE` es el francotirador que le dice a SQL: *"Cámbiame el dato ÚNICAMENTE en esta fila"*.

<br> 
---
## **¿Qué pasa con el WHERE y colocarle el nombre de la tabla?**
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
<br> 
---

#### 🧠 La Lógica de examen:
* 🧼 **`DELETE FROM tablaMario`**: Le dices a SQL: *"Voy a eliminar registros de esta tabla"*. (Nota que aquí no se ponen nombres de columnas, porque vas a borrar la fila completa).
<br>

* 🛡️ **`WHERE monedas = 'azules'`**: El guardaespaldas otra vez. Si no pones el `WHERE`, ejecutas un `DELETE FROM tablaMario;` y vacías la tabla por completo, dejas a Mario sin ningún dato. El `WHERE` le dice: *"Borra ÚNICAMENTE la fila donde las monedas sean azules"*.

---

### 🏆 Laboratorio Práctico de DML (Caso de Examen)
```sql
-- Insert into Consola 
INSERT INTO Consola
(IdConsola, Nombre, Marca) 
VALUES (5, 'PS5', 'Sony');

-- Insert into Videojuego
INSERT INTO Videojuego
(IdJuego, Titulo, Genero) 
VALUES (101, 'Spider-Man', 'Accion');

-- Update Videojuego 
UPDATE Videojuego 
SET Genero = 'Aventura'
WHERE IdJuego = 101; 
-- 💡 Nota: Usamos el IdJuego = 101 como
francotirador para cambiar el género de
forma única sin alterar otros registros.

-- Delete de Videojuego
DELETE FROM Videojuego 
WHERE IdJuego = 101;
```
---
<br>

*[📚 Volver al Índice](README.md)
<br> 

*[⬅️ Pagina anterior](01_introduccion.md)
<br> 

*[➡️ Siguiente pagina](03_diseno_avanzado.md)
