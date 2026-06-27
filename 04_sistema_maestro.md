###🏢 Estructura de Producción: Sistema Maestro-Detalle (Requisiciones y Cotizaciones)
( Ejercicio echos )

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

[📚 Volver al Índice](README.md)
[⬅️ Pagina anterior](03_diseno_avanzado.md)
