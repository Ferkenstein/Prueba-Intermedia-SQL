# Ejercicio 3

## Creación de Tablas

### Crear tabla Ficha de Pelicula

La tabla Ficha_Pelicula tiene un idPelicula, tituloDistribucion, tituloOriginal, idiomaOriginal,
paisOrigen, anioProduccion, urlSitioWeb, duracion, clasificacion, fechaEstreno, resumen.

```SQL
CREATE TABLE FICHA_PELICULA (
idPelicula INTEGER PRIMARY KEY NOT NULL,
tituloDistribucion VARCHAR2(50) NOT NULL,
tituloOriginal VARCHAR2(50) NOT NULL,
idiomaOriginal VARCHAR2(50) NOT NULL,
paisOrigen  VARCHAR2(50) NOT NULL,
anioProduccion INTEGER NOT NULL,
urlSitioWeb VARCHAR2(50) NOT NULL,
duracion VARCHAR2(50) NOT NULL,
clasificacion VARCHAR2(50) NOT NULL,
fechaEstreno DATE NOT NULL,
resumen VARCHAR2(100) NOT NULL
);

```

### Crear tabla Subtitulo

La tabla Subtitulo fue creada debido a que una pelicula puede tener distintos subtitulos, esta tiene idSubtitulo, subtituloPelicula, idPelicula.

```SQL
CREATE TABLE SUBTITULO (
idSubtitulo INTEGER PRIMARY KEY NOT NULL,
subtituloPelicula VARCHAR2(50) NOT NULL,
idPelicula INTEGER NOT NULL
);
-- Agregar llave foránea.
ALTER TABLE SUBTITULO ADD FOREIGN KEY (idPelicula) REFERENCES FICHA_PELICULA(idPelicula);
```

### Crear tabla Reparto

La tabla reparto contiene el idReparto, nombreReparto, nacionalidad, el rol que cumple en la pelicula y la cantidadPeliculas.

``` SQL
CREATE TABLE REPARTO (
idReparto INTEGER NOT NULL PRIMARY KEY,
nombreReparto VARCHAR2(50) NOT NULL,
nacionalidad VARCHAR2(50) NOT NULL,
rol VARCHAR2(50) NOT NULL,
cantidadPeliculas INTEGER NOT NULL
);
```

### Crear tabla Pelicula Reparto

La tabla Pelicula_Reparto relaciona el reparto de la pelicula con la ficha de la pelicula, tiene un idPelicula e idReparto

``` SQL
CREATE TABLE PELICULA_REPARTO (
idPelicula INTEGER NOT NULL,
idReparto INTEGER NOT NULL
);
-- Agregar llave foránea.
ALTER TABLE PELICULA_REPARTO ADD FOREIGN KEY (idPelicula) REFERENCES FICHA_PELICULA(idPelicula);
ALTER TABLE PELICULA_REPARTO ADD FOREIGN KEY (idReparto) REFERENCES REPARTO(idReparto);
```

### Crear tabla Cine

La tabla Cine tiene idCine, nombreCine, direccionCine, telefonoCine.

``` SQL
CREATE TABLE CINE (
idCine INTEGER NOT NULL PRIMARY KEY,
nombreCine VARCHAR2(50) NOT NULL,
direccionCine VARCHAR2(50) NOT NULL,
telefonoCine VARCHAR2(50) NOT NULL
);
```
### Crear tabla Sala

La tabla Sala tiene idCine, idSala, nombreSala, cantidadButacas.

``` SQL
CREATE TABLE SALA (
idCine INTEGER NOT NULL,
idSala INTEGER NOT NULL PRIMARY KEY,
nombreSala VARCHAR2(50) NOT NULL,
cantidadButacas INTEGER NOT NULL
);
-- Agregar llave foránea.
ALTER TABLE SALA ADD FOREIGN KEY (idCine) REFERENCES CINE(idCine);
```

### Crear tabla Funcion

La tabla Funcion tiene idFuncion, idSala, idPelicula, fechaFuncion.

``` SQL
CREATE TABLE FUNCION (
idFuncion INTEGER PRIMARY KEY NOT NULL,
idSala INTEGER NOT NULL,
idPelicula INTEGER NOT NULL,
fechaFuncion DATE
);
-- Agregar llave foránea.
ALTER TABLE FUNCION ADD FOREIGN KEY (idSala) REFERENCES SALA(idSala);
ALTER TABLE FUNCION ADD FOREIGN KEY (idPelicula) REFERENCES FICHA_PELICULA(idPelicula);
```

### Crear tabla Opiniones

La tabla Opiniones tiene idOpinion, idFuncion, nombrePersona, edad, fechaOpinion, calificacion, comentario

``` SQL
CREATE TABLE OPINIONES (
idOpinion INTEGER PRIMARY KEY NOT NULL,
idFuncion INTEGER NOT NULL,
nombrePersona VARCHAR2(50) NOT NULL,
edad INTEGER NOT NULL,
fechaOpinion DATE NOT NULL,
calificacion VARCHAR2(50) NOT NULL,
comentario VARCHAR2(100) NOT NULL
);
-- Agregar llave foránea.
ALTER TABLE OPINIONES ADD FOREIGN KEY (idFuncion) REFERENCES FUNCION(idFuncion);
```
### Crear tabla Promoción

La tabla Promoción tiene idPromocion, idFuncion, descripcionPromocion, descuento.

``` SQL
CREATE TABLE PROMOCION (
idPromocion INTEGER PRIMARY KEY NOT NULL,
idFuncion INTEGER NOT NULL,
descripcionPromocion VARCHAR2(50) NOT NULL,
descuento INTEGER NOT NULL
);
-- Agregar llave foránea.
ALTER TABLE PROMOCION ADD FOREIGN KEY (idFuncion) REFERENCES FUNCION(idFuncion);
```









